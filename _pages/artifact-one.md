---
  permalink: /artifact-one/
  title: "Artifact One - TI Board Thermometer"
---

## Artifact One - TI Board Thermometer
- [Original Artifact One Code](https://github.com/mlineselle/CS-350-H7050-Emerging-Sys-Arch-Tech.git)
- [Enhanced Artifact One Code](https://github.com/mlineselle/ArtifactOneEnhancement.git)

### Narrative for Artifact One
This artifact is an embedded C program that runs an example thermostat on a TI Launchpad CC3220S. It runs using a timer that was created, and using the build in functionality of the board with UART2 and I2C, along with a temperature sensor and buttons, it detects the current temperature and will activate the heat if it is too cold. I chose this artifact as it was one of the few programs that interacted with a physical object and went through the board. This is a crucial skill for several fields of software engineering, and may be something I wish to pursue. I want to showcase how I can learn to design software that runs on hardware and can accomplish tasks in the physical world, as well as being able to debug and fix this code. I improved the artifact by including a PID system for the thermostat for more accuracy, along with adding some more error handling and general code improvement. I also designed code to utilize the board's onboard wifi connection chip to have it offload the thermostat data to an HTTP website. I have met the course objectives that I had planned with this enhancement. I fixed some of the security and demonstrated that I could write a popular piece of software, a PID system for a specific piece of equipment. I also demonstrated my ability to utilize the board to its fullest through the wifi and connecting to HTTP. When I was writing this code, I realized that the PID system was not as difficult as I originally expected, however getting the HTTP code to work was difficult. I did not have a public server so had to host one privately and get the wifi to connect to it. I also realized that I had no idea how to securely hide the website password on the board code, but since the board shouldnt be able to be attacked easily I thought it would be an okay practice to leave it there.

