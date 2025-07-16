# Colourful Containers v4.2 (CCv4.2) - Change Log

## Overview
This document details the changes and modifications made to create Colourful Containers v4.2 (CCv4.2) from VDX-DUI-v3.2.3 and VDX-MUI-v3.2.3.

## Source Packs
- VDX-DUI-v3.2.3 (Dark UI)
- VDX-MUI-v3.2.3 (Modern UI)

## Major Changes

### 1. Manifest.json Changes
- Updated pack name to "Colourful Containers BE - v4.2"
- New UUID: 48440f30-d760-4a23-8b34-0226219f9932
- Version updated to [4, 2, 0]
- Added new description with Discord server link
- Implemented new subpacks system:
  - Dark mode (memory_tier: 1)
  - Light mode (memory_tier: 2)
- Added settings section with mode descriptions
- Removed original metadata section
- Updated min_engine_version to [1, 21, 0]

### 2. Directory Structure Changes
The following directories were combined and modified:
- vdx/
- ui/
- textures/
- texts/
- subpacks/ (New directory)
  - dark/
  - light/
- sounds/
- font/
- assets/

### 3. New Features
- Implemented dual-mode system (Dark/Light)
- Added Discord community support
- Created new subpacks structure for theme variants
- Added in-game settings descriptions

### 4. Removed Features
- Removed original author metadata
- Removed original URL references
- Removed version-specific subpacks from MUI

### 5. Modified Features
- Updated UI elements to support both dark and light themes
- Modified container GUI textures
- Updated version compatibility to 1.21.1

### 6. UI-Specific Changes
#### Global Variables (_global_variables.json)
- Modified button colors:
  - Changed hover and pressed colors to [1.0, 1.0, 1.0]
  - Set locked button color to [0.62, 0.62, 0.62]
- Updated container text colors:
  - Changed container title text color to [1, 1, 1]
  - Changed 3x3 crafting title text color to [1, 1, 1]
  - Added new CC-specific container text color: [0.3, 0.3, 0.3]
- Modified enchanting table colors:
  - Runes color: [0.4, 0.36, 0.3]
  - Highlighted runes: [1.0, 1.0, 0.5]
  - Disabled runes: [0.2, 0.18, 0.14]
- Updated villager trade colors:
  - Trade tier name color: [1.0, 1.0, 1.0]
  - Locked trade tier color: [0.16, 0.14, 0.10]
- Added new UI features:
  - Custom hover text support
  - Custom durability bar support
  - Touch-specific item details
  - Gamepad helper configurations
- Modified HUD elements:
  - Updated experience bar colors
  - Modified chat size and message limits
  - Updated scoreboard colors
  - Added custom boss bar textures

### 7. Texture Changes
#### UI Textures
- Added comprehensive controller support textures:
  - Xbox controller buttons and controls
  - PlayStation 4/5 controller buttons and controls
  - Nintendo Switch controller buttons and controls
  - Generic controller support
- Added new UI elements:
  - Custom pointer texture
  - Purple border texture and JSON definition
  - Generic 14x14 face button textures
- Controller-specific features:
  - D-pad textures for all controller types
  - Face button textures (A/B/X/Y, Cross/Circle/Square/Triangle, etc.)
  - Trigger and bumper textures
  - Stick textures
  - Special buttons (Start, Select, Home, etc.)
  - Touchpad support for PlayStation controllers

## Process of Creation
1. Base Setup
   - Started with VDX-DUI-v3.2.3 as the primary base
   - Incorporated elements from VDX-MUI-v3.2.3
   - Created new manifest.json with updated version information

2. Directory Modifications
   - Combined and modified UI elements from both packs
   - Merged texture files
   - Updated text files
   - Added new subpacks directory
   - Integrated sound files
   - Updated font files
   - Modified asset files

## Credits
- Original DUI pack creators
- Original MUI pack creators
- CCv4.2 modifications by Redstone Chicken

## Version History
- v4.2: Current version
  - Combined DUI and MUI elements
  - Added dark/light mode system
  - Updated to 1.21.1 compatibility
  - Added Discord community support
  - Implemented new subpacks structure 