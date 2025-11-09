# Bill of Materials (BOM)

Complete parts list for the Trinavia sensor payload system.

## Minimal Payload Configuration

*High-impact starting point for vineyard data collection*

| # | Component | Model | Qty | Unit Cost | Total Cost | Weight (g) | Power (W) | Supplier | Status | Notes |
|---|-----------|-------|-----|-----------|------------|------------|----------|----------|--------|-------|
| 1 | Multispectral Sensor | MicaSense RedEdge-MX | 1 | $5,500 | $5,500 | 230 | 3-5 | MicaSense | 📋 Planned | Industry standard for crop indices |
| 2 | Thermal Camera | FLIR Boson 320 | 1 | $2,500 | $2,500 | 75 | 1-2 | FLIR OEM | 📋 Planned | Radiometric, good sensitivity |
| 3 | GNSS/RTK Module | u-blox ZED-F9P | 1 | $250 | $250 | 20 | 1 | u-blox | 📋 Planned | Centimeter accuracy, PPS output |
| 4 | Mission Computer | NVIDIA Jetson Xavier NX | 1 | $600 | $600 | 125 | 10-25 | NVIDIA | 📋 Planned | Edge ML processing |
| 5 | Storage | NVMe SSD 1TB | 1 | $125 | $125 | 50 | 2-3 | Various | 📋 Planned | High-speed data recording |
| 6 | Power Distribution | Custom PCB | 1 | $75 | $75 | 30 | - | TBD | 📋 Planned | Regulated rails, CAN gateway |
| 7 | CAN Gateway MCU | STM32F4 | 1 | $15 | $15 | 5 | 0.5 | STMicro | 📋 Planned | Sensor bus controller |
| 8 | Cables & Connectors | Various | 1 | $100 | $100 | 50 | - | Various | 📋 Planned | USB, Ethernet, power |
| 9 | Mounting Hardware | 3D Printed | 1 | $50 | $50 | 100 | - | Local | 📋 Planned | Adapter plate, brackets |
| **TOTAL** | | | | | **$9,215** | **~680g** | **~20-35W** | | | |

### Minimal Config Summary
- **Total Cost**: ~$9,200
- **Total Weight**: ~680g
- **Power Consumption**: ~20-35W
- **Primary Use**: Multispectral + thermal vineyard monitoring

---

## Full Configuration (Additions)

*Complete sensor suite for comprehensive vineyard analysis*

| # | Component | Model | Qty | Unit Cost | Total Cost | Weight (g) | Power (W) | Supplier | Status | Notes |
|---|-----------|-------|-----|-----------|------------|------------|----------|----------|--------|-------|
| 10 | RGB Camera | Industrial IMX Module | 1 | $750 | $750 | 150 | 2-5 | TBD | 📋 Planned | Global shutter, 12-20MP |
| 11 | LiDAR | Livox Mid-40 | 1 | $1,750 | $1,750 | 700 | 8-12 | Livox | 📋 Planned | 3D structure mapping |
| 12 | IMU | VectorNav VN-100 | 1 | $650 | $650 | 30 | 0.5 | VectorNav | 📋 Planned | High-quality orientation |
| 13 | Telemetry Radio | SiK Radio 915MHz | 1 | $50 | $50 | 30 | 2 | Various | 📋 Planned | Long-range telemetry |
| 14 | 4G/LTE Modem | Quectel EC25 | 1 | $75 | $75 | 20 | 2 | Quectel | 📋 Planned | Optional data link |
| **ADDITIONAL TOTAL** | | | | | **$3,275** | **~930g** | **~15-22W** | | | |

### Full Config Summary
- **Additional Cost**: ~$3,300
- **Additional Weight**: ~930g
- **Additional Power**: ~15-22W
- **Combined Total Cost**: ~$12,500
- **Combined Total Weight**: ~1,610g
- **Combined Power**: ~35-57W

---

## Mechanical Components

| # | Component | Material | Qty | Unit Cost | Total Cost | Weight (g) | Supplier | Status | Notes |
|---|-----------|----------|-----|-----------|------------|------------|----------|--------|-------|
| 15 | Ball Turret Base | PETG/Nylon (3D printed) | 1 | $20 | $20 | 200 | Local | 📋 Planned | Modified Thingiverse design |
| 16 | Adapter Plate | PETG/Nylon (3D printed) | 1 | $15 | $15 | 150 | Local | 📋 Planned | Custom sensor mounting |
| 17 | Sensor Mounts | PETG/Nylon (3D printed) | 4 | $5 | $20 | 100 | Local | 📋 Planned | Individual sensor brackets |
| 18 | Vibration Dampers | Rubber/TPU | 8 | $2 | $16 | 20 | Various | 📋 Planned | Camera isolation |
| 19 | Fasteners | M3/M4 hardware | 1 | $30 | $30 | 50 | Various | 📋 Planned | Screws, standoffs, etc. |
| **MECHANICAL TOTAL** | | | | | **$101** | **~520g** | | | |

