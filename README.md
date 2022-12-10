# Python-3d-sphere

Here is a simple Python program that uses the VPython library to create and launch a 3D sphere:

```
from vpython import *

# Create a new 3D canvas
scene = canvas()

# Set the background color to black
scene.background = color.black

# Create a new sphere
sphere = sphere(pos=vec(0,0,0), radius=1, color=color.red)

# Set the initial velocity of the sphere
sphere.velocity = vec(1,1,1)

# Function to update the position of the sphere
def update_sphere():
  # Update the position of the sphere
  sphere.pos = sphere.pos + sphere.velocity

  # If the sphere hits a wall, reflect its velocity
  if sphere.pos.x > scene.width/2 or sphere.pos.x < -scene.width/2:
    sphere.velocity.x = -sphere.velocity.x
  if sphere.pos.y > scene.height/2 or sphere.pos.y < -scene.height/2:
    sphere.velocity.y = -sphere.velocity.y
  if sphere.pos.z > scene.width/2 or sphere.pos.z < -scene.width/2:
    sphere.velocity.z = -sphere.velocity.z

  # Call this function again in 1/60 of a second
  scene.waitfor("redraw")
  scene.after(1/60, update_sphere)

# Start the sphere update loop
update_sphere()

```

This code creates a new 3D canvas using the canvas function from VPython, and then creates a new sphere at the origin with a radius of 1 and a red color. The sphere's initial velocity is set to (1,1,1), and a function is defined to update the sphere's position every 1/60 of a second. The function uses the VPython waitfor and after methods to create a continuous update loop. If the sphere hits one of the walls of the canvas, its velocity is reflected to simulate a bouncing effect. You can customize this code to change the appearance or behavior of the sphere, or to add additional objects to the scene.
