# Rainy-Day-shader
Volumetric lightmap based lighting and atmospheric scattering shader demo for MCPE 1.18.12
##  Usage Requirements
The following conditions has to be met in order to use this shader
- Minecraft: Pocket Edition (Bedrock Edition for mobile devices) 1.18.12
	- May or may not work on versions prior to 1.18.12
	- Doesn't work on newer versions because of Render Dragon
- Support for `GL_ARM_shader_framebuffer_fetch_depth_stencil` and either `GL_EXT_shader_framebuffer_fetch` or `GL_ARM_shader_framebuffer_fetch` GLSL extensions
	- OpenGL ES 3.0
	- ARM processor
- Rain or Snow
	- This shader only works during the rain or snow
##  Features
- #### Volumetric atmospheric light scattering
	- Preetham atmospheric scattering model
	- Sun is always assumed to be directly above
- #### Lightmap based volumetric lighting
	- Blocks have a vlolumetric lighting effect, based on their lightmap brightness
	- Only works on the terrain surface if there are no blocks above
- #### Settings
  - Ray marching distance can be configured in the pack settings, by pressing a cog button when applying the pack

## How it works
- In MCPE rain and snow shaders have access to a special texture, that contains the heightmap of the terrain as well as lighting values from the lightmap. This texture is used to light the raindrops based on light level on the surface and to make sure that the rain doesn't go through blocks. Rainy Day shader ray marches across that texture, checking nearby blocks and accumulating lighting from both the atmosphere scattered light and block lighting from the lightmap. It uses GLSL extensions to sample the depth and color of already rendered pixels from the framebuffer to make sure that lighting behind objects doesn't contributes to the image. Computed lighting gets added to the existing framebuffer color which then has ACES tonemapper applied to it before getting displayed on the screen.

## Screenshots

[![Le Ultimate RTX (Java map)](https://cdn.discordapp.com/attachments/327203882180542484/1096779081929994320/Screenshot_20230408-211617.png "Le Ultimate RTX (Java map)")](https://www.mediafire.com/file/of1821ywjctxzyh/le_ultimate_rtx14.zip/file "Le Ultimate RTX (Java map)")

![Vanilla screenshot](https://cdn.discordapp.com/attachments/327203882180542484/1099249612272967731/Screenshot_20230422-102254.png "Vanilla screenshot")

![Vanilla screenshot](https://cdn.discordapp.com/attachments/327203882180542484/1096798130105753782/Screenshot_20230409-202753.png "Vanilla screenshot")

[![Le Ultimate RTX (Java map)](https://cdn.discordapp.com/attachments/327203882180542484/1096779082341031956/Screenshot_20230408-211323.png "Le Ultimate RTX (Java map)")](https://www.mediafire.com/file/of1821ywjctxzyh/le_ultimate_rtx14.zip/file "Le Ultimate RTX (Java map)")

[![Le Ultimate RTX (Java map)](https://cdn.discordapp.com/attachments/327203882180542484/1096779082697551902/Screenshot_20230408-211247.png "Le Ultimate RTX (Java map)")](https://www.mediafire.com/file/of1821ywjctxzyh/le_ultimate_rtx14.zip/file "Le Ultimate RTX (Java map)")
