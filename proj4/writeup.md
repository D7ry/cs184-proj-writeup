# CS 184: Computer Graphics and Imaging, Spring 2023
# Project 4: Cloth Simulator

## Overview

In this project, we built a cloth simulator using the mass-spring system that supports self-collision, object-collision, and shaders. This project is really cool.

## Part I: Masses and Springs

### Take some screenshots of scene/pinned2.json from a viewing angle where you can clearly see the cloth wireframe to show the structure of your point masses and springs.
<table>
  <tr>
    <td align="center"><img src="images/p1_wireframe_s1.png" width="400px"></td>
    <td align="center"><img src="images/p1_wireframe_s2.png" width="400px"></td>
  </tr>
</table>

### Show us what the wireframe looks like (1) without any shearing constraints, (2) with only shearing constraints, and (3) with all constraints.
<table>
  <tr>
    <td align="center">
	<img src="images/p1_constraint_shearing_off.png" width="400px">
	        <figcaption>without shearing constraints</figcaption>
	</td>
    <td align="center">
	<img src="images/p1_constraint_shearing_only.png" width="400px">
	        <figcaption>with only shearing constraint</figcaption>
	</td>
	<td align="center">
	<img src="images/p1_constraint_all.png" width="400px">
	        <figcaption>with all constraints</figcaption>
	</td>
  </tr>
</table>

## Part II: Simulation via numerical integration

### Describe the effects of changing the spring constant ks; how does the cloth behave from start to rest with a very low ks? A high ks?

Ks determines the stiffness of the springs. A really low ks makes the cloth very loose and the cloth sags a lot. A high ks makes the cloth very stiff, and as a result, more resistant to external forces. Visually, the cloth is more "crisp" with a high ks.

<table>
  <tr>
    <td align="center">
	<img src="images/p2_ks_small.png" width="400px">
	        <figcaption>Small ks</figcaption>
	</td>
    <td align="center">
	<img src="images/p2_ks_default.png" width="400px">
	        <figcaption>Default ks</figcaption>
	</td>
	<td align="center">
	<img src="images/p2_ks_big.png" width="400px">
	        <figcaption>Big ks</figcaption>
	</td>
  </tr>
</table>

With big ks, the cloth seems to be extremely tight that it tries to pull itself together. This reminds me balloons.

### What about for density?

Density changes the cloth's mass per unit and therefore, inertia and resistance to external forces. A higher density makes the cloth heavier and more resistant to external forces, making it harder to move around; the cloth also tend to sag more. A lower density makes the cloth lighter and more susceptible to external forces, making it easier to move around; the cloth also tends to sag less.

<table>
  <tr>
    <td align="center">
	<img src="images/p2_density_low.png" width="400px">
	        <figcaption>Low density</figcaption>
	</td>
    <td align="center">
	<img src="images/p2_density_default.png" width="400px">
	        <figcaption>Default density</figcaption>
	</td>
	<td align="center">
	<img src="images/p2_density_high.png" width="400px">
	        <figcaption>High density</figcaption>
	</td>
  </tr>
</table>

With low density, the cloth appears to be visually lighter too since it sags much less. It makes the viewer feel as if less force is pulling the cloth down.

### What about for damping?

Damping determines the amount of energy loss for each simulation. A higher damping makes the cloth lose energy faster, making it less likely to oscillate. A lower damping makes the cloth lose energy slower, making it more likely to oscillate, i.e. more dynamic yet less stable.

<table>
  <tr>
    <td align="center">
	<img src="images/p2_damping_0.png" width="400px">
	        <figcaption>Low damping</figcaption>
	</td>
    <td align="center">
	<img src="images/p2_damping_default.png" width="400px">
	        <figcaption>Default damping</figcaption>
	</td>
	<td align="center">
	<img src="images/p2_damping_high.png" width="400px">
	        <figcaption>High damping</figcaption>
	</td>
  </tr>
</table>

The images above are taken 1 second into the simulation. With damping set to zero, the cloth oscillates a lot; with higher damping values, the cloth oscillates a lot less and stops really quickly, with gravity being the only force that pulls the cloth down.

### For each of the above, observe any noticeable differences in the cloth compared to the default parameters and show us some screenshots of those interesting differences and describe when they occur.

see above.

