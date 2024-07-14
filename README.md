# TechAura Team - Intel Unnati Industrial Training Program

## Project: Development of a 2D Occupancy Grid Map of a Room Using Overhead Cameras

## 1. Problem Definition
The primary objective of this project is to develop a 2D occupancy grid map of a room using overhead cameras. This grid map will be analogous to the maps created by ROS2-based SLAM algorithms typically used by autonomous mobile robots (AMRs) for path-planning and navigation.

## Description
### Phase 1: Static Environment Mapping

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

### Phase 2: Dynamic Environment Mapping and Semantic Labeling

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

## 2. Solution Approach

Our solution involves setting up four overhead RGB cameras in a 2x2 pattern to capture overlapping images of a room. Initially, we will capture images of a room with static objects, then stitch these images together to create a unified view, applying preprocessing techniques to enhance image quality. From this unified view, we will generate a 2D occupancy grid map that indicates occupied and unoccupied spaces. To accommodate dynamic environments, we will implement object detection algorithms to recognize and label objects such as "table" and "chair," updating the occupancy grid map to reflect changes in object positions. The updated map will integrate semantic labels for additional context, ensuring it accurately represents the room's current state. Finally, we will validate the effectiveness of the occupancy grid map by using it for autonomous mobile robot (AMR) navigation, ensuring successful navigation in both static and dynamic environments. This approach ensures a robust and dynamic 2D occupancy grid mapping system that enhances AMR path-planning and navigation capabilities.

![image](https://github.com/user-attachments/assets/801fe05c-7a30-43e2-9554-b4428f84572e)

## 4. Methodology

To create the solution, we utilized Gazebo simulation and ROS2 (Robot Operating System) for simulating and testing robots. Here's an overview of our approach:

1. Introduction to ROS-Gazebo:
    - We used ROS2 and Gazebo to simulate the robots and environment, providing a robust     
      platform for developing and testing our solution.

2. Setting up the ROS2 Environment:

    - Our development environment was set up on Ubuntu 20.04 with ROS2 Foxy. The setup involved
      installing the necessary packages and dependencies for ROS2.

3. Adding Overhead Cameras:
    - We added four overhead RGB cameras in a 2x2 pattern within the Gazebo simulation to     
      ensureoverlapping fields of view for comprehensive room coverage.

4. Setting up the Environment:
    - The simulated room in Gazebo contained static objects like chairs, tables, stools, and 
      boxes. This setup allowed us to mimic a real-world scenario for testing our solution.

5. Acquiring Data from Cameras:
    - ROS2 operates on a publisher-subscriber model. We set up nodes to stream images from the 
      cameras on specific topics.
    - A Python script was used to access these images. The script initiated nodes, created     
      subscriptions to the camera topics, and executed a callback function whenever an image 
      was published.
    - Important commands included sourcing the ROS2 setup script (source 
      /opt/ros/foxy/setup.bash) before running the Python script.

6. Generating the 2D Occupancy Grid Map:
    - We captured images from the overhead cameras and stitched them together to create a     
      unified view of the room.
    - Preprocessing techniques such as filtering, noise reduction, and edge detection were 
      applied to enhance the image quality.
    - Image processing algorithms generated a 2D occupancy grid map indicating occupied and 
      unoccupied spaces.
      
7. Dynamic Object Detection and Semantic Labeling:
    - Object detection algorithms recognized and labeled objects like "table" and "chair." The 
      occupancy grid map was dynamically updated to reflect changes in object positions in 
      real-time.

8. Evaluating the Generated Map:
    - We used Rviz, a ROS visualization tool, to evaluate the accuracy of the generated map.         Key point measurements were used as benchmarks.
    - A reference map generated with Cartographer was provided for comparison.
    - The evaluation involved running a command to visualize the map in Rviz, adjusting the 
      YAML file path as necessary.

## Validation
To validate our solution, we tested the map's accuracy and effectiveness using ROS and Gazebo simulations. Initially, we verified the map in a static environment where AMRs navigated the room using the generated map. We then introduced changes to the room, re-captured images, and tested the dynamically updated map. Semantic labels were verified, performance metrics were measured, and extensive field tests in the simulation environment ensured robustness. This comprehensive approach ensured the creation of a reliable and dynamic 2D occupancy grid map, enhancing AMR navigation capabilities.

## Advantages and Limitations of the Approach
### Advantages:

1. High Accuracy
    - By using four overhead RGB cameras in a 2x2 pattern, we achieved comprehensive coverage        of the room with overlapping fields of view, leading to high accuracy in generating the        2D occupancy grid map.
    - The integration of preprocessing techniques such as filtering, 
     noise reduction, and edge detection enhanced the quality of the stitched images, further       improving the map's accuracy.
    - Dynamic object detection and semantic labeling provided additional context and ensured         real-time updates to the occupancy grid map, maintaining accuracy even in dynamic 
      environments.

2. Scalability:
    - The use of ROS2 and Gazebo for simulation allows for easy scaling of the system to 
      larger environments or more complex scenarios.
    - Additional cameras can be added to cover larger areas, and the system can be extended to       include more advanced object detection algorithms to handle a wider variety of objects.

3. Real-time Processing:
    - The ROS2 publisher-subscriber model enables real-time image streaming and processing, 
      allowing the occupancy grid map to be dynamically updated as the environment changes.
    - This real-time capability is crucial for applications involving autonomous mobile robots       (AMRs) that require up-to-date information for navigation.
      
4. Visualization and Benchmarking:
    - The use of Rviz for visualization provides a clear and intuitive way to evaluate the     
      generated maps.
    - Benchmarking against a reference map generated with Cartographer allows for quantitative       assessment of the system's performance.
      
### Limitations:

1. Computational Complexity:
    - The image stitching, preprocessing, and object detection algorithms require significant 
      computational resources, which could be a limitation in resource-constrained  
      environments.
    - Real-time processing demands high-performance hardware to ensure low latency and quick  
      updates to the occupancy grid map.

2. Initial Setup and Calibration:
    - Setting up and calibrating the cameras to ensure proper overlap and coverage can be
      time-consuming and may require precise adjustments.
    - Misalignment or calibration errors can affect the accuracy of the stitched images and,   
      consequently, the occupancy grid map.

3. Environmental Dependence:
    - The system's performance is dependent on the quality of the captured images. Poor   
      lighting conditions, occlusions, or reflective surfaces can degrade image quality and  
      affect the accuracy of the occupancy grid map.
    - Static objects are easier to detect and map, while dynamic objects may introduce   
      additional complexity and require more sophisticated algorithms for accurate real-time   
      tracking.
      
4. Semantic Labeling Limitations:
    - While the system can label common objects like "table" and "chair," it may struggle with       less common or more complex objects without additional training and customization.
    - The accuracy of semantic labeling is dependent on the performance of the object     
      detection algorithms, which may require fine-tuning and validation.
      
5. Dependency on ROS2 and Gazebo:
    - The solution relies on the ROS2 and Gazebo platforms, which may have a steep learning   
      curve for new users and require familiarity with their tools and frameworks.
    - Any updates or changes to these platforms may impact the system's functionality and   
      require adaptations.


