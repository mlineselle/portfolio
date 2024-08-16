---
  permalink: /artifact-one/
  title: "Artifact One - TI Board Thermometer"
  layout: single
---

### Original Code
Included a simple main function that used timers to trigger different functions and tasks while the thermostat program was working.

```
void *mainThread(void *arg0)
{
    /* Call driver init functions */
    GPIO_init();
    initUART2();
    initI2C();
    initTimer();

    /* Declare necessary variables */
    uint32_t seconds = 0;
    uint32_t setpoint = 30;
    uint32_t temperature = 0;
    unsigned char heat = false;

    /* Configure the LED pin */
    GPIO_setConfig(CONFIG_GPIO_LED_0, GPIO_CFG_OUT_STD | GPIO_CFG_OUT_LOW);

    /* Configure the Button 0 */
    GPIO_setConfig(CONFIG_GPIO_BUTTON_0, GPIO_CFG_IN_PU | GPIO_CFG_IN_INT_FALLING);

    /* Install Button callback */
    GPIO_setCallback(CONFIG_GPIO_BUTTON_0, gpioButtonFxn0);

    /* Enable interrupts */
    GPIO_enableInt(CONFIG_GPIO_BUTTON_0);

    /*
     *  If more than one input pin is available for your device, interrupts
     *  will be enabled on CONFIG_GPIO_BUTTON1.
     */
    if (CONFIG_GPIO_BUTTON_0 != CONFIG_GPIO_BUTTON_1)
    {
        /* Configure BUTTON1 pin */
        GPIO_setConfig(CONFIG_GPIO_BUTTON_1, GPIO_CFG_IN_PU | GPIO_CFG_IN_INT_FALLING);

        /* Install Button callback */
        GPIO_setCallback(CONFIG_GPIO_BUTTON_1, gpioButtonFxn1);
        GPIO_enableInt(CONFIG_GPIO_BUTTON_1);
    }

    while (1) {
        // Every 200ms
        if (timerFlag200) {
            // Check if buttons have been pressed, and change setpoint accordingly
            if (button0Flag) {  // If button 0 has been pressed
                setpoint += 1;  // Increase setpoint by one
                button0Flag = false;  // Reset the button flag
            } else if (button1Flag) {  // If button 1 has been pressed
                setpoint -= 1;  // Decrease setpoint by one
                button1Flag = false;  // Reset the button flag
            }
            timerFlag200 = false;  // Reset the flag
        }
        // Every 500ms
        if (timerFlag500) {
            temperature = readTemp();  // Read the current temperature and store it in temperature variable
            timerFlag500 = false; // Reset the flag

        }
        // Every 1 second
        if (timerFlag1000) {
            // Calculate and store amount of seconds, turn on the heat if needed, and output information.
            seconds = timerCount / 1000000;

            if (temperature < setpoint) {  // If the temperature is less than the setpoint
                heat = true;  // Turn on the heat
                GPIO_write(CONFIG_GPIO_LED_0, CONFIG_GPIO_LED_ON);  // Turn on the LED
            } else if (temperature > setpoint) {  // Else if the temperature is more than the setpoint
                heat = false;  // Turn off the heat
                GPIO_write(CONFIG_GPIO_LED_0, CONFIG_GPIO_LED_OFF);  // Turn off the LED
            }

            outputFormattedInfo(temperature, setpoint, heat, seconds);  // Output the information in the correct format
            timerFlag1000 = false; // Reset the flag
        }
    }

    return (NULL);
}
```

### Enhanced Code
I added utilization of wifi chip, and sending data to an https server to store for later. As well as simple PID structure to enhance reliability

