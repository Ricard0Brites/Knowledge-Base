---
# Stream Output View (SOV)

Stream output views enable the vertex information that the vertex, tessellation and geometry shaders have come up with to be streamed back out to the application for further use. For example, an object that has been distorted by these shaders could be written back to the application to provide more accurate input to a physics or other engine. In practice though, stream output views are an infrequently used feature of the graphics pipeline.