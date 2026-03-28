# Real-Time-object-detection-using-Joint-Dehazing-and-multimodal-fusion-in-adverse-weather-conditions

**What is DAAF-YOLOv8?**
DAAF-YOLOv8 is a novel RGB-Thermal multimodal fusion framework that achieves state-of-the-art object detection performance under adverse weather conditions (fog, rain, night, glare) while maintaining real-time edge deployment capability (50 FPS on T4 GPU).

Unlike traditional approaches that rely on heavy restoration networks or static fusion rules, DAAF learns to dynamically prioritize the more reliable sensor using cross-modal attention—without requiring weather labels or domain supervision.

Performance Highlights
Model	Modality	mAP@50	mAP@50-95	FPS (T4)	Params
DAAF-YOLOv8 (Ours)	RGB+Thermal	76.1%	41.4%	50	3.2M
YOLOv8n (baseline)	RGB	71.6%	41.2%	52	3.0M
TIR-YOLO-ADAS	Thermal	70.3%	41.8%	35	8.1M
DSNet	RGB	65.4%	38.2%	28	15.2M

**Architectural Flow**:

<img width="306" height="281" alt="image" src="https://github.com/user-attachments/assets/157d4f1b-a1a6-4d88-ae40-c60743ecb077" />


The proposed architecture processes RGB and thermal images to achieve robust object detection under challenging environmental conditions. Both modalities are first passed through separate YOLOv8 backbone networks to extract deep visual and thermal features. These features are then organized using multi-scale feature pyramid extraction, enabling the model to detect objects of varying sizes. A modality configuration controller allows the system to operate in RGB-only, thermal-only, or multimodal modes. The core component, domain-adaptive attention fusion, integrates features using bidirectional cross-attention and spatially adaptive modality weighting while suppressing weather-related noise. Finally, fused multi-scale representations (P3, P4, P5) generate a weather-robust multimodal feature representation for accurate and reliable object detection<img width="468" height="92" alt="image" src="https://github.com/user-attachments/assets/f0c8b719-1d44-4680-98bf-d6de7cd3eff3" />



**DAAF Module Components:**

Thermal→RGB Attention: Thermal guides refinement of degraded RGB features

RGB→Thermal Attention: RGB provides texture details to thermal

Spatial Modality Weighting: Per-pixel sensor reliability estimation

Feature Alignment: Reduces RGB-Thermal domain gap


**Applications**
1. Automotive ADAS
Night pedestrian/vehicle detection

Automatic Emergency Braking (AEB)

Forward Collision Warning (FCW)

Blind spot monitoring

2. Autonomous Vehicles
Level 2+ autonomy in adverse weather

Redundant sensor fusion with LiDAR/radar

Edge deployment on Jetson Orin

3. UAV Surveillance
Night search-and-rescue

Perimeter security through foliage/smoke

4. Industrial Robotics
Warehouse AGV obstacle avoidance

Low-light worker detection