```
/* Function to Initialize the on Board wifi to connect to the data webpage */
void initWiFi() {
    SlNetCfgIpV4Args_t ipV4;
    int32_t status = sl_Start(0, 0, 0);
    if (status < 0) {
        // Handle Error
        UART2_write(uart, "Failed to start Wi-Fi\n", 22, &bytesWritten);
        exit(1);
    }

    status = sl_WlanSetMode(ROLE_STA);
    if (status < 0) {
        // Handle Error
        UART2_write(uart, "Failed to set Wi-Fi mode\n", 25, &bytesWritten);
        exit(1);
    }

    status = sl_WlanConnect((signed char *)SSID_NAME, strlen(SSID_NAME), 0, &SecurityParams, 0);
    if (status < 0) {
        // Handle Error
        UART2_write(uart, "Failed to connect to Wi-Fi\n", 27, &bytesWritten);
        exit(1);
    }

    while ((status = sl_WlanConnect(0, 0, 0, 0, 0)) != ROLE_STA) {
        // Wait for connection
        UART2_write(uart, "Connecting to Wi-Fi...\n", 23, &bytesWritten);
        sleep(1);
    }

    UART2_write(uart, "Connected to Wi-Fi\n", 18, &bytesWritten);
}

/* Function to send data to the webpage from the board */
void sendData(int temperature, int setpoint, int heat, int seconds) {
    HTTPClient_Handle httpClient;
    HTTPClient_ExtendedHeaderFields fields;
    HTTPClient_Response response;
    char postData[100];
    char responseBody[128];

    snprintf(postData, sizeof(postData), "{\"temperature\":%d,\"setpoint\":%d,\"heat\":%d,\"seconds\":%d}",
             temperature, setpoint, heat, seconds);

    httpClient = HTTPClient_create(&httpClientObj);
    HTTPClient_connect(httpClient, SERVER_NAME, 0, 0);

    fields.count = 0;
    HTTPClient_setExtendedHeaderFields(httpClient, &fields);

    int status = HTTPClient_sendRequest(httpClient, HTTP_METHOD_POST, POST_PATH, postData, strlen(postData), 0, 0);
    if (status < 0) {
        snprintf(responseBody, sizeof(responseBody), "Error on sending POST: %d\n", status);
        UART2_write(uart, responseBody, strlen(responseBody), &bytesWritten);
    } else {
        int bytesRead = HTTPClient_readResponseBody(httpClient, responseBody, sizeof(responseBody));
        responseBody[bytesRead] = '\0';
        UART2_write(uart, responseBody, strlen(responseBody), &bytesWritten);
    }

    HTTPClient_disconnect(httpClient);
    HTTPClient_destroy(httpClient);
}
```

### Narrative for Artifact One
This artifact is an embedded C program that runs an example thermostat on a TI Launchpad CC3220S. It runs using a timer that was created, and using the build in functionality of the board with UART2 and I2C, along with a temperature sensor and buttons, it detects the current temperature and will activate the heat if it is too cold. I chose this artifact as it was one of the few programs that interacted with a physical object and went through the board. This is a crucial skill for several fields of software engineering, and may be something I wish to pursue. I want to showcase how I can learn to design software that runs on hardware and can accomplish tasks in the physical world, as well as being able to debug and fix this code. 

I improved the artifact by including a PID system for the thermostat for more accuracy, along with adding some more error handling and general code improvement. I also designed code to utilize the board's onboard wifi connection chip to have it offload the thermostat data to an HTTP website. I have met the course objectives that I had planned with this enhancement. I fixed some of the security and demonstrated that I could write a popular piece of software, a PID system for a specific piece of equipment. I also demonstrated my ability to utilize the board to its fullest through the wifi and connecting to HTTP. 

When I was writing this code, I realized that the PID system was not as difficult as I originally expected, however getting the HTTP code to work was difficult. I did not have a public server so had to host one privately and get the wifi to connect to it. I also realized that I had no idea how to securely hide the website password on the board code, but since the board shouldnt be able to be attacked easily I thought it would be an okay practice to leave it there.

### Full Code Git Repositories
- [Original Artifact One Code](https://github.com/mlineselle/CS-350-H7050-Emerging-Sys-Arch-Tech.git)
- [Enhanced Artifact One Code](https://github.com/mlineselle/ArtifactOneEnhancement.git)

### CC3220S LAUNCHXL TI board
<img src="https://github.com/mlineselle/portfolio/raw/master/assets/images/cc3220sf-launchxl-top.png" alt="CC3220S LaunchXL TI board Image" width="560" height="315">
