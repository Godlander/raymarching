# Raymarching Resourcepack

To see the shader, equip the resourcepack, load into a world, and summon a glowing end crystal with a beam. The end of the beam will be the center of the rendered scene.

```mcfunction
summon end_crystal x y z {Glowing:1b,BeamTarget:{X:x,Y:y,Z:z}}
```

make sure to replace the `x` `y` and `z` with your own coordinates.

![image](https://user-images.githubusercontent.com/16228717/170604180-cf979f10-dca2-4141-b1a4-1640d2fb470d.png)

# Editing the shader

### adding shapes

to add new shapes, make sure that the sdf function for that shape is defined, then it is as simple as following the format, setting a position, size, and material in the `hit` function.

for example, adding a new two unit tall cube with pink material:
```glsl
o = Add(o, Cube(pos + vec3(-2,1,-3), vec3(1,2,1), 2));
```

### adding materials

in the `render` function, find the `switch` on `o.type` and add a new case. you can change the color there, and apply shadows or sunlight to it.

in the `hit` function, you can change any object added to the scene to the new material.
