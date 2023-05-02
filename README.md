Download Link: https://assignmentchef.com/product/solved-cosc363-lab-4-object-modelling
<br>
This lab introduces object modeling techniques using triangle and quad strips. Such methods are commonly used for triangulating polygonal surfaces and also for generating sweep surfaces.

<ol>

 <li><u> Boat.cpp:</u></li>

</ol>

The program Boat.cpp displays only the grid of the floor plane. It however contains the data required for generating a simple model of a country boat as shown in Fig.1.  We will construct the surfaces of this model using polygonal strips.




Fig. 1.                                                             Fig. 2.

<ol>

 <li>The function drawBase()  contains the vertex coordinates of a polygon shown in Fig. 2.  This polygon represents the base panel of the boat. The polygon has a convex shape, and therefore can be rendered using the primitive type GL_POLYGON  (see slide [5]-3).  Please include the code for drawing this polygon in the drawBase() You should get the output in Fig. 2.</li>

 <li>The function drawSide() contains the vertex coordinates of points <em>V<sub>i</sub></em> and <em>W<sub>i</sub></em> on two polygonal lines forming the bottom and top edges of the side of the boat. Such polygonal shapes can be easily designed by plotting the points on a graph paper (Fig. 3). Both polygonal lines have the same number of points. In the drawSide() function,  include the code for drawing a quad strip (GL_QUAD_STRIP) connecting pairs of  points on the polygonal lines (see slide [5]-8). You should get the output in Fig. 4.  The scene can be rotated using left/right arrow keys.</li>

</ol>







Fig. 3.                                                             Fig. 4.

<ol start="3">

 <li>In the display() function, include a second call to the drawSide() function to generate a copy of this quad strip, and scale it by factors (1, 1, -1) to create a reflection about the xy-plane (Fig. 5.)</li>

</ol>




Fig. 5.

<ol start="4">

 <li>Lighting calculations require the definition of surface normal vectors for each quad in the polygon strips. Include the call to the normal() function in the code for generating the quad strips (see Slide [5]-12).  In the display() function,  change the polygon mode from GL_LINE to GL_FILL, and enable lighting.  You should now get the output shown in Fig. 1.</li>

 <li>Assign texture coordinates to the vertices of the quad strip as shown on Slide [5]13. Enable texturing in the display() You should get an output similar to that in Fig. 6.</li>

</ol>

<u> Vase.cpp:</u>

The program Vase.cpp contains the vertex data for a base curve in arrays vx[<em>i</em>], vy[<em>i</em>], vz[<em>i</em>], <em> i</em> = 0 … <em>N</em>-1,   <em>N</em>=50.  It displays only the floor grid of the scene. The scene can be rotated using left/right arrow keys.  The up/down arrow keys change the height of the camera.

<ol>

 <li>In the display() function, transform each point (vx[<em>i</em>], vy[<em>i</em>], vz[<em>i</em>]) about the y-axis by 10 degrees to form a new set of points (wx[<em>i</em>], wy[<em>i</em>], wz[<em>i</em>]), <em>i</em>=0…<em>N</em>-1. The function already includes the declaration of these array variables. Use the following equations, and include your code after the statement marked “Start here”.  <em>w<sub>x</sub></em> = <em>v<sub>x</sub></em> cos + <em>v<sub>z</sub></em> sin,      = 10 Degs (Convert to radians!) <em>w<sub>y</sub></em> = <em>v<sub>y</sub></em></li>

</ol>

<em>w<sub>z</sub></em> = <em> v<sub>x</sub></em> sin + <em>v<sub>z</sub></em> cos

These points <em>W<sub>i</sub></em> define the rotated base curve. Construct a triangle strip between the two polygonal curves using the method given on slide [5]-8. The required output is shown in Fig. (a).

<ol start="2">

 <li>Copy the coordinates <em>W<sub>i</sub></em> to <em>V<sub>i</sub></em> for the next iteration, and repeat the steps 36 times to get a 360 degree revolution of the base curve (Fig. (b)). Steps 1 and 2 can be implemented as nested loops:</li>

</ol>

for(int j = 0; j &lt; 36; j++)       //36 slices in 10 deg steps

{

for(int i = 0; i &lt; N; i++)   //N vertices along each slice

{

wx[i] = …     //Get transformed points W          wy[i] = …          wz[i] = …

}       glBegin((GL_TRIANGLE_STRIP);  //Create triangle strip using V, W

…

glEnd();




//Copy W array to V for next iteration

}

<ol start="3">

 <li>Now add functions to compute normal vectors at each vertex of the triangle strip as shown on Slide [5]-11. In the display() function, change the polygon mode from GL_LINE to GL_FILL,  and enable lighting. The output with lighting  is given in Fig. (c).</li>

 <li>The program includes the function to load a bitmap texture “VaseTexture.bmp”. We will texture map the image to the whole surface generated above. Assign texture coordinates to the points on the triangle strip, assuming that the points are nearly equally spaced.  In the display() function, enable texture mapping.  Please refer to Slide [5]-18 for more information on computing texture coordinates for the vertices of polygonal strips. The textured output is shown in Fig (d).</li>

</ol>




Fig (d)







<u>Ref</u>:




[5]   Lec05_ObjectModelling.pdf  (COSC363 Lecture notes)




<ul>

 <li><u>cpp</u></li>

</ul>

The Developers Image Library (a.k.a Open Image Library) is a useful library with OpenGL interoperability features, supporting image operations.  It can be used to load textures in PNG, JPG formats. A test file showing the implementation of texture loading functions and a sample image “Colors.png” are provided.  The program loads the image and displays a quad, texture mapped with the image.





