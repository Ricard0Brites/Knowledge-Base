---
# Render Target View (RTV)

Render targets enable a scene to be rendered to a temporary intermediate buffer, rather than to the back buffer to be rendered to the screen. This feature enables use of the complex scene that might be rendered, perhaps as a reflection texture or other purpose within the graphics pipeline, or perhaps to add additional pixel shader effects to the scene before rendering.

A Render Target View (RTV) specifies the resource that will be used as the render target.
