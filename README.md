# pygl
Assorted PyGL and PyGLUT mini-projects

## History
I've been doing OpenGL since before it was OpenGL (IrisGL on SiliconGraphics workstations, starting back in 1990), but it had been a while and I wanted to start my own code-base (not my various employers'...).  And I like Python.  So I searched up "python glut" and ran across http://www.lighthouse3d.com/tutorials/glut-tutorial/.  This is in C/C++ but IMO a really nicely put together tutorial project, introducing concepts and corresponding code in sensible stages; feel free to go learn.

So I started with a simple "display a shaded sphere" demo (and of course don't remember where I found it, possibly at the above but probably somewhere else.  Also, I'll add some notes here about where to get the GL, GLU (utilities) and GLUT (stuff specific to creating a platform-specific window to render into and handling keyboard/mouse/etc input) libraries.

From there, between the sphere-demo code and the tutorials above, I've started putting together a more object-oriented project (in Python as I hinted at above), adding functionality as I needed it to do the next thing I felt like creating.  Listed in the next section....

## Demos

**Sphere** -- the sample code I pulled off the internet, this isn't mine.  Sets up the GL basics, and draws a lit glutSolidSphere().  When I rediscover where I found it, I'll provide credit in the source and here.

**Other shapes** -- dicing a square into sub-squares, and creating a cylinder following the same idea as for glutSolidSphere(), used for placing a camera, specifying field-of-view and aspect-ratio, etc.

**Vases** -- "Swept surfaces", in this case, a curve rotated around the Z-axis.  The curve is approximated by a set of points, and the surface by replacing each point with a "ring" of N points at the same distance from the Z-axis.  If the rings are all aligned, the surface is a set of "rectangle"-shaped quads (well trapezoids, since the top & bottom are parallel but have different lengths except when the distance from the Z-axis is the same for successive rings).  If they're offset from each other by rotating alternate rings so the points fall halfway between the others (360 degrees / 2N), the surface becomes a set of "diamond"-shaped quads (with triangles at the top & bottom edges of the surface.  I added the ability to rotate each ring by an arbitrary constant amount to skew the diamonds.

**Mushrooms** -- More swept-surfaces, an initial part of an art project based in equal parts on Alice in Wonderland, environments in World of Warcraft, and faery-themed art.

**Bouncing Cubes** -- Animation tests, both animating the cubes, and animating the view-point (including the ability to mouse-drag to update, and continue the rotation on release).

**Color Samples** -- visualize (eventually) the colors in a subset of a color-space. Animates a bunch of "color chips" at the corresponding 3D location and resulting color in the space, supports increasing/decreasing the number of chips shown at a time, size of chips, rate at which chips are added/removed. TODO: add color spaces other than RGB; support picking a central color-of-interest and orientation of primary axes (eigenvectors!) for the subspace of color; turn on/off z-buffering (so chips "in front" don't always hide chips "in back".  Based on a project from the mind of the late Prof. Ken "Mojo" Musgrave.

**Shells** -- from a lightweight SIGGRAPH or IEEE article on rendering sea-shells.  For simplicity, creates a spiral seashell shape from a set of overlapping spheres (though could be arbitrarily fancier).  Formula for size, height, and distance-from-z-axis, of each sphere as a function of it's angular position, substantially impacts resulting spiral shape.

**Fountain** -- Started by spewing somewhat randomized animated particles.  Started updating this to replace a single particle with a trail where the animated particle is the "head" of the trail, and the trail represents a partial history of the particle's position (fading as it goes back in time, maybe for a total of a half-second or so), still needs work.  A modification of the Trail class could be used animate simple Fireworks, or anywhere else where motion-blur or other time-accumulated view of a point is of interest.

**Flowers** -- From an old Silicon Graphics screen-saver, 2D geometric flower where each petal is a simple diamond-shape.  TODO: animate by spinning each flower, and animating its petal-shape, and then having them bounce around the screen.  Why not?

**Fractal Clock** -- an idea from an iPhone or Mac OSX screen-saver, easy enough to duplicate.  Create a swirling fractal collection of lines based on the current time as displayed on an analog clock (with hour, minute & second hands).  Allow the user to control the number of fractal generations, the amount by which the next generation is shrunk (or grown) compared to the previous, the amount by which the color is faded into the background at each generation, and a temporary "hide" (or nearly hide) the fractal-part to clearly see just the current time.

## Projects

**Cleaning up / improving the wrapper classes**

**Mini-Minecraft** -- create and display a world based on cubes, be able to add/remove cubes, be able to "walk" and "fly" over the world.

**More to come**
