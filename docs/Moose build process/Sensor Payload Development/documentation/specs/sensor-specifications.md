# Sensor Specifications

Detailed specifications for each sensor in the Trinavia payload system.

## RGB Camera

### Requirements
- **Resolution**: 12-20 MP minimum
- **Shutter Type**: Global shutter (critical for moving UAV)
- **Interface**: USB3 or Ethernet (PoE preferred)
- **Trigger**: Hardware trigger line support
- **Geotagging**: EXIF metadata with GNSS coordinates

### Recommended Models
- Industrial global-shutter camera modules with Sony IMX sensors
- Compact photogrammetry cameras with mechanical trigger

### Use Cases
- Grape cluster detection and counting
- Visual crop assessment
- Canopy analysis
- High-resolution mapping

---

## Multispectral Sensor

### MicaSense RedEdge-MX

**Specifications**:
- **Weight**: 230g
- **Power**: 3-5W
- **Bands**: 5 narrow spectral bands
  - Blue (475nm)
  - Green (560nm)
  - Red (668nm)
  - Red Edge (717nm)
  - Near Infrared (842nm)
- **Resolution**: 1.2 MP per band
- **Capture Rate**: Up to 1 capture per second
- **Interface**: USB-C, GPS synchronization

**Indices Generated**:
- NDVI (Normalized Difference Vegetation Index)
- NDRE (Normalized Difference Red Edge)
- GNDVI (Green NDVI)
- Custom disease detection indices

**Use Cases**:
- Plant health assessment
- Disease detection (mildew, leaf spot)
- Chlorophyll content estimation
- Vegetation stress monitoring

**Reference**: [MicaSense RedEdge-MX](https://measur.ca/products/micasense-rededge-mx)

---

## Thermal Camera

### FLIR Boson 320

**Specifications**:
- **Resolution**: 320×256 pixels
- **Weight**: ~50-100g (module only)
- **Power**: 1-2W
- **Temperature Range**: -10°C to 400°C
- **Radiometric**: Yes (temperature measurement per pixel)
- **Frame Rate**: 60 Hz
- **Interface**: USB3, SPI

**Alternative: FLIR Boson 640**
- **Resolution**: 640×512 pixels
- Higher resolution for detailed thermal mapping
- Slightly higher weight and power consumption

**Use Cases**:
- Water stress detection (canopy temperature)
- Irrigation effectiveness assessment
- Thermal anomaly detection (disease, equipment issues)
- Microclimate analysis

**Reference**: [FLIR Boson Family](https://oem.flir.com/boson-family/)

---

## LiDAR

### Livox Mid-40

**Specifications**:
- **Weight**: 700g
- **Power**: 8-12W
- **Range**: 260m @ 80% reflectivity
- **Field of View**: 38.4° circular
- **Point Rate**: 100,000 points/second
- **Interface**: Ethernet, USB-C
- **Accuracy**: ±2cm @ 100m

**Use Cases**:
- 3D terrain mapping
- Canopy height modeling (CHM)
- Vineyard row geometry analysis
- Structural analysis of vine architecture
- Ground elevation mapping

**Alternative: Velodyne Puck (VLP-16)**
- 360° scanning capability
- Higher weight (~830g)
- Good for comprehensive 3D mapping

**Reference**: [Livox Mid-40 Specs](https://www.livoxtech.com/mid-40-and-mid-100/specs)

---

## GNSS/RTK Module

### u-blox ZED-F9P

**Specifications**:
- **Weight**: ~20g
- **Power**: ~1W
- **Accuracy**: 
  - Standalone: 1.5m
  - RTK: 1cm + 1ppm
- **Update Rate**: Up to 20 Hz
- **PPS Output**: Yes (critical for time synchronization)
- **Multi-band**: GPS, GLONASS, Galileo, BeiDou
- **Interface**: UART, USB, I2C, SPI

**Use Cases**:
- Centimeter-level geotagging of all sensor data
- Precise waypoint navigation
- Time reference (PPS) for sensor synchronization
- Mapping and photogrammetry accuracy

**Reference**: [u-blox ZED-F9P](https://www.u-blox.com/en/product/zed-f9p-module)

---

## IMU (Inertial Measurement Unit)

### VectorNav VN-100

**Specifications**:
- **Weight**: ~30g
- **Power**: ~0.5W
- **Sensors**: 3-axis accelerometer, gyroscope, magnetometer
- **Accuracy**: 
  - Roll/Pitch: ±0.5°
  - Yaw: ±1° (with magnetometer)
- **Update Rate**: Up to 800 Hz
- **Interface**: UART, SPI, CAN

**Alternative: ADIS Series**
- Lower cost options available
- Similar performance characteristics

**Use Cases**:
- Sensor fusion for accurate georeferencing
- Camera/LiDAR orientation tracking
- Flight dynamics analysis
- Vibration compensation

---

## Mission Computer

### NVIDIA Jetson Xavier NX

**Specifications**:
- **Weight**: ~100-150g (with carrier board)
- **Power**: 10-25W (depending on workload)
- **CPU**: 6-core NVIDIA Carmel ARMv8.2
- **GPU**: 384-core NVIDIA Volta
- **Memory**: 8GB 128-bit LPDDR4x
- **Storage**: NVMe SSD support
- **Interfaces**: USB3, Ethernet, GPIO, I2C, SPI, UART

**Capabilities**:
- Real-time ML inference
- On-device image processing
- Sensor fusion algorithms
- ROS2 support

**Alternative: Jetson Orin Nano**
- More recent, improved performance
- Similar form factor and power consumption

**Alternative: Raspberry Pi CM4**
- Lower power (5-10W)
- Lighter weight (~50g)
- Suitable for basic control and logging
- Limited ML inference capability

**Reference**: [NVIDIA Jetson Xavier NX](https://developer.nvidia.com/embedded/jetson-xavier-nx)

---

## Storage

### NVMe SSD

**Requirements**:
- **Capacity**: 1-2TB (for continuous data collection)
- **Interface**: NVMe M.2
- **Speed**: PCIe 3.0 or 4.0
- **Weight**: ~50g
- **Power**: 2-3W

**Use Cases**:
- High-speed recording of camera streams
- LiDAR point cloud storage
- Temporary data buffer before offload
- Onboard processing workspace

---

## Power Requirements Summary

| Component | Typical Power | Peak Power |
|-----------|---------------|------------|
| RGB Camera | 2-5W | 5W |
| RedEdge-MX | 3-5W | 5W |
| FLIR Boson 320 | 1-2W | 2W |
| Livox Mid-40 | 8-12W | 12W |
| ZED-F9P | 1W | 1W |
| IMU | 0.5W | 0.5W |
| Jetson Xavier NX | 10-25W | 25W |
| NVMe SSD | 2-3W | 3W |
| **Minimal Config** | **~20-35W** | **~35W** |
| **Full Config** | **~40-60W** | **~60W** |

---

## Weight Summary

| Component | Weight |
|-----------|--------|
| RGB Camera | 100-200g |
| RedEdge-MX | 230g |
| FLIR Boson 320 | 50-100g |
| Livox Mid-40 | 700g |
| ZED-F9P | 20g |
| IMU | 30g |
| Jetson Xavier NX | 100-150g |
| NVMe SSD | 50g |
| Power Distribution | 30g |
| Mounting Hardware | 50-100g |
| **Minimal Config** | **~500-600g** |
| **Full Config** | **~1200-1500g** |

