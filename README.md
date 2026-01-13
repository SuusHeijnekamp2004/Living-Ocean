# Living-Ocean
Interactive Media installation

# Project name and course description 
Living Ocean is an interactive media installation in which the audience is immersed in a virtual sea filled with schools of fish that respond to sound. The 360° igloo creates an enveloping underwater world in which every sound influences the movements of the fish. Visitors become part of the ecosystem and discover their own presence shapes the environment.  

# Video documentation
Video (behind the scenes)

# Reproducibility
This is how Living Ocean can be replicated in TouchDesigner 2023.12480:

**Step one - Base visual element**
   
1. A single fish image (important! - PNG with transparency) is imported
We start with one 2D fish image where the transparent background ensures only the fish is visible when rendered. 

2. A plane is created and the PNG is mapped onto it.
The plane functions as a stable surface to display the fish image in 3D space. Using a plane avoids visibility and shading issues that can occur when instancing complex or thin geometry directly. It also makes scaling and orientation more predictable.

3. The fish-plane combination is placed inside a geometry COMP
This step defines the fish as a reusable visual element within the scene. Placing it inside a geometry COMP prepares it for instancing and further transformations, allowing the same fish element to be duplicated efficiently throughout the project.

**Step two - Using a Torus as spatial structure**

1. A torus geometry is created
The torus provides a circle structure with evenly distributed vertices. This makes it suitable as a spatial framework for placing multiple objects in a continuous loop. 

2. Vertex positions of the torus are used as instance coordinates
Each vertex of the torus mesh provides X, Y and Z values. These values are connected to the instancing parameters of the fish, determining where each fish is placed in 3D space. 

3. Form and structure are separated
The fish defines the visual appearance, while the torus defines the spatial arrangement. This separation allows us to change the overall structure without modifying the fish geometry itself.

**Step three - Enabling instancing**

1. Instancing is enabled on the geometry COMP
Instancing allows the system to render a large number of fish efficiently using one source geometry. Instead of copying the fish manually, each instance is generated based on external position data.

2. Torus vertex positions are connected to the instancing parameters
The previously prepared torus vertex positions are connected to the Translate X,Y and Z instancing parameters of the geometry COMP. This determines where each fish instance is placed in 3D space.

3. Multiple fish instances are generated automatically
Once the instancing parameters are connected, the single fish element is duplicated across all torus vertex positions, resulting in multiple visible fish instances.

**Step four - Deforming the torus with noise**

1. A noise SOP is applied to the torus
Noise introduces small variations in the torus shape, preventing it from appearing rigid or artificial. The deformation affects all vertex positions. 

2. Fish positions update automatically through instancing
Because the fish instances inherit their position from the torus vertices, any deformation of the torus directly changes the fish distribution. This creates organic, flowing motion without animating each fish individually.

**Step five - Integrating audio input**

1. A microphone input is added to the system
Live audio is used as an external input to influence the visual behavior of the fishes. The audio signal is analyzed and converted into usable control values. 

2. Audio data modulates the noise deformation
The intensity of the sound affects the noise parameters applied to the torus. Louder or more complex audio results in stronger deformation, which in turn changes the fish positions. 

3. Structural control instead of direct animation
Instead of moving the fish directly, the underlying structure (the torus) is manipulated. This keeps the system coherent and easier to control. 

**Step six - Rotation and camera placement**

1. The torus is continuously rotated
Rotation is applied to create a sense of motion and flow. This movement is smooth and consistent, contributing to the illusion of swimming fish. 

2. A camera is placed inside the centre of the torus
  The camera is positioned in the empty space inside the torus and oriented outward. This placement allows the viewer to see only a small section of the rotating structure. 

3. Motion is created relative to the camera
Because the camera remains stationary while the torus rotates, the fish appear to move through space. This approach simplifies animation while maintaining a strong visual effect. 

**Step seven - Resulting system behavior**

1. Fish appear to flow continuously around the viewer
The combination instancing, deformation and rotation creates a dynamic environment. The motion feels continuous rather than looped or mechanical. 

2. The system reacts to audio input in real time
Changes in sound immediately influence the visual structure. This makes the installation responsive and interactive. 

3. Complex behavior emerges from simple components
The final result is produced by combining basic systems rather than complex individual animations. This makes the project modular and expendable. 





