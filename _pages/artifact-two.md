---
  permalink: /artifact-two/
  title: "Artifact Two - OpenGL Kitchen Render"
  layout: single
---

<video width="560" height="315" controls muted>
  <source src="https://github.com/mlineselle/portfolio/raw/main/assets/videos/ArtifactTwoVideo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Changes in Data Structures and Algorithms


### Narrative for Artifact Two
This artifact is a rendered 3D scene written in C++ with OpenGL. I wrote a file that does all the work for creating vertices and then rendering them into a 3D space. This scene includes objects of various shapes and sizes as well as individually textured and the scene has lighting. This artifact displays my ability to understand the functionality behind modern technology and that I can learn new skills and languages quickly. OpenGL has many higher level languages and programs that never make you go into such detail for rendering. This shows that I have a grasp at languages at their base forms, meaning I should be able to use that knowledge and create more efficient code. There are many algorithms that were used for creating the vertices of all the objects in the scene and mapping the textures and dealing with lighting. To improve this artifact, I focused on the cube creation code that was very messy and hard to read as I did not use the proper data structures and algorithms to keep it clean. I rewrote the cube creation code to include data structures for parameters and texture mapping values. I also cleaned up how I created the cube vertices to be cleaner and included some helper functions and structures. After further review of my code, I was unable to find a way to make it render more efficiently as I realized it was already written in best practices in regards to rendering the shapes. As the code is in base OpenGL, and there is not many vertices to render, the code is very effecient and is difficult to make any more effecient. This led me to focus more on adding data structures for my texture mapping values and fixing up sloppy and unreadable code. I learned the importance of taking a second look at the code and cleaning it up to make it stronger and more readable for other programmers. I had some challenges in making sure my objects rendered correctly when changing how the vertices were created, but was successful in the end.


### Full Code Git Repositories
Download Project2 folder and run the .exe file within Debug folder to use view application. Use Microsoft Visual Studio and open the OpenGLSample.sln file to see the code.
- [Original Artifact Two Code](https://github.com/mlineselle/CS-330-Comp-Graphic-and-Visualization.git)
- [Enhanced Artifact Two Code](https://github.com/mlineselle/ArtifactTwoEnhancement.git)
