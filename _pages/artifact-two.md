---
  permalink: /artifact-two/
  title: "Artifact Two - OpenGL Kitchen Render"
  layout: single
---

<video width="560" height="315" controls muted>
  <source src="https://github.com/mlineselle/portfolio/raw/master/assets/videos/ArtifactTwoVideo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Changes in Data Structures and Algorithms
One of the big changes was cleaning up the original buildCubeBases function and making it cleaner as well as using data structures to store more values.

#### Original Code

<details>
<summary>Click to expand!</summary>
<pre style="font-size: 9px;">
<code>  
// Build Cube Bases
std::vector(GLfloat) buildCubeBases(GLfloat x, GLfloat y, GLfloat z, GLfloat height, GLfloat width, GLfloat length, GLfloat leftTextureXStart, GLfloat leftTextureXStop, GLfloat leftTextureYStart, GLfloat leftTextureYStop, GLfloat rightTextureXStart, GLfloat rightTextureXStop, GLfloat rightTextureYStart,   GLfloat rightTextureYStop, GLfloat frontTextureXStart, GLfloat frontTextureXStop, GLfloat frontTextureYStart, GLfloat frontTextureYStop, GLfloat backTextureXStart, GLfloat backTextureXStop, GLfloat backTextureYStart, GLfloat backTextureYStop, GLfloat topTextureXStart, GLfloat topTextureXStop, GLfloat topTextureYStart, GLfloat topTextureYStop, GLfloat bottomTextureXStart, GLfloat bottomTextureXStop, GLfloat bottomTextureYStart, GLfloat bottomTextureYStop) {

    // Initialize vector for base vertices
    std::vector(GLfloat) squareVerts;

    // Top Square
        // Top left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(topTextureXStart);
            squareVerts.push_back(topTextureYStop);


        // Top Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(topTextureXStop);
            squareVerts.push_back(topTextureYStop);


        // Bottom Left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(topTextureXStart);
            squareVerts.push_back(topTextureYStart);


        // Bottom Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(topTextureXStop);
            squareVerts.push_back(topTextureYStart);

    // Front Square
        // Top left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(frontTextureXStart);
            squareVerts.push_back(frontTextureYStop);


        // Top Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(frontTextureXStop);
            squareVerts.push_back(frontTextureYStop);


        // Bottom Left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(frontTextureXStart);
            squareVerts.push_back(frontTextureYStart);


        // Bottom Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(frontTextureXStop);
            squareVerts.push_back(frontTextureYStart);

    // Left Square
        // Top left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(leftTextureXStart);
            squareVerts.push_back(leftTextureYStop);


        // Top Right Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(leftTextureXStop);
            squareVerts.push_back(leftTextureYStop);


          // Bottom Left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(leftTextureXStart);
            squareVerts.push_back(leftTextureYStart);


        // Bottom Right Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(leftTextureXStop);
            squareVerts.push_back(leftTextureYStart);


    // Right Square
        // Top left Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(rightTextureXStart);
            squareVerts.push_back(rightTextureYStop);


        // Top Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(rightTextureXStop);
            squareVerts.push_back(rightTextureYStop);


        // Bottom Left Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(rightTextureXStart);
            squareVerts.push_back(rightTextureYStart);


        // Bottom Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(1.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(rightTextureXStop);
            squareVerts.push_back(rightTextureYStart);

    // Back Square
        // Top left Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            // Texture Coordinates
            squareVerts.push_back(backTextureXStart);
            squareVerts.push_back(backTextureYStop);


        // Top Right Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z + height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            // Texture Coordinates
            squareVerts.push_back(backTextureXStop);
            squareVerts.push_back(backTextureYStop);


        // Bottom Left Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            // Texture Coordinates
            squareVerts.push_back(backTextureXStart);
            squareVerts.push_back(backTextureYStart);


        // Bottom Right Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            // Texture Coordinates
            squareVerts.push_back(backTextureXStop);
            squareVerts.push_back(backTextureYStart);

    // Bottom Square
        // Top left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(bottomTextureXStart);
            squareVerts.push_back(bottomTextureYStart);


        // Top Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y + length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(bottomTextureXStop);
            squareVerts.push_back(bottomTextureYStart);


        // Bottom Left Vertex
            // Coordinates
            squareVerts.push_back(x - width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(bottomTextureXStop);
            squareVerts.push_back(bottomTextureYStart);


        // Bottom Right Vertex
            // Coordinates
            squareVerts.push_back(x + width / 2);
            squareVerts.push_back(y - length / 2);
            squareVerts.push_back(z - height / 2);
            //Normal Vector Coordinates
            squareVerts.push_back(0.0);
            squareVerts.push_back(-1.0);
            squareVerts.push_back(0.0);
            // Texture Coordinates
            squareVerts.push_back(bottomTextureXStart);
            squareVerts.push_back(bottomTextureYStart);

      return squareVerts;
  }
  </code>
  </pre>
  </details>

#### Enhanced Code

<details>
<pre style="font-size: 9px;">
<code>  
  
void addVertex(std::vector(GLfloat)& squareVerts, GLfloat x, GLfloat y, GLfloat z, GLfloat nx, GLfloat ny, GLfloat nz, GLfloat tx, GLfloat ty) {
    squareVerts.push_back(x);
    squareVerts.push_back(y);
    squareVerts.push_back(z);
    squareVerts.push_back(nx);
    squareVerts.push_back(ny);
    squareVerts.push_back(nz);
    squareVerts.push_back(tx);
    squareVerts.push_back(ty);
}

std::vector(GLfloat) buildCubeBases(const CubeDimensions& dim,
    const TextureCoords& leftTex,
    const TextureCoords& rightTex,
    const TextureCoords& frontTex,
    const TextureCoords& backTex,
    const TextureCoords& topTex,
    const TextureCoords& bottomTex) {

    std::vector(GLfloat) squareVerts;

    // Top Square
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y + dim.length / 2, dim.z + dim.height / 2, 0.0, 1.0, 0.0, topTex.xStart, topTex.yStop);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y + dim.length / 2, dim.z + dim.height / 2, 0.0, 1.0, 0.0, topTex.xStop, topTex.yStop);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y - dim.length / 2, dim.z + dim.height / 2, 0.0, 1.0, 0.0, topTex.xStart, topTex.yStart);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y - dim.length / 2, dim.z + dim.height / 2, 0.0, 1.0, 0.0, topTex.xStop, topTex.yStart);

    // Front Square
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y - dim.length / 2, dim.z + dim.height / 2, 0.0, 0.0, 1.0, frontTex.xStart, frontTex.yStop);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y - dim.length / 2, dim.z + dim.height / 2, 0.0, 0.0, 1.0, frontTex.xStop, frontTex.yStop);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y - dim.length / 2, dim.z - dim.height / 2, 0.0, 0.0, 1.0, frontTex.xStart, frontTex.yStart);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y - dim.length / 2, dim.z - dim.height / 2, 0.0, 0.0, 1.0, frontTex.xStop, frontTex.yStart);

    // Left Square
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y + dim.length / 2, dim.z + dim.height / 2, -1.0, 0.0, 0.0, leftTex.xStart, leftTex.yStop);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y - dim.length / 2, dim.z + dim.height / 2, -1.0, 0.0, 0.0, leftTex.xStop, leftTex.yStop);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y + dim.length / 2, dim.z - dim.height / 2, -1.0, 0.0, 0.0, leftTex.xStart, leftTex.yStart);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y - dim.length / 2, dim.z - dim.height / 2, -1.0, 0.0, 0.0, leftTex.xStop, leftTex.yStart);

    // Right Square
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y - dim.length / 2, dim.z + dim.height / 2, 1.0, 0.0, 0.0, rightTex.xStart, rightTex.yStop);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y + dim.length / 2, dim.z + dim.height / 2, 1.0, 0.0, 0.0, rightTex.xStop, rightTex.yStop);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y - dim.length / 2, dim.z - dim.height / 2, 1.0, 0.0, 0.0, rightTex.xStart, rightTex.yStart);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y + dim.length / 2, dim.z - dim.height / 2, 1.0, 0.0, 0.0, rightTex.xStop, rightTex.yStart);

    // Back Square
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y + dim.length / 2, dim.z + dim.height / 2, 0.0, 0.0, -1.0, backTex.xStart, backTex.yStop);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y + dim.length / 2, dim.z + dim.height / 2, 0.0, 0.0, -1.0, backTex.xStop, backTex.yStop);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y + dim.length / 2, dim.z - dim.height / 2, 0.0, 0.0, -1.0, backTex.xStart, backTex.yStart);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y + dim.length / 2, dim.z - dim.height / 2, 0.0, 0.0, -1.0, backTex.xStop, backTex.yStart);

    // Bottom Square
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y + dim.length / 2, dim.z - dim.height / 2, 0.0, -1.0, 0.0, bottomTex.xStart, bottomTex.yStart);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y + dim.length / 2, dim.z - dim.height / 2, 0.0, -1.0, 0.0, bottomTex.xStop, bottomTex.yStart);
    addVertex(squareVerts, dim.x - dim.width / 2, dim.y - dim.length / 2, dim.z - dim.height / 2, 0.0, -1.0, 0.0, bottomTex.xStart, bottomTex.yStop);
    addVertex(squareVerts, dim.x + dim.width / 2, dim.y - dim.length / 2, dim.z - dim.height / 2, 0.0, -1.0, 0.0, bottomTex.xStop, bottomTex.yStop);

    return squareVerts;
}

