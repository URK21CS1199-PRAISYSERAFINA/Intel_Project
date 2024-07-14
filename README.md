# TechAura Team - Intel Unnati Industrial Training Program

## Project: Development of a 2D Occupancy Grid Map of a Room Using Overhead Cameras

### Problem Definition
The primary objective of this project is to develop a 2D occupancy grid map of a room using overhead cameras. This grid map will be analogous to the maps created by ROS2-based SLAM algorithms typically used by autonomous mobile robots (AMRs) for path-planning and navigation.

### Description
#### Phase 1: Static Environment Mapping

1. Setup:
    - Equip a room or designated area with four overhead RGB cameras.
    - Arrange the cameras in a 2x2 pattern, ensuring some overlap in their fields of view.
    - The room should contain static objects such as chairs, tables, stools, and boxes.

2. Image Acquisition:
    - Capture images from all four cameras simultaneously.
    - Ensure that the overlap between the fields of view allows for seamless stitching of the images.

3. Image Processing:
    - Stitch the images together to form a comprehensive view of the room.
    - Use image processing techniques to generate a 2D occupancy grid map. This map will     
      indicate occupied and unoccupied spaces in the room.
      
4. Validation:
    - Demonstrate that the generated occupancy grid map can be effectively used by AMRs for   
      path-planning and navigation within the static environment.

#### Phase 2: Dynamic Environment Mapping and Semantic Labeling

1. Dynamic Environment:
    - Modify the room environment by moving objects such as tables and chairs.
    - Capture new images from the overhead cameras to reflect these changes.

2. Dynamic Map Updating:
    - Update the 2D occupancy grid map dynamically to account for the changes in the room.
    - Ensure the updated map accurately represents the current state of the room for AMRs to   
      navigate.

3. Semantic Labeling:
    - Implement simple object detection algorithms to identify and label objects in the room   
      (e.g., "table," "chair," "other AMR").
    - Integrate these semantic labels into the occupancy grid map to provide additional context 
    for the AMRs.
4. Validation:
    - Demonstrate that the dynamically updated and semantically labeled occupancy grid map can 
      be effectively used by AMRs for path-planning and navigation in the dynamic environment.
