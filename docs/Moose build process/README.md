<div align="center">

# Moose UAV Build Project

**3D-Printed Fixed-Wing UAV Development for Trinavia**

*A foundational step toward autonomous precision agriculture systems*

</div>

---

## Overview

The **Moose** is a versatile 3D-printed fixed-wing UAV designed by [Flightory](https://flightory.com/product/moose/), featuring a classic layout with dual tractor motors and V-tail configuration. This project represents a critical milestone in developing the technical expertise and hands-on experience necessary for building Trinavia's custom drone systems for precision viticulture applications.

### Aircraft Specifications

| Parameter | Specification |
|-----------|-------------|
| **Wingspan** | 1600mm |
| **Length** | 1000mm |
| **All-Up Weight (AUW)** | 2000-4500g |
| **Optimal Cruise Speed** | 60-70 km/h |
| **Airfoil** | Selig S3021 |
| **Payload Compartment** | 140 × 118 × 90 mm (near CG) |
| **Construction** | Hybrid LW-PLA/ASA + PC/PETG with carbon fiber reinforcement |

---

## Project Significance for Trinavia

### Why This Build Matters

The Moose build serves as a comprehensive learning platform that directly supports Trinavia's mission to develop advanced UAV systems for precision agriculture. This project enables:

1. **Hardware Integration Expertise**: Hands-on experience with flight controllers, GPS modules, telemetry systems, and motor controllers—essential for integrating sensor payloads in viticulture applications.

2. **3D Modeling & Manufacturing**: Proficiency in CAD design, 3D printing optimization, and material selection—critical for custom sensor mounts, payload compartments, and aerodynamic modifications.

3. **Signal Processing & Control Systems**: Understanding of flight control algorithms, sensor fusion, and autonomous navigation—foundational for developing Trinavia's autonomous data collection workflows.

4. **System Integration**: Experience assembling complex electronic systems, wiring harnesses, and ensuring reliable operation—necessary for integrating lidar, RGB, spectral, and thermal sensors.

5. **Aerospace Engineering Fundamentals**: Practical understanding of aerodynamics, center of gravity management, and flight stability—enabling optimization of aircraft for specific agricultural mission profiles.

---

## Development Roadmap

### Phase 1: Project Airborne 🛫
**Status**: In Progress

- Complete final assembly and integration of all electronic components
- Conduct initial flight testing and calibration
- Validate flight stability and control surface responsiveness
- Achieve successful maiden flight with manual control

**Deliverable**: Operational RC aircraft capable of manual flight operations.

### Phase 2: Project Autonomous 🤖
**Status**: Planned

- Implement autonomous flight modes using ArduPilot/PX4 flight controller
- Develop automated waypoint navigation for systematic field coverage
- Integrate return-to-home (RTH) and failsafe systems
- Create automated mission planning workflows for vineyard surveying

**Deliverable**: Fully autonomous UAV capable of executing predefined flight missions without pilot intervention.

### Phase 3: Sensor Integration 📡
**Status**: Planned

Develop and integrate specialized sensor modules for agricultural data collection:

- **RGB Imaging**: High-resolution cameras for visual crop assessment and canopy analysis
- **Spectral Sensors**: Multispectral and hyperspectral imaging for NDVI, chlorophyll content, and plant health indices
- **Thermal Imaging**: Infrared cameras for water stress detection and irrigation optimization
- **LiDAR**: 3D terrain mapping and canopy structure analysis

**Deliverable**: Multi-sensor payload system with synchronized data collection capabilities.

### Phase 4: Software Development 💻
**Status**: Planned

- Develop Trinavia's data processing pipeline for sensor fusion
- Create automated analysis algorithms for disease detection and yield prediction
- Build mission planning software optimized for vineyard layouts
- Implement real-time telemetry and data visualization systems

**Deliverable**: Complete software ecosystem for processing agricultural UAV data.

### Phase 5: Custom UAV Development 🚁
**Status**: Future

- Design and manufacture custom UAV platforms optimized for viticulture applications
- Integrate all sensor systems into purpose-built aircraft
- Develop modular payload systems for different mission types
- Achieve regulatory compliance and certification for commercial operations

**Deliverable**: Production-ready Trinavia UAV systems for vineyard operations.

---

## Build Progress Gallery

<table>
<tr>
<td width="33%"><img src="Media/IMG_6561 2.PNG" alt="Build progress" width="200"/></td>
<td width="33%"><img src="Media/IMG_6562 2.PNG" alt="Spar integration" width="200"/></td>
<td width="33%"><img src="Media/IMG_6563 2.PNG" alt="Wing structure" width="200"/></td>
</tr>
<tr>
<td width="33%"><img src="Media/IMG_6708 2.JPG" alt="Complete airframe" width="200"/></td>
<td width="33%"><img src="Media/IMG_6709 2.JPG" alt="Control surfaces" width="200"/></td>
<td width="33%"><img src="Media/IMG_6710 2.JPG" alt="Pre-flight check" width="200"/></td>
</tr>
<tr>
<td width="33%"><img src="Media/IMG_6727 2.JPG" alt="Ready for flight" width="200"/></td>
<td width="33%"><img src="Media/IMG_6728 2.JPG" alt="Ground testing" width="200"/></td>
<td width="33%"></td>
</tr>
</table>

> **Note**: HEIC format images are not supported for display on GitHub. Currently showing only JPG and PNG images. To view all build progress photos including those in HEIC format, please download the Media folder. A video documentation file (`video_2025-09-22_11-41-07 2.MP4`) is also available showcasing the complete build process.

---

## Technical Components

### Electronic Systems

| Component | Model | Purpose |
|----------|-------|---------|
| **Flight Controller** | Speedybee F405 Wing | Autonomous flight control and mission execution |
| **GPS Module** | Matek M10Q | Position tracking and navigation |
| **Motors** | 2× 28XX (910KV) | Dual tractor propulsion system |
| **ESCs** | 2× 35-60A | Motor speed control and power management |
| **Servos** | 4× EMAX ES08 MAII | Control surface actuation (ailerons, V-tail) |
| **Receiver** | Matek R24-D ELRS | Radio control link |
| **FPV System** | Walksnail Avatar HD | First-person view and telemetry |
| **Battery** | 4S-6S Li-Ion/Li-Po | Power system |

### Structural Components

- **Main Spar**: 10×1000mm carbon fiber tube
- **Secondary Spar**: 8×1000mm carbon fiber tube
- **Wing Spars**: 2× 6×500mm carbon fiber tubes
- **V-Tail Spars**: 2× 8×285mm + 2× 6×130mm carbon fiber tubes
- **Hinges**: Carbon fiber tubes for control surface articulation
- **Fasteners**: Snap-lock system for tool-free assembly

### Materials

- **Primary Structure**: LW-PLA/LW-ASA (lightweight expanded foam)
- **High-Stress Components**: PC/PETG (polycarbonate/polyethylene terephthalate)
- **Flexible Components**: TPU (thermoplastic polyurethane) where needed
- **Reinforcement**: Carbon fiber tubes and composite materials

---

## Skills & Expertise Developed

### Technical Competencies

✅ **3D Modeling & CAD Design**
- Parametric modeling for custom modifications
- STEP file manipulation and component integration
- Design optimization for 3D printing constraints

✅ **Additive Manufacturing**
- Multi-material printing workflows
- Print parameter optimization for strength-to-weight ratio
- Post-processing and finishing techniques

✅ **Electronics Integration**
- Flight controller configuration and tuning
- Sensor calibration and data fusion
- Power distribution and wiring harness design
- Electromagnetic interference mitigation

✅ **Aerospace Engineering**
- Center of gravity calculation and balancing
- Control surface design and actuation
- Aerodynamic optimization for mission profiles
- Structural analysis and reinforcement strategies

✅ **Software & Firmware**
- ArduPilot/PX4 configuration
- Mission planning and waypoint navigation
- Telemetry data processing
- Autonomous flight mode development

✅ **Testing & Validation**
- Ground testing protocols
- Flight test procedures
- System integration verification
- Safety and reliability assessment

---

## Integration with Trinavia Platform

### Direct Applications

1. **Vineyard Mapping**: The Moose's payload compartment is positioned near the center of gravity, making it ideal for mounting mapping cameras and sensors for systematic vineyard surveys.

2. **Autonomous Missions**: The modular design allows for easy sensor swapping, enabling different mission profiles (health monitoring, yield estimation, irrigation assessment) using the same airframe.

3. **Data Collection Workflows**: Experience gained from autonomous flight operations directly informs the development of Trinavia's automated data collection systems.

4. **Sensor Fusion**: Understanding flight dynamics and sensor mounting positions enables optimal placement of multi-sensor payloads for synchronized data acquisition.

5. **Custom Platform Development**: The knowledge gained from modifying and optimizing the Moose platform will inform the design of Trinavia's purpose-built agricultural UAV systems.

---

## Future Enhancements

### Planned Modifications

- **Extended Range**: Battery optimization for longer flight times suitable for large vineyard surveys
- **Payload Optimization**: Custom sensor mounts designed for agricultural imaging systems
- **Weather Resistance**: Sealing and protection for operation in agricultural environments
- **Modular Nose Sections**: Custom nose designs for different sensor configurations
- **Telemetry Integration**: Real-time data streaming to Trinavia's ground control station

---

## Build Resources

- **Design Source**: [Flightory Moose](https://flightory.com/product/moose/)
- **Documentation**: Assembly manual and wiring diagrams included with purchase
- **Community**: Flightory Discord and support channels
- **Software**: ArduPilot Mission Planner, QGroundControl, Betaflight Configurator

---

## Safety & Compliance

- All flight operations conducted in accordance with local UAV regulations
- Pre-flight checklists and safety protocols established
- Failsafe systems configured for safe operation
- Insurance and certification considerations for commercial agricultural applications

---

## Project Status

**Current Phase**: Project Airborne - Final Assembly & Integration  
**Next Milestone**: Maiden Flight  
**Timeline**: Q1 2025

---

## Contact & Collaboration

For questions about this build, technical discussions about UAV development for precision agriculture, or collaboration opportunities, please reach out through the [main Trinavia repository](../../README.md).

---

## Acknowledgments

- **Flightory**: Design and engineering of the Moose platform
- **Open Source Community**: ArduPilot, PX4, and related flight control software
- **3D Printing Community**: Material optimization and printing techniques

---

## License

This build documentation is part of the Trinavia project. The Moose design is licensed for personal use under [Flightory's License Agreement](https://flightory.com/product/moose/).

---

<div align="center">

**Part of the [Trinavia](/) Ecosystem**

*Advancing precision agriculture through autonomous UAV technology*

</div>

