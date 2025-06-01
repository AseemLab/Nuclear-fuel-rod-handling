# Nuclear Fuel Rod Relocation using 6 DOF Robotic Arms

**Author:** Aseem Saxena  
**Department:** Electrical and Electronics Engineering  
**Institution:** University of Bath

## Overview

This project explores the use of a 6 DOF (Degree of Freedom) industrial robotic arm system to safely relocate spent nuclear fuel rods through thick concrete walls in nuclear facilities. The system provides enhanced safety measures and resource efficiency for handling highly radioactive and fragile fuel rods.

## Executive Summary

Nuclear energy accounts for approximately 10% of global electricity production (2545 TWh) using 436 operational power reactors worldwide. The handling of spent nuclear fuel rods is a critical and dangerous operation that requires high precision and safety measures. This project demonstrates a robotic solution using multiple coordinated robotic arms to transfer fuel rods between different processing stages within nuclear facilities.

## System Architecture

The system consists of four Niryo-One robotic arms working in sequence:

1. **Robot 1**: Picks up the fuel rod and presents it through an aperture in the first barrier
2. **Robot 2**: Collects the rod and transfers it through the second aperture
3. **Robot 3**: Continues the transfer through the third aperture
4. **Robot 4**: Places the rod in its final position or onto a conveyor system

![System Layout](Fig1_Robot_Layout.png)
*Figure 1: Four Niryo-One robots positioned with Perspex screens representing concrete barriers*

## Features

- **Multi-Robot Coordination**: Four 6-DOF robotic arms working in synchronized sequence
- **Safety Barriers**: Perspex screens with circular apertures simulating concrete walls
- **Automated Transport**: Integrated conveyor belt system for final rod transportation
- **Digital Twin**: Complete simulation environment for testing and validation
- **Inverse Kinematics**: Advanced motion planning for precise positioning

## Simulation Environment

The project uses **CoppeliaSim Edu version 4.6.0** for digital twin simulation.

![Simulation Scene](Fig2_Simulation_Scene.png)
*Figure 2: Complete simulation environment with robots, barriers, and transport system*

### System Requirements

- **Operating System**: Windows
- **Processor**: Intel i7 11th generation or equivalent
- **RAM**: 16 GB minimum
- **Graphics**: No dedicated GPU required
- **Software**: CoppeliaSim Edu 4.6.0

## Technical Implementation

### Programming Language
- **Primary**: Lua scripting
- **Alternative**: Python (supported but not used in this implementation)

### Key Components

1. **Inverse Kinematics (IK)**: Back-propagation algorithm for joint movement calculation
2. **Proximity Sensors**: For object detection and positioning
3. **Signal Communication**: Inter-robot coordination system
4. **Dynamic Properties**: Physics engine configuration for realistic simulation

### Simulation Setup

![CoppeliaSim Interface](Fig3_Interface.png)
*Figure 3: CoppeliaSim Edu development interface*

The simulation includes:
- Four Niryo-One robotic arms
- Three Perspex barrier screens with apertures
- Conveyor belt transport system
- Rod-holding trays
- Radiation-absorbing carbon foam receptacle
- Industrial-grade support platforms

## Installation and Setup

1. **Install CoppeliaSim Edu 4.6.0** on a Windows machine
2. **Load the project file** containing all scene elements
3. **Configure robot positions** using the object shift and rotate tools
4. **Set up Inverse Kinematics** for each robotic arm
5. **Add positioning dummies** for path planning
6. **Configure dynamic properties** for realistic physics simulation

## Usage Instructions

### Scene Configuration

1. Add Niryo-One robots from the model browser
2. Position Perspex screens with appropriate aperture locations
3. Configure conveyor belts and support structures
4. Set up proximity sensors and counters

### Programming the Robots

Each robot requires:
- Position variables linked using `sim.getObject` function
- Sequential movement code in `sysCall_thread()` function
- Proper frame orientation for gripper positioning
- Signal coordination between robots

### Key Functions

```lua
sim.getObjectPosition()     -- Get object position
sim.setObjectPosition()     -- Set target position
sim.getObjectOrientation()  -- Get object orientation
sim.setObjectOrientation()  -- Set target orientation
sim.setInt32Signal()        -- Close gripper
sim.clearInt32Signal()      -- Open gripper
sim.waitForSignal()         -- Wait for coordination signal
```

## Path Planning

![Final Scene](Fig4_Final_Scene.png)
*Figure 4: Complete simulation scene with positioned elements*

The system uses multiple waypoints to ensure smooth robot movement and avoid collisions. Path planning addresses:
- Jittering elimination during arm movement
- Collision avoidance with scene objects
- Uncertainty in IK-calculated paths

## Results and Performance

The simulation successfully demonstrates:
- ✅ Coordinated multi-robot operation
- ✅ Safe fuel rod transfer through barriers
- ✅ Automated transport to final destination
- ✅ Collision-free movement paths
- ✅ Realistic physics simulation

### Key Achievements

- Successful implementation of 6-DOF robotic arm coordination
- Effective use of Inverse Kinematics for precise positioning
- Robust inter-robot communication system
- Scalable design for industrial applications

## Challenges and Solutions

### Identified Issues
- **Jittering**: Robot arm instability during movement
- **Path Uncertainty**: Unpredictable IK-calculated paths
- **Collision Risk**: Potential interference with scene objects

### Implemented Solutions
- Multiple positioning waypoints for smooth transitions
- Careful timing delays for IK calculations
- Frame-oriented positioning for consistent gripper alignment

## Future Enhancements

- **Advanced Path Planning**: Implementation of sophisticated trajectory planning algorithms
- **Enhanced Sensors**: Additional proximity and force sensors for improved safety
- **Fluid Motion**: Smoother robotic arm movements with reduced delays
- **Multi-Manufacturer Support**: Code adaptability for different robot brands

## Safety Considerations

This system addresses critical nuclear facility requirements:
- Remote handling of radioactive materials
- Precision movement through confined spaces
- Fail-safe operation protocols
- Minimal human exposure to radiation

## File Structure

```
nuclear-fuel-rod-handling/
├── simulation/
│   ├── main_scene.ttt
│   ├── robot_scripts/
│   └── ik_configurations/
├── documentation/
│   ├── technical_report.pdf
│   └── user_manual.md
└── README.md
```

## Contributing

This project was developed as part of academic research at the University of Bath. For contributions or questions, please refer to the complete technical documentation.

## References

1. [Niryo One Mechanical Specifications](https://www.gotronic.fr/pj2-36480-mechanical-specifications-11-09-2018-2063.pdf)
2. [Nuclear Power Today | World Nuclear Association](https://world-nuclear.org/information-library/current-and-future-generation/nuclear-power-in-the-world-today.aspx)

## License

This project is developed for educational and research purposes. Please ensure compliance with nuclear safety regulations and institutional guidelines when implementing similar systems.

---

**Note**: This simulation represents a proof-of-concept for nuclear fuel rod handling. Actual implementation in nuclear facilities requires extensive safety validation and regulatory approval.
