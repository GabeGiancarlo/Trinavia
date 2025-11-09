# Ball Turret Integration Guide

Integration of the Trinavia sensor payload with the Thingiverse mini gimbal ball turret design.

## Base Design Reference

**Source**: [Thingiverse Mini Gimbal](https://www.thingiverse.com/thing:592330)

The base design provides a compact two-axis gimbal suitable for small camera payloads. For our agricultural sensor suite, we'll need to modify and reinforce the design.

## Design Constraints

### Original Limitations
- **Payload Capacity**: ~300-400g per sensor module
- **Internal Volume**: Limited space for electronics
- **Material**: Designed for PLA/PETG printing
- **Degrees of Freedom**: Continuous yaw + limited tilt (±90°)

### Our Requirements
- **Payload**: 500-600g (minimal config) to 1200-1500g (full config)
- **Sensors**: Multiple cameras + thermal + potential LiDAR
- **Electronics**: Mission computer, power distribution, CAN gateway
- **Reliability**: Agricultural environment operation

## Design Modifications

### 1. Scaling & Reinforcement

**Approach**:
- Scale up base design by 1.5-2x for increased payload capacity
- Use stronger materials: PETG, Nylon, or carbon-fiber reinforced filament
- Add structural reinforcements at stress points
- Increase wall thickness for critical load-bearing sections

**Materials**:
- **Primary Structure**: PETG or Nylon (better impact resistance)
- **High-Stress Areas**: Carbon-fiber reinforced PETG or Nylon
- **Flexible Components**: TPU for cable management

### 2. Custom Adapter Plate

**Design Requirements**:
- Bolt pattern matching ball turret servo mounts
- Mounting points for sensor modules
- Cable routing channels
- Vibration isolation mounting points
- Weight distribution optimization

**CAD Considerations**:
- Parametric design for easy modification
- Modular mounting system for different sensor configurations
- Thermal management (ventilation for electronics)
- Water resistance (IP54 minimum for agricultural use)

### 3. Cable Management

**Challenges**:
- Multiple sensor cables (USB, Ethernet, power)
- CAN bus wiring
- GNSS antenna cable
- Rotating interface for continuous yaw

**Solutions**:
- **Limited Yaw (±90°)**: Standard servo harness, no slip-ring needed
- **360° Yaw**: Slip-ring for power, UAVCAN over rotating interface for data
- Cable routing channels in adapter plate
- Strain relief at all connection points

### 4. Vibration Isolation

**Strategy by Component**:

| Component | Mounting Type | Rationale |
|-----------|---------------|-----------|
| RGB Camera | Soft mount (rubber dampers) | Reduce motion blur |
| Multispectral | Soft mount | Image quality critical |
| Thermal | Foam isolation | Vibration affects thermal accuracy |
| LiDAR | Rigid mount | Stable scan geometry required |
| Mission Computer | Soft mount | Protect from vibration damage |
| GNSS/IMU | Rigid mount | Accurate orientation measurement |

**Implementation**:
- Rubber grommets for camera mounts
- Foam padding for thermal sensor
- Rigid aluminum brackets for LiDAR
- Vibration-damping material between adapter plate and turret

## Mounting Strategy

### Component Placement

**On Gimbal (Aimed Scans)**:
- RGB Camera
- Multispectral (RedEdge-MX)
- Thermal (FLIR Boson)
- Total weight: ~400-500g

**Fixed to Airframe (Near CG)**:
- LiDAR (Livox Mid-40) - too heavy for gimbal
- RTK GNSS base antenna (if using base station)
- Mission computer (can be on gimbal if lightweight config)
- Power distribution board

**Rationale**:
- Keep gimbal payload under 500g for reliable operation
- Heavy components near CG minimize flight dynamics impact
- LiDAR doesn't need pointing (360° or wide FOV)

### Weight Distribution

**CG Considerations**:
- Calculate payload CG relative to aircraft CG
- Balance gimbal payload to minimize servo load
- Consider moment arm effects on flight stability

**Weight Budget**:
- Gimbal payload: <500g recommended
- Fixed payload: Remaining weight
- Total: Must fit within Moose payload capacity (~2000-2500g)

## Mechanical Integration Steps

### Step 1: Design Custom Adapter Plate

1. Import ball turret STL into CAD software
2. Design adapter plate with:
   - Bolt pattern matching turret mounts
   - Sensor mounting points
   - Cable routing
   - Weight distribution optimization
3. Export STL for 3D printing

### Step 2: Material Selection & Printing

1. **Primary Structure**: PETG or Nylon
   - Print settings: 0.2mm layer height
   - 3-4 perimeters for strength
   - 20-30% infill
2. **Reinforcements**: Carbon-fiber reinforced filament
   - Use for high-stress areas
   - May require hardened nozzle

### Step 3: Assembly

1. Print adapter plate and test fit on ball turret
2. Install vibration isolation mounts
3. Mount sensors to adapter plate
4. Route cables through channels
5. Connect to power distribution and data buses
6. Test gimbal movement range and cable clearance

### Step 4: Integration Testing

1. **Static Tests**:
   - Weight distribution check
   - CG calculation
   - Cable routing validation
   - Gimbal range of motion

2. **Dynamic Tests**:
   - Vibration analysis
   - Gimbal servo response
   - Power consumption
   - Heat management

3. **Flight Tests**:
   - Small-scale test flights
   - Gimbal operation during flight
   - Data collection validation

## Design Files

### CAD Models (To Be Created)

- `adapter-plate.step` - Main adapter plate design
- `sensor-mounts/` - Individual sensor mounting brackets
- `cable-routing/` - Cable management components
- `vibration-isolation/` - Damping mounts

### 3D Printing Files

- `adapter-plate.stl` - Ready to print
- `sensor-mounts/*.stl` - Individual mounts
- Print profiles for different materials

## Future Enhancements

### Potential Improvements

1. **Active Stabilization**: Add IMU feedback to gimbal for active vibration cancellation
2. **Weather Sealing**: IP65+ rating for harsh agricultural environments
3. **Modular Design**: Quick-swap sensor modules for different mission profiles
4. **Heated Enclosure**: For operation in cold conditions
5. **Custom Gimbal Controller**: Optimized for agricultural scanning patterns

## References

- [Thingiverse Mini Gimbal](https://www.thingiverse.com/thing:592330)
- [UAVCAN Specification](https://uavcan.org/) - For rotating interface data transmission
- [Moose Build Documentation](../Moose%20build%20process/README.md) - Aircraft integration details

