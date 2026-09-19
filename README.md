# SURGE
A Blender addon for generating surf ramp meshes.

For instructions on how to use this addon, check out my tutorial video: https://youtu.be/WWZm1lRNFAs

If you like verbose single-script Python, then have I got a repository for you!

This is my first addon for Blender and my first piece of Python I’ve written, so naturally it’s not the best block of code you are likely to see, but it works! At least in Blender 2.91...

Essentially, It’s just one script file and a custom icon folder. The script is far too long at this point and needs to be separated into multiple files and refactored somewhat, but that’s perhaps something another contributor would like to get involved with. Feel free to fix my code!

## Changes by CoNeJo
- Added a Straight ramp direction using the new `straight.png` icon.
- Straight ramps use Size as their total length and Smoothness as their number of segments.
- Generated meshes are named `<name>_VIS` for the visible mesh and `<name>_CLIP` for the collision mesh.

DONT FORGET $concave
THIS ALLOWS THE PHYSICS MESH TO CURVE WITH THE RAMP, WITHOUT THIS YOU WILL ONLY BE ABLE TO MAKE STRAIGHT RAMPS
Example qc:
$modelname "ramsay/ramps/ramp.mdl"
$cdmaterials "models/ramsay/ramps/"
$body "ramp" "ramp_VIS.smd"


$collisionmodel "ramp_CLIP.smd"
{
    $mass 1
    $inertia 1
    $damping 1
    $rotdamping 1
    $concave
}

$staticprop
$sequence idle "ramp_VIS.smd" fps 1