</code>
</pre>
</details>


### Narrative for Artifact Two
This artifact is a rendered 3D scene written in C++ with OpenGL. I wrote a file that does all the work for creating vertices and then rendering them into a 3D space. This scene includes objects of various shapes and sizes as well as individually textured and the scene has lighting. This artifact displays my ability to understand the functionality behind modern technology and that I can learn new skills and languages quickly. OpenGL has many higher level languages and programs that never make you go into such detail for rendering. This shows that I have a grasp at languages at their base forms, meaning I should be able to use that knowledge and create more efficient code. There are many algorithms that were used for creating the vertices of all the objects in the scene and mapping the textures and dealing with lighting. 

To improve this artifact, I focused on the cube creation code that was very messy and hard to read as I did not use the proper data structures and algorithms to keep it clean. I rewrote the cube creation code to include data structures for parameters and texture mapping values. I also cleaned up how I created the cube vertices to be cleaner and included some helper functions and structures. After further review of my code, I was unable to find a way to make it render more efficiently as I realized it was already written in best practices in regards to rendering the shapes. As the code is in base OpenGL, and there is not many vertices to render, the code is very effecient and is difficult to make any more effecient. This led me to focus more on adding data structures for my texture mapping values and fixing up sloppy and unreadable code. 

I learned the importance of taking a second look at the code and cleaning it up to make it stronger and more readable for other programmers. I had some challenges in making sure my objects rendered correctly when changing how the vertices were created, but was successful in the end.


### Full Code Git Repositories
Download Project2 folder and run the .exe file within Debug folder to use view application. Use Microsoft Visual Studio and open the OpenGLSample.sln file to see the code.
- [Original Artifact Two Code](https://github.com/mlineselle/CS-330-Comp-Graphic-and-Visualization.git)
- [Enhanced Artifact Two Code](https://github.com/mlineselle/ArtifactTwoEnhancement.git)
