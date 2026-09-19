
#  Robo: Multi-Robot System with RL, 3D Mapping & LLM Integration

A modular robotics project designed for ROS 2 Humble, integrating multi-robot coordination, real-time 3D mapping, task allocation using reinforcement learning, and natural language processing via OpenAI’s LLMs.

---

##  Project Structure

```
/robo  
└── src  
    └── ros2_learners  
        ├── llm                      # LLM interface for natural language processing  
        ├── log                      # Log storage  
        ├── logs                     # Real-time logging (object & bot positions, task assignment)  
        ├── my_robot_controller      # Swarm RL implementation (TD3, etc.)  
        ├── navigation_tb3           # Navigation and control packages  
        ├── nodes                    # General ROS 2 nodes  
        ├── pc                       # Real-time logging utilities  
        ├── point_cloud_perception   # Real-time 3D mapping with RTAB-Map  
        ├── resources                # Resource files  
        ├── robot_math               # Utility math functions  
        ├── TaskAllocation           # DQN-based task assignment logic  
        ├── transforms               # TF2 frame utilities  
        └── turtlebot3_gazebo        # Robot models, world files, launch files  
```

---

## 🛠️ System Requirements

- **OS**: Ubuntu 22.04  
- **ROS 2**: Humble Hawksbill  
- **Python**: 3.10.12  

---

## 🔗 Installation Links

- [ROS 2 Humble Installation](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)  
- [Gazebo Classic Installation](https://classic.gazebosim.org/tutorials?tut=install_ubuntu)

---

## 📦 Software Dependencies

- ROS 2 Gazebo Packages  
- Xacro  
- Gazebo Classic  
- PyTorch 2.3.1  
- TensorFlow 2.15.0  
- Numpy 1.21.5  
- Matplotlib 3.5.1  
- TensorBoard  
- OpenAI 0.28  

---

## 🧰 Installation Instructions

### 1. Source ROS 2
```bash
source /opt/ros/humble/setup.bash
```

### 2. Check Ubuntu Version
```bash
lsb_release -a
```

### 3. Install ROS-Gazebo Packages
```bash
sudo apt install ros-humble-gazebo-ros-pkgs ros-humble-gazebo-ros2-control
```

### 4. Install Xacro
```bash
sudo apt install ros-humble-xacro
```

### 5. Navigate to Project Directory
```bash
cd robo
```

### 6. Install ROS Dependencies
```bash
rosdep init
rosdep update
rosdep install -i --from-path src --rosdistro humble -y
```

### 7. Build the Workspace
```bash
colcon build
```

---

## 🌐 Environment Setup

### Source the Workspace
```bash
source install/setup.bash
```

### Set TurtleBot3 Model
```bash
export TURTLEBOT3_MODEL=waffle
```

---

## 🚀 Launch Instructions

### Start Gazebo World
```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

### Visualize 3D Depth Mapping
```bash
cd robo
source install/setup.bash
# Replace {N} with bot number, e.g., 5
ros2 launch point_cloud_perception 3d_depth_mapping_rtab{N}.launch.py
```

---

## 🧠 LLM + OpenAI Setup

1. Create an API key from [OpenAI API Keys](https://platform.openai.com/settings/organization/api-keys)  
2. Create a file named `api_key.txt` inside the `llm/` folder  
3. Paste the secret API key into the file  

### Install OpenAI Python Package
```bash
pip install openai==0.28
```

---

## 🧪 Running Modules

### Task Allocation
```bash
cd ~/robo/src/ros2_learners/TaskAllocation/
python3 script.py
```

### Maintain Bot Position
```bash
python3 TaskAllocationNode.py
```

### Object Position Logging
```bash
cd ~/robo/src/ros2_learners/pc/pc/
python3 list1.py
```

### Task Object Logging
```bash
python3 match.py
```

---

## 🧠 TD3 Training & Testing

### Test Model
```bash
cd ~/robo/src/ros2_learners/my_robot_controller/my_robot_controller/td3/
python3 test_copy.py
```

### Train Model
```bash
python3 train.py
```

---

## 💬 LLM Execution

```bash
cd ~/robo/src/ros2_learners/llm
python3 scripts/run_llm.py
```
