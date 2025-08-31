# KAMP Adaptive Density Control (KAMP-ADC)

[![Klipper](https://img.shields.io/badge/Klipper-Compatible-blue.svg)](https://www.klipper3d.org/)
[![License](https://img.shields.io/badge/License-GPLv3-green.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Version](https://img.shields.io/badge/Version-1.0.0-orange.svg)]()

An intelligent extension of KAMP (Klipper Adaptive Meshing & Purging) that automatically adjusts bed mesh density based on print size.

## Key Features

-  **Smart Adaptive Density**: Automatically adjusts probe points based on relative print size
-  **Time Optimization**: Fewer points for large prints, more points for small prints
-  **Fully Customizable**: Configure thresholds and multipliers to your needs
-  **Detailed Feedback**: Real-time information about applied adjustments
-  **Full Compatibility**: Maintains all original KAMP functionality

## How It Works

| Print Size | Density | Benefit |
|------------|---------|---------|
| **Small** (<20%) | +50% points | Better precision for fine details |
| **Medium** (20-50%) | +25% points | Ideal quality/time balance |
| **Large** (>50%) | Original density | Maximum efficiency without quality loss |

## Installation

1. **Have original KAMP installed**
2. **Replace files**:
   - `KAMP_Settings.cfg` → Add new variables
   - `Adaptive_Meshing.cfg` → Replace with modified file
3. **Restart Klipper**:
   ```bash
   RESTART


## Configuration

Edit `KAMP_Settings.cfg` to customize behavior:

```cfg
# Adaptive Density Control
variable_small_size_threshold: 0.2          # Threshold for small pieces (0.0-1.0)
variable_medium_size_threshold: 0.5         # Threshold for medium pieces (0.0-1.0)
variable_small_piece_multiplier: 1.5        # Multiplier for small pieces
variable_medium_piece_multiplier: 1.25      # Multiplier for medium pieces
variable_large_piece_multiplier: 1.0        # Multiplier for large pieces
```

## Configuration Examples

**Precision Profile (Recommended)**:
```cfg
variable_small_size_threshold: 0.15
variable_medium_size_threshold: 0.4
variable_small_piece_multiplier: 1.8
variable_medium_piece_multiplier: 1.4
variable_large_piece_multiplier: 1.0
```

**Speed Profile**:
```cfg
variable_small_size_threshold: 0.25
variable_medium_size_threshold: 0.6
variable_small_piece_multiplier: 1.3
variable_medium_piece_multiplier: 1.1
variable_large_piece_multiplier: 0.9
```

## Expected Results

| Scenario | Original Mesh | KAMP-ADC | Benefit |
|----------|---------------|----------|---------|
| Small (10%) | 100 points | 150 (15) points | +50% precision |
| Medium (40%) | 100 points | 125 (40) points | +25% Balanced |
| Large (80%) | 100 points | 100 points | Maintains efficiency |

# ⚠️ Disclaimer

**This mod was only tested on the Neptune 4 Pro V1.1.3.3. I can’t guarantee this won’t cause issues, but the changes I made are pretty minor compared to the original. If anyone with deeper Klipper knowledge wants to double-check, I’d really appreciate it.**
