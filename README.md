Vulkan Flocking: compute and shading in one pipeline!
======================
[CLICK ME FOR INSTRUCTION OF THIS PROJECT](./INSTRUCTION.md)

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Akshay Shah
* Tested on: Windows 10, i7-5700HQ @ 2.70GHz 16GB, GTX 970M 6GB (Personal Computer)

### Vulkan Boids flocking simulation

Screenshots
-----------

  ![](img/boids.gif)

Analysis
--------

* <b>Why do you think Vulkan expects explicit descriptors for things like generating pipelines and commands?</b>

  Since Vulkan gets the memory to store command buffers from a preallocated command pool on the GPU, explicit descriptors for pipelines and commands can be used because it cannot be updated once created. Having preallocation, would mean the input and the output of the pipelines would have been already allocated during runtime and has no other overhead. (i.e., One command buffer can be used for multiple data.)

* <b>Describe a situation besides flip-flop buffers in which you may need multiple descriptor sets to fit one descriptor layout.</b>

  When you want to render different textures on the same mesh or have different vertices set for a mesh. For example, you could render a cube or a sphere with the same descriptionLayout just with different sets.

* <b>What are some problems to keep in mind when using multiple Vulkan queues?
  * take into consideration that different queues may be backed by different hardware
  * take into consideration that the same buffer may be used across multiple queues</b>

  Queues are good when there is a lot of operation that is independent of each other. This would mean that these queues could be highly parallelized. Since they are parallelized, any synchronous operation might fail as there is no known order of execution. If the operations involve a lot of transfers between buffers, then a single queue would have better performance.

* <b>What is one advantage of using compute commands that can share data with a rendering pipeline?</b>

  Avoids copying data from input and output.

Bloopers
--------

![](img/boids_bug.gif)

### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)
* [Conrad Parker's notes](http://www.vergenet.net/~conrad/boids/pseudocode.html)
* [2D implementation in Processing](http://studio.sketchpad.cc/sp/pad/view/ro.9cbgCRcgbPOI6/rev.23?)
