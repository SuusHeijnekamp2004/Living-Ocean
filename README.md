# Living-Ocean 🐠 🌊
Interactive Media installation

# 1. Course description 
Living Ocean is an interactive media installation in which the audience is immersed in a virtual sea filled with schools of fish that respond to sound. The 360° igloo creates an enveloping underwater world in which every sound influences the movements of the fish. Visitors become part of the ecosystem and discover their own presence shapes the environment. 

# 2. Video documentation
Video (behind the scenes)


# 3. Reproducibility
This is how Living Ocean can be replicated in TouchDesigner 2023.12480:

### Step one - Base visual element
   
1. A single fish image (important! - PNG with transparency) is imported
We start with one 2D fish image where the transparent background ensures only the fish is visible when rendered. 

2. A plane is created and the PNG is mapped onto it.
The plane functions as a stable surface to display the fish image in 3D space. Using a plane avoids visibility and shading issues that can occur when instancing complex or thin geometry directly. It also makes scaling and orientation more predictable.

3. The fish-plane combination is placed inside a geometry COMP
This step defines the fish as a reusable visual element within the scene. Placing it inside a geometry COMP prepares it for instancing and further transformations, allowing the same fish element to be duplicated efficiently throughout the project.

### Step two - Using a Torus as spatial structure

1. A torus geometry is created
The torus provides a circle structure with evenly distributed vertices. This makes it suitable as a spatial framework for placing multiple objects in a continuous loop. 

2. Vertex positions of the torus are used as instance coordinates
Each vertex of the torus mesh provides X, Y and Z values. These values are connected to the instancing parameters of the fish, determining where each fish is placed in 3D space. 

3. Form and structure are separated
The fish defines the visual appearance, while the torus defines the spatial arrangement. This separation allows us to change the overall structure without modifying the fish geometry itself.

### Step three - Enabling instancing

1. Instancing is enabled on the geometry COMP
Instancing allows the system to render a large number of fish efficiently using one source geometry. Instead of copying the fish manually, each instance is generated based on external position data.

2. Torus vertex positions are connected to the instancing parameters
The previously prepared torus vertex positions are connected to the Translate X,Y and Z instancing parameters of the geometry COMP. This determines where each fish instance is placed in 3D space.

3. Multiple fish instances are generated automatically
Once the instancing parameters are connected, the single fish element is duplicated across all torus vertex positions, resulting in multiple visible fish instances.

### Step four - Deforming the torus with noise

1. A noise SOP is applied to the torus
Noise introduces small variations in the torus shape, preventing it from appearing rigid or artificial. The deformation affects all vertex positions. 

2. Fish positions update automatically through instancing
Because the fish instances inherit their position from the torus vertices, any deformation of the torus directly changes the fish distribution. This creates organic, flowing motion without animating each fish individually.

### Step five - Integrating audio input 

1. A microphone input is added to the system
Live audio is used as an external input to influence the visual behavior of the fishes. The audio signal is analyzed and converted into usable control values. 

2. Audio data modulates the noise deformation
The intensity of the sound affects the noise parameters applied to the torus. Louder or more complex audio results in stronger deformation, which in turn changes the fish positions. 

3. Structural control instead of direct animation
Instead of moving the fish directly, the underlying structure (the torus) is manipulated. This keeps the system coherent and easier to control. 

### Step six - Rotation and camera placement

1. The torus is continuously rotated
Rotation is applied to create a sense of motion and flow. This movement is smooth and consistent, contributing to the illusion of swimming fish. 

2. A camera is placed inside the centre of the torus
  The camera is positioned in the empty space inside the torus and oriented outward. This placement allows the viewer to see only a small section of the rotating structure. 

3. Motion is created relative to the camera
Because the camera remains stationary while the torus rotates, the fish appear to move through space. This approach simplifies animation while maintaining a strong visual effect. 

### Step seven - Resulting system behavior

1. Fish appear to flow continuously around the viewer
The combination instancing, deformation and rotation creates a dynamic environment. The motion feels continuous rather than looped or mechanical. 

2. The system reacts to audio input in real time
Changes in sound immediately influence the visual structure. This makes the installation responsive and interactive. 