### Show us a screenshot of your shaded cloth from scene/pinned4.json in its final resting state! If you choose to use different parameters than the default ones, please list them.

<table>
  <tr>
    <td align="center"><img src="images/p2_pinned_4_final_state.png" width="400px"></td>
	<figcaption>Final state of pinned4.json</figcaption>
  </tr>
</table>

## Part III: Handling collisions with other objects
### Show us screenshots of your shaded cloth from scene/sphere.json in its final resting state on the sphere using the default ks = 5000 as well as with ks = 500 and ks = 50000. Describe the differences in the results.

<table>
  <tr>
    <td align="center">
	<img src="images/p3_sphere_ks_500.png" width="400px">
	        <figcaption>ks = 500</figcaption>
	</td>
    <td align="center">
	<img src="images/p3_sphere_ks_5000.png" width="400px">
	        <figcaption>ks = 5000</figcaption>
	</td>
	<td align="center">
	<img src="images/p3_sphere_ks_50000.png" width="400px">
	        <figcaption>ks = 50000</figcaption>
	</td>
  </tr>
</table>

Simulations with lower ks appears to be less stiff and more soggy. The cloth drapes more loosely on the sphere. Simulations with high ks(50000) looks very stiff and crisp, and the cloth drapes very tightly on the sphere, with most part "folding" together on one of the 4 sides, with much fewer folds.

### Show us a screenshot of your shaded cloth lying peacefully at rest on the plane. If you haven't by now, feel free to express your colorful creativity with the cloth! (You will need to complete the shaders portion first to show custom colors.)

<table>
<tr>
	<td align="center">
	<img src="images/p3_peacefully_lying.png" width="400px">
	<figcaption>peace</figcaption>
	</td>
</tr>
</table>

## Part IV: Handling self-collisions


### Show us at least 3 screenshots that document how your cloth falls and folds on itself, starting with an early, initial self-collision and ending with the cloth at a more restful state (even if it is still slightly bouncy on the ground).

<table>
  <tr>
    <td align="center">
	<img src="images/p4_collision_1.png" width="400px">
	</td>
    <td align="center">
	<img src="images/p4_collision_2.png" width="400px">
	</td>
	<td align="center">
	<img src="images/p4_collision_3.png" width="400px">
	</td>
  </tr>
</table>


### Vary the density as well as ks and describe with words and screenshots how they affect the behavior of the cloth as it falls on itself.

Higher density makes the cloth heavier, and it tends to collapse onto itself more, lower density makes the cloth lighter and it tends to spread out more. The fold is also more pronounced with higher density.

<table>
  <tr>
    <td align="center">
	<img src="images/p4_density_low.png" width="400px">
		        <figcaption>low density</figcaption>
	</td>
    <td align="center">
	<img src="images/p4_density_default.png" width="400px">
			        <figcaption>default density</figcaption>
	</td>
	<td align="center">
	<img src="images/p4_density_high.png" width="400px">
				        <figcaption>high density</figcaption>
	</td>
  </tr>
</table>

Variation in ks affects the speed of the cloth's collapse. Higher ks makes the cloth collapse faster, lower ks makes the cloth collapse slower, as the cloth has less force to pull itself together. The following 3 images are taken 5 seconds into the simulation; cloth with higher ks appears to be "folding" more quickly and looks more "crisp" due to the more pronounced folds as a result of the higher ks. Cloth with low ks looks as if it's having a hard time pulling itself together.

<table>
  <tr>
    <td align="center">
	<img src="images/p4_ks_low.png" width="400px">
		        <figcaption>low ks</figcaption>
	</td>
    <td align="center">
	<img src="images/p4_ks_default.png" width="400px">
			        <figcaption>default ks</figcaption>
	</td>
	<td align="center">
	<img src="images/p4_ks_high.png" width="400px">
				        <figcaption>high ks</figcaption>
	</td>
  </tr>
</table>



## Part V: Shaders

### Explain in your own words what is a shader program and how vertex and fragment shaders work together to create lighting and material effects.

A shader program is a program, typically run by GPU, that takes in a vertex or a fragment and a bunch of parameters, and outputs how the vertex or fragment should be rendered. 

