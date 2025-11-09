<div align="center">

# Trinavia Custom Sensor Payload

**Multi-Sensor Agricultural Imaging System for Moose UAV**

*Integrated RGB, Multispectral, Thermal, and LiDAR payload for precision viticulture*

</div>

---

## Overview

This project develops a custom multi-sensor payload system designed to integrate with the Moose fixed-wing UAV platform. The payload combines RGB imaging, multispectral sensors, thermal cameras, and LiDAR to provide comprehensive vineyard monitoring capabilities including disease detection, water stress assessment, yield estimation, and canopy structure analysis.

### Design Philosophy

The sensor payload is designed around a **ball turret/gimbal form factor** (based on [Thingiverse mini gimbal](https://www.thingiverse.com/thing:592330)) that provides two-axis pointing capability while maintaining compact size and weight suitable for UAV integration. The system emphasizes:

- **SWaP Optimization**: Size, Weight, and Power constraints for UAV deployment
- **Synchronized Data Collection**: GNSS PPS-based time synchronization across all sensors
- **Modular Architecture**: Hot-swappable sensor modules via UAVCAN/CAN bus
- **Edge Processing**: Onboard compute for real-time analysis and data reduction
- **Agricultural Focus**: Sensors and processing optimized for viticulture applications

---

## System Architecture

### Sensor Suite

| Sensor Type | Recommended Model | Purpose | Weight | Power |
|------------|------------------|---------|--------|-------|
| **RGB Camera** | Industrial global-shutter (12-20 MP Sony IMX) | Grape cluster detection, counting, visual assessment | ~100-200g | 2-5W |
| **Multispectral** | MicaSense RedEdge-MX | NDVI, disease indices, plant health | ~230g | 3-5W |
| **Thermal** | FLIR Boson 320/640 | Water stress, irrigation effectiveness, thermal anomalies | ~50-100g | 1-2W |
| **LiDAR** | Livox Mid-40 | 3D structure, canopy height, row geometry | ~700g | 8-12W |
| **GNSS/RTK** | u-blox ZED-F9P | Centimeter-level geotagging, time reference | ~20g | 1W |
| **IMU** | VectorNav VN-100 or ADIS | Orientation for sensor fusion | ~30g | 0.5W |

### Computing & Communication

| Component | Recommended Model | Purpose | Weight | Power |
|-----------|------------------|---------|--------|-------|
| **Mission Computer** | NVIDIA Jetson Xavier NX / Orin Nano | Edge processing, ML inference | ~100-150g | 10-25W |
| **Alternative** | Raspberry Pi CM4 | Lightweight control, data logging | ~50g | 5-10W |
| **Storage** | NVMe SSD (1-2TB) | High-speed data recording | ~50g | 2-3W |
| **Telemetry** | SiK Radio / 4G LTE Modem | Long-range data link | ~30-50g | 2-5W |

### Total Payload Estimate

- **Minimal Configuration** (RedEdge-MX + FLIR Boson + ZED-F9P + Jetson): ~500-600g, ~20-35W
- **Full Configuration** (All sensors + LiDAR): ~1200-1500g, ~40-60W

---

## Sensor Bus Architecture

### Physical Bus Design

1. **Power Distribution**
   - Regulated 5V rail for cameras and sensors
   - 12V rail for LiDAR and mission computer
   - PoE support for compatible camera modules
   - Power budget: ~50-60W total (with headroom)

2. **Data Communication**
   - **UAVCAN v1 / CAN bus**: Sensor control, telemetry, actuator commands
   - **USB3 / Ethernet**: High-speed camera and LiDAR data streams
   - **PoE**: Unified power + data for cameras where supported
   - **GPIO / Hardware Triggers**: GNSS PPS synchronization lines

3. **Time Synchronization**
   - GNSS PPS (Pulse-Per-Second) from u-blox ZED-F9P
   - NTP/PPS discipline for system clock
   - Hardware trigger lines for frame-accurate camera capture
   - Synchronized timestamps in all data streams

### Data Flow

```
Sensors → MCU Gateway (CAN/UAVCAN) → Mission Computer (Jetson/CM4)
                                              ↓
                                    Local NVMe SSD (Raw Data)
                                              ↓
                                    Optional: LTE/RTSP Streaming
```

### Protocols & Software Stack

- **Flight Control**: PX4/Cube flight controller
- **Mission Control**: MAVLink between flight controller and mission computer
- **Sensor Fusion**: ROS2 on mission computer
- **Camera Drivers**: ROS2 camera nodes with hardware trigger support
- **LiDAR Processing**: ROS2 LiDAR nodes
- **Data Storage**: EXIF metadata (UTC, lat/lon/alt, yaw/pitch/roll), LAS/LAZ for LiDAR, ROS bags

---

## Mechanical Integration

### Ball Turret Mounting

The payload integrates with a modified [Thingiverse mini gimbal](https://www.thingiverse.com/thing:592330) ball turret design:

- **Payload Capacity**: ~300-400g per sensor module (may require redesign for heavier components)
- **Degrees of Freedom**: Continuous yaw + limited tilt (±90° typical)
- **Cable Management**: Slip-ring or UAVCAN over rotating interface for 360° yaw
- **Vibration Isolation**: Soft mounts for cameras, foam isolation for thermal sensors, rigid mounting for LiDAR

### Mounting Strategy

1. **Heavy Components** (LiDAR, RTK base): Mount near vehicle centerline, not on gimbal
2. **Gimbal Payload**: RGB + Multispectral + Thermal cameras (aimed scans)
3. **Adapter Plate**: Custom 3D-printed adapter (PETG/Nylon/CF-reinforced) bolting to ball turret servo mounts

### Weight & CG Considerations

- Early payload weight estimates required for flight controller parameter updates
- Recalculate UAV center of gravity with full payload
- May require ball turret scaling/reinforcement for full sensor suite

---

## Software & Analytics Pipeline

### In-Flight Processing

- Lightweight ML models on Jetson for preliminary detection:
  - Vine stress hot spots
  - Quick grape cluster count estimates
  - Real-time anomaly detection
- Full-resolution data saved to onboard SSD

### Post-Flight Processing

1. **Photogrammetry**
   - Agisoft Metashape / OpenDroneMap
   - RGB orthomosaic and 3D models
   - Global shutter + accurate GNSS reduces tie-point errors

2. **Multispectral Analysis**
   - MicaSense workflow or open tools (Pix4Dfields, QGIS)
   - Generate NDVI, NDRE, and other vegetation indices
   - Disease detection algorithms

3. **Thermal Analysis**
   - Radiometric thermal mosaicking
   - Canopy temperature anomaly mapping
   - Water stress assessment

4. **LiDAR Processing**
   - Point cloud classification (ground, canopy, vine trunks)
   - Canopy Height Model (CHM) generation
   - Row geometry analysis

5. **Machine Learning**
   - Transfer learning on CNN for cluster detection
   - Combine detections with geotags for per-vine yield estimates
   - Multi-sensor fusion for improved mildew detection precision

### Data Fusion

Combine NDVI + thermal + LiDAR CHM + RGB detection for:
- Enhanced mildew detection precision
- Robust water stress estimation
- Comprehensive yield prediction models

---

## Development Roadmap

### Phase 1: Minimal Payload (High-Impact Start) 🔄

**Priority Components**:
1. MicaSense RedEdge-MX (multispectral)
2. FLIR Boson 320 (radiometric thermal)
3. u-blox ZED-F9P (RTK GNSS)
4. Jetson Xavier NX (edge compute)
5. NVMe SSD (storage)

**Deliverables**:
- Functional sensor integration
- Synchronized data collection
- Basic processing pipeline
- Initial vineyard test flights

### Phase 2: RGB & IMU Integration 📋

- High-resolution global-shutter RGB camera
- Machine-grade IMU (VectorNav VN-100 or ADIS)
- Hardware trigger synchronization
- Photogrammetry workflow

### Phase 3: LiDAR Integration 📋

- Livox Mid-40 integration
- 3D point cloud processing
- Canopy height modeling
- Structural analysis algorithms

### Phase 4: Advanced Analytics 📋

- Real-time ML inference on Jetson
- Multi-sensor fusion algorithms
- Automated disease detection
- Yield prediction models

### Phase 5: Production Optimization 📋

- Custom PCB design (power distribution + CAN gateway)
- Reinforced mechanical mounts
- Production-grade software stack
- Regulatory compliance

---

## Integration Checklist

### Hardware Integration

- [ ] Confirm payload envelope (weight, dimensions) for ball turret
- [ ] Scale/reinforce printed model if needed for full sensor suite
- [ ] Design and print custom adapter plate (PETG/Nylon/CF)
- [ ] Wire CAN bus + power distribution board
- [ ] Integrate GNSS with PPS wiring to mission computer
- [ ] Implement hardware trigger lines (camera ↔ GNSS PPS)
- [ ] Mount sensors with appropriate vibration isolation
- [ ] Verify weight and CG calculations

### Software Integration

- [ ] Flash ROS2 and MAVROS on mission computer
- [ ] Integrate with PX4 on Moose flight controller
- [ ] Configure camera drivers with hardware trigger support
- [ ] Set up LiDAR ROS2 nodes
- [ ] Implement time synchronization (GNSS PPS → NTP)
- [ ] Develop data logging pipeline (EXIF, LAS, ROS bags)
- [ ] Create ground control station interface

### Testing & Validation

- [ ] Ground tests: sensor timestamps, thermal snapshots
- [ ] LiDAR scan pattern validation
- [ ] Image overlap tests for photogrammetry
- [ ] Power consumption measurements
- [ ] Vibration analysis
- [ ] Small mapping missions
- [ ] Data offload and processing pipeline validation

---

## Bill of Materials (BOM)

### Minimal Payload Configuration

| Component | Model | Approx. Cost | Weight | Power | Justification |
|-----------|-------|--------------|--------|-------|---------------|
| Multispectral | MicaSense RedEdge-MX | $5,500 | 230g | 3-5W | Industry standard for crop indices |
| Thermal | FLIR Boson 320 | $2,000-3,000 | 50-100g | 1-2W | Radiometric, good sensitivity |
| GNSS/RTK | u-blox ZED-F9P | $200-300 | 20g | 1W | Centimeter accuracy, PPS output |
| Mission Computer | Jetson Xavier NX | $500-700 | 100-150g | 10-25W | Edge ML processing capability |
| Storage | NVMe SSD 1TB | $100-150 | 50g | 2-3W | High-speed data recording |
| Power Distribution | Custom PCB | $50-100 | 30g | - | Regulated rails, CAN gateway |
| **Total** | | **~$8,500-10,000** | **~500-600g** | **~20-35W** | |

### Full Configuration (Additions)

| Component | Model | Approx. Cost | Weight | Power | Justification |
|-----------|-------|--------------|--------|-------|---------------|
| RGB Camera | Industrial IMX module | $500-1,000 | 100-200g | 2-5W | Global shutter, high-res |
| LiDAR | Livox Mid-40 | $1,500-2,000 | 700g | 8-12W | 3D structure mapping |
| IMU | VectorNav VN-100 | $500-800 | 30g | 0.5W | High-quality orientation |
| **Additional Total** | | **~$2,500-3,800** | **~830-930g** | **~11-18W** | |

---

## Resources & References

### Product Documentation

- [MicaSense RedEdge-MX](https://measur.ca/products/micasense-rededge-mx)
- [FLIR Boson Thermal Modules](https://oem.flir.com/boson-family/)
- [u-blox ZED-F9P RTK GNSS](https://www.u-blox.com/en/product/zed-f9p-module)
- [Livox Mid-40 LiDAR](https://www.livoxtech.com/mid-40-and-mid-100/specs)
- [NVIDIA Jetson Xavier NX](https://developer.nvidia.com/embedded/jetson-xavier-nx)
- [Raspberry Pi CM4](https://datasheets.raspberrypi.com/cm4/cm4-product-brief.pdf)

### Design References

- [Thingiverse Mini Gimbal](https://www.thingiverse.com/thing:592330) - Ball turret base design
- [UAVCAN Specification](https://uavcan.org/) - Sensor bus protocol
- [PX4 Flight Controller](https://px4.io/) - Autonomous flight system
- [ROS2](https://docs.ros.org/en/humble/) - Robot operating system for sensor fusion

### Software Tools

- **Photogrammetry**: Agisoft Metashape, OpenDroneMap
- **Multispectral**: Pix4Dfields, QGIS
- **LiDAR**: CloudCompare, PDAL
- **ML/Analytics**: PyTorch, TensorFlow, scikit-learn

---

## Next Steps

### Immediate Actions

1. **Detailed BOM**: Complete parts list with weights, power draw, and sourcing
2. **Wiring Diagram**: Power distribution + CAN gateway + camera trigger lines
3. **3D Adapter Design**: STL/parametric model for ball turret sensor mounting
4. **PCB Design**: Power distribution board with CAN gateway

### Development Priorities

1. Start with minimal payload (RedEdge-MX + Boson + ZED-F9P + Jetson)
2. Validate sensor synchronization and data collection
3. Develop basic processing pipeline
4. Conduct initial vineyard test flights
5. Iterate based on field data and requirements

---

## Project Status

**Current Phase**: Design & Planning  
**Next Milestone**: Minimal Payload Integration  
**Timeline**: Q1-Q2 2025

---

## Contact & Collaboration

For questions about sensor payload development, technical discussions, or collaboration opportunities, please refer to the [main Trinavia repository](../../README.md).

---

## License

This sensor payload development is part of the Trinavia project. See [LICENSE](../../../LICENSE) for usage restrictions and collaboration guidelines.

---

<div align="center">

**Part of the [Trinavia](../../../README.md) Ecosystem**

*Advancing precision agriculture through autonomous UAV technology*

</div>