3. Complex behavior emerges from simple components
The final result is produced by combining basic systems rather than complex individual animations. This makes the project modular and expendable.


# 4. Communication diagram
**Hardware used:** 
- Asus Zenbook 14 & Dell XPS 15 9520
- 5 Projectors

**Software used:**
- TouchDesigner (2023.12480, non-commercial)

**Diagram:**

<img width="2000" height="1414" alt="Communication diagram" src="https://github.com/user-attachments/assets/cd63e962-0464-4065-aef5-d5b03259bbc7" />

# 5. Production process

## Planning and development process

At the start of the project, the team explored several concepts for an interactive installation in the 360° igloo. Although the initial idea showed potential, the team realized during this exploration phase that they were unable to fully develop it into a clear and workable concept within the possibilities of the igloo. 

However, one principle remained clear from the beginning: the installation needed to be interactive and actively involve the visitor in the experience. 

In a later phase of the project, the concept Living Ocean emerged: an audiovisual underwater world in which fish respond to sound. This idea offered both creative and technical opportunities to place interaction at the core of the experience. After finalizing the concept, the installation was developed in TouchDesigner, where visual elements were linked to sound input. Through iterative testing and refinement, the behaviour of the fish was fine-tuned. Ultimately, the interactive underwater world was integrated into the 360° igloo, resulting in an immersive experience in which the audience and environment are directly connected.   

## Rejected solutions

Initially, the team worked on a different concept for the igloo, but due to a lack of knowledge and experience, we were unable to fully develop it. The concept did not provide enough guidance to make it concrete and feasible, so it was eventually abandoned. The team then decided to focus on creating an installation when interaction is central. Which led to the concept: Living Ocean. 

Since none of the team members had experience with TouchDesigner or previous projects in this field, many technical choices and solutions had to be discovered through trial and error during the project.This meant that some initial ideas were too complex or time-consuming to implement and therefore had to be adapted or replaced. 

## Failures and replanning
  
During development, we realized that creating complex fish movements was technically very challenging. The team originally intended for the fish to swim in different directions to make it look more organic. However, due to a lack of knowledge of TouchDesigner and limited available time, this proved unfeasible. Therefore, we simplified the animation: the fish respond to sound and change position, making the interaction clearly visible without overloading the technical setup. 

## Challenges
  
Working with TouchDesigner was completely new and the complexity of the software was initially underestimated. 
Much technical knowledge had to be acquired during the project itself, which was time-consuming.
Developing a consistent and responsive fish reaction to sound required extensive testing and replanning. 

## Task distribution

We worked with a team of three: Sanne van Lierop, Nina Travers & Suus Heijnekamp. Throughout the entire project, the team worked closely together. From the initial concept to the final implementation, all decisions were made collaboratively and tasks were distributed in a flexible and cooperative manner. Due to lack of experience with TouchDesigner and interactive installations, we worked on almost all aspects of the project together. This allowed us to learn as a team, solve problems as they arose, and ensure that everyone understood each part of the installation. 

To remain efficient while writing the report, we divided some of the tasks so that each member could work on a section individually. At the same time, everyone reviewed each other’s work to ensure quality and consistency.

## Tools
  
ChatGPT: 
We used ChatGPT to help us with TouchDesigner whenever we were unsure how to proceed, and to assist in organizing and structuring our project documentation.
Support of the teachers Phillip Krüger and Jan Fiess.

## Known bugs
  
The project functions properly in the Igloo on Campus Somedia at FHGR. 

## Learning effect

- The Living Ocean project was a valuable learning experience for all team members, especially since none of us had previous experience with TouchDesigner or interactive installations. Throughout the process, we acquired many new skills and insights, including:
- Setting up and structuring a TouchDesigner network from scratch.
- Working with audio inputs to generate interactive fish responses.
- Experimenting with visual effects, movements, and particle systems in a 360° environment. 
- Understanding the interplay between audio, visuals, interaction, and the physical space of the igloo. 
- Collaborating effectively as a team with limited technical knowledge, reviewing each other’s work, and solving problems together.


# 6. Project video 🎥
Final Video

# 7. Screenshots TouchDesigner
![Screenshot 2026-01-13 155808](https://github.com/user-attachments/assets/6749a768-5feb-4c56-9629-d4ccc3f8b86d)