Vertex and fragment shaders are the two main components of the shader program. Vertex shaders process individual vertices of a 3D mesh, outputting their position and shading properties such as color and texture. Fragment shaders process fragments of vertex shader's outputs, for example, pixels, and output the final color of the pixel, which is then rendered on the screen.

### Explain the Blinn-Phong shading model in your own words. Show a screenshot of your Blinn-Phong shader outputting only the ambient component, a screen shot only outputting the diffuse component, a screen shot only outputting the specular component, and one using the entire Blinn-Phong model.

The Blinn-Phong shading model is a superset of diffuse shading. Blinn-Phong shading comprises 3 parts: diffuse lighting, ambient lighting, and specular lighting. Diffuse lighting is the most basic reflection from an object, while specular lighting depends on the camera angle, and ambient lighting is the light that is reflected from the environment. Together, the 3 lighting components creates a realistic rendering of the object.

<table>
  <tr>
    <td align="center">
	<img src="images/p5_phong_ambient.png" width="400px">
		        <figcaption>Only ambient</figcaption>
	</td>
    <td align="center">
	<img src="images/p5_phong_diffuse.png" width="400px">
			        <figcaption>Only diffuse</figcaption>
	</td>
	<td align="center">
	<img src="images/p5_phong_specular.png" width="400px">
				        <figcaption>Only specular</figcaption>
	</td>
  </tr>
</table>

<table>
<tr>
	<td align="center">
	<img src="images/p5_phong_all.png" width="400px">
		        <figcaption>Ambient, diffuse, and specular</figcaption>
	</td>
</tr>
</table>

### Show a screenshot of your texture mapping shader using your own custom texture by modifying the textures in /textures/.
<table>
<tr>
	<td align="center">
	<img src="images/p5_texture_modified.png" width="400px">
	<figcaption>Modified texture</figcaption>
	</td>
</tr>
</table>

### Show a screenshot of bump mapping on the cloth and on the sphere. 

<table>
  <tr>
	<td align="center">
	<img src="images/p5_bump_cloth.png" width="400px">
		        <figcaption>Bump mapping on cloth</figcaption>
	</td>
	<td align="center">
	<img src="images/p5_bump_sphere.png" width="400px">
			        <figcaption>Bump mapping on sphere</figcaption>
	</td>
  </tr>
  </table>

### Show a screenshot of displacement mapping on the sphere. Use the same texture for both renders. You can either provide your own texture or use one of the ones in the textures directory, BUT choose one that's not the default texture_2.png. 

<table>
<tr>
	<td align="center">
	<img src="images/p5_displacement_sphere.png" width="400px">
		        <figcaption>Displacement mapping on sphere</figcaption>
	</td>
</tr>
</table>


### Compare the two approaches and resulting renders in your own words. 

While both approaches give the illusion of a 3D object, bump mapping provides a more stable and less "3D" appearance than displacement mapping. Displacement mapping is more "3D", but may look weird depending on the depth of the displacement, as it directly changes vertex positions. Bump mapping is more stable, but may look less "3D" depending on the strength of the bump. Both react to light.

### Compare how your the two shaders react to the sphere by changing the sphere mesh's coarseness by using -o 16 -a 16 and then -o 128 -a 128.

<table>
  <tr>
    <td align="center">
	<img src="images/p5_low_res_bump.png" width="400px">
		        <figcaption>16 * 16, bump</figcaption>
	</td>
    <td align="center">
	<img src="images/p5_low_res_displacement.png" width="400px">
			        <figcaption>16 * 16, displacement</figcaption>

  </tr>
  <tr>
  	</td>
	<td align="center">
	<img src="images/p5_high_res_bump.png" width="400px">
				        <figcaption>128 * 128, bump</figcaption>
	</td>
	  	</td>
	<td align="center">
	<img src="images/p5_high_res_displacement.png" width="400px">
				        <figcaption>128 * 128, displacement</figcaption>
	</td>
	</tr>
</table>

Per the above comparison, changes in coarseness manifest most clearly on the displacement shader. The higher resolution the sphere has, the more protrusion i.e. 3D-ness the displacement shader shows. The bump shader, on the other hand, is more stable and less affected by coarseness. If one look very closely, the bump shader does show some extra details on the higher resolution sphere, but it is not as pronounced as the displacement shader.


### Show a screenshot of your mirror shader on the cloth and on the sphere.
