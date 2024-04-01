# Barista Robot Description

This repository hosts the URDF and XACRO descriptions along with launch files for the barista robots, Rick and Morty. Designed for ROS2, it allows for the visualization in RViz and spawning of the robots within a Gazebo simulation environment. This setup is foundational for simulating the "Catch Me If You Can" game scenario where one robot chases another using the ROS2 framework.
A more comprehensive explanation of this project can be found [here](https://miguelsolissegura.com/project/barista-robots-p1).

## Getting Started

These instructions will guide you through setting up the project on your local machine for development, visualization, and testing purposes.

### Prerequisites

Ensure you have the following installed:
- ROS2 Foxy Fitzroy or newer
- Gazebo simulation environment
- git for version control

### Installation

1. Clone this repository into the `src` directory of your ROS2 workspace:
   ```bash
   cd ~/ros2_ws/src
   git clone https://github.com/MiguelSolisSegura/barista_robot_description.git
   ```
   
2. Navigate back to your ROS2 workspace and use `rosdep` to install any dependencies:
   ```bash
   cd ~/ros2_ws
   rosdep install --from-paths src --ignore-src -r -y
   ```

3. Build your ROS2 workspace:
   ```bash
   colcon build
   source install/setup.bash
   ```

## Running the Simulations

### Visualizing Robots in RViz

To visualize the robot models in RViz use:

```bash
ros2 launch barista_robot_description barista_two_robots.launch.py
```

This launch file also initializes both robots in Gazebo and configures them for the "Catch Me If You Can" game simulation.

### Testing Individual Robot Movement

You can test the movement and control of individual robots using the `teleop_twist_keyboard` package. For example, to control Morty:

```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args --remap cmd_vel:=/morty/cmd_vel
```

Similarly, replace `/morty` with `/rick` to control Rick.
