---
  permalink: /artifact-two/
  title: "Artifact Two - OpenGL Kitchen Render"
  layout: single
---

<video width="560" height="315" controls muted>
  <source src="/assets/videos/ArtifactTwoVideo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Changes in Data Structures and Algorithms

```
void addVertex(std::vector<GLfloat>& squareVerts, GLfloat x, GLfloat y, GLfloat z, GLfloat nx, GLfloat ny, GLfloat nz, GLfloat tx, GLfloat ty) {
    squareVerts.push_back(x);
    squareVerts.push_back(y);
    squareVerts.push_back(z);
    squareVerts.push_back(nx);
    squareVerts.push_back(ny);
    squareVerts.push_back(nz);
    squareVerts.push_back(tx);
    squareVerts.push_back(ty);
}

std::vector<GLfloat> buildCubeBases(const CubeDimensions& dim,
    const TextureCoords& leftTex,
    const TextureCoords& rightTex,
    const TextureCoords& frontTex,
    const TextureCoords& backTex,
    const TextureCoords& topTex,
    const TextureCoords& bottomTex) {

    std::vector<GLfloat> squareVerts;

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

// Create cube indices for all triangles

std::vector<GLushort> createCubeIndices() {
    // Initialize vector for cube indices
    std::vector<GLushort> cubeIndices;

    // Define the base indices for the cube faces
    std::array<std::array<GLushort, 4>, 6> faceIndices = { {
        {0, 1, 2, 3},  // Top face
        {21, 20, 22, 23},  // Bottom face
        {16, 17, 18, 19},  // Back face
        {12, 13, 14, 15},  // Right face
        {4, 5, 6, 7},  // Front face
        {8, 9, 10, 11}  // Left face
    } };

    // Loop through each face to add the indices
    for (const auto& face : faceIndices) {
        cubeIndices.push_back(face[0]);
        cubeIndices.push_back(face[1]);
        cubeIndices.push_back(face[2]);
        cubeIndices.push_back(face[1]);
        cubeIndices.push_back(face[3]);
        cubeIndices.push_back(face[2]);
    }

    return cubeIndices;
}
```

### Narrative for Artifact Two
This artifact is a rendered 3D scene written in C++ with OpenGL. I wrote a file that does all the work for creating vertices and then rendering them into a 3D space. This scene includes objects of various shapes and sizes as well as individually textured and the scene has lighting. This artifact displays my ability to understand the functionality behind modern technology and that I can learn new skills and languages quickly. OpenGL has many higher level languages and programs that never make you go into such detail for rendering. This shows that I have a grasp at languages at their base forms, meaning I should be able to use that knowledge and create more efficient code. There are many algorithms that were used for creating the vertices of all the objects in the scene and mapping the textures and dealing with lighting. 

To improve this artifact, I focused on the cube creation code that was very messy and hard to read as I did not use the proper data structures and algorithms to keep it clean. I rewrote the cube creation code to include data structures for parameters and texture mapping values. I also cleaned up how I created the cube vertices to be cleaner and included some helper functions and structures. After further review of my code, I was unable to find a way to make it render more efficiently as I realized it was already written in best practices in regards to rendering the shapes. As the code is in base OpenGL, and there is not many vertices to render, the code is very effecient and is difficult to make any more effecient. This led me to focus more on adding data structures for my texture mapping values and fixing up sloppy and unreadable code. 

I learned the importance of taking a second look at the code and cleaning it up to make it stronger and more readable for other programmers. I had some challenges in making sure my objects rendered correctly when changing how the vertices were created, but was successful in the end.


### Full Code Git Repositories
Download Project2 folder and run the .exe file within Debug folder to use view application. Use Microsoft Visual Studio and open the OpenGLSample.sln file to see the code.
- [Original Artifact Two Code](https://github.com/mlineselle/CS-330-Comp-Graphic-and-Visualization.git)
- [Enhanced Artifact Two Code](https://github.com/mlineselle/ArtifactTwoEnhancement.git)