---

## Power System

| # | Component | Model | Qty | Unit Cost | Total Cost | Weight (g) | Supplier | Status | Notes |
|---|-----------|-------|-----|-----------|------------|------------|----------|--------|-------|
| 20 | Power Distribution PCB | Custom | 1 | $75 | $75 | 30 | TBD | 📋 Planned | 5V/12V regulated rails |
| 21 | Voltage Regulators | Various | 4 | $5 | $20 | 10 | Various | 📋 Planned | 5V, 12V, 3.3V |
| 22 | Power Connectors | XT60, JST, etc. | 1 | $25 | $25 | 20 | Various | 📋 Planned | Power distribution |
| 23 | Fuses & Protection | Circuit breakers | 1 | $15 | $15 | 10 | Various | 📋 Planned | Overcurrent protection |
| **POWER TOTAL** | | | | | **$135** | **~70g** | | | |

---

## Software & Development

| # | Component | Type | Cost | Status | Notes |
|---|-----------|------|------|--------|-------|
| 24 | ROS2 Humble | Open Source | $0 | ✅ Available | Robot Operating System |
| 25 | PX4 Firmware | Open Source | $0 | ✅ Available | Flight controller |
| 26 | MAVROS | Open Source | $0 | ✅ Available | ROS-PX4 bridge |
| 27 | Agisoft Metashape | Commercial | $3,500 | 📋 Planned | Photogrammetry software |
| 28 | Pix4Dfields | Commercial | $5,000 | 📋 Planned | Multispectral processing |
| **SOFTWARE TOTAL** | | | **$8,500** | | |

*Note: Open source alternatives available for photogrammetry (OpenDroneMap) and processing (QGIS)*

---

## Grand Total Summary

### Minimal Configuration
- **Hardware**: $9,215
- **Mechanical**: $101
- **Power**: $135
- **Software**: $0 (open source) to $8,500 (commercial)
- **TOTAL**: **$9,451** (open source) to **$17,951** (commercial software)

### Full Configuration
- **Hardware**: $12,490
- **Mechanical**: $101
- **Power**: $135
- **Software**: $0 (open source) to $8,500 (commercial)
- **TOTAL**: **$12,726** (open source) to **$21,226** (commercial software)

---

## Procurement Priority

### Phase 1: Essential Components (Start Here)
1. ✅ u-blox ZED-F9P (GNSS/RTK) - $250
2. ✅ NVIDIA Jetson Xavier NX - Mission computer
3. ✅ NVMe SSD - Storage
4. ✅ MicaSense RedEdge-MX - Primary agricultural sensor
5. ✅ FLIR Boson 320 - Thermal imaging

### Phase 2: Integration Components
6. ✅ Custom Power Distribution PCB
7. ✅ CAN Gateway MCU
8. ✅ Mounting hardware (3D printed)
9. ✅ Cables and connectors

### Phase 3: Enhanced Capabilities
10. ✅ RGB Camera
11. ✅ IMU
12. ✅ LiDAR (if 3D mapping required)

### Phase 4: Software & Processing
13. ✅ Photogrammetry software (or open source alternative)
14. ✅ Multispectral processing tools

---

## Cost Optimization Strategies

1. **Open Source Software**: Use OpenDroneMap and QGIS instead of commercial software ($8,500 savings)
2. **Alternative Sensors**: Consider lower-cost multispectral options for initial testing
3. **3D Printing**: Print mechanical components in-house to reduce costs
4. **Bulk Purchasing**: Group component orders for better pricing
5. **Used Equipment**: Consider used/refurbished sensors for non-critical applications

---

## Weight & Power Budget

### Moose UAV Constraints
- **Max Payload**: ~2000-2500g (estimated)
- **Available Power**: Dependent on battery capacity and flight duration

### Payload Budgets

| Configuration | Weight | Power | Within Limits? |
|---------------|--------|-------|---------------|
| Minimal | ~680g | ~20-35W | ✅ Yes |
| Full | ~1,610g | ~35-57W | ⚠️ May require optimization |

**Recommendations**:
- Start with minimal configuration
- Optimize power consumption through efficient processing
- Consider battery capacity upgrades for full configuration
- Monitor flight time impact of payload weight

---

## Status Legend

- ✅ **Available**: Component available, ready to order
- 📋 **Planned**: Component identified, not yet procured
- 🔄 **In Progress**: Component ordered or being integrated
- ⚠️ **Needs Review**: Component requires further evaluation
- ❌ **Cancelled**: Component no longer needed

---

## Notes

- All costs are approximate and subject to change
- Weight and power specifications are from manufacturer datasheets
- Actual values may vary based on specific models and configurations
- Consider shipping, import duties, and taxes in final budget
- Some components may require development kits or evaluation boards first

---

*Last Updated: 2025-01-XX*
*Next Review: After Phase 1 procurement*

