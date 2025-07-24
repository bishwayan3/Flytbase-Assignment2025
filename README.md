# Flytbase-Assignment2025
# FlytBase Drone Deconfliction Assignment – 2025

**Candidate**: Bishwayan Sarkar  
**Track**: UAV Systems | Robotics | Conflict Detection  
**Platform**: Google Colab + Plotly + scikit-learn  

---

## 1. Overview

This project implements a 4D drone deconfliction system simulating a primary mission and surrounding UAV traffic. The solution leverages a time-scaled 4D KD-Tree to efficiently detect spatiotemporal conflicts and visualizes the airspace dynamically using Plotly's animated 3D graphs.

---

## 2. Objectives Fulfilled

| Requirement                               | Status     |
|-------------------------------------------|------------|
| Simulate a primary drone mission          | ✅ Completed |
| Simulate multiple nearby drone flights    | ✅ Completed |
| Detect conflicts using space + time       | ✅ Completed |
| Use 4D KD-Tree with time scaling          | ✅ Completed |
| Return conflict time, location, ID        | ✅ Completed |
| Visualize missions and highlight conflict | ✅ Completed |
| Provide reusable query interface          | ✅ Completed |

---

## 3. Logic and Approach

### 3.1 Mission Representation
The primary mission is a list of 3D waypoints, time-stamped and interpolated into 4D points (x, y, z, t). Simulated drones follow randomly generated trajectories, also interpolated into timestamped 4D paths.

### 3.2 Time-Scaled KD-Tree
To convert time into a compatible spatial dimension, the time component is scaled using:

```python
time_scale = spatial_radius / temporal_tolerance
```

Each point is then represented as:

```
[x, y, z, t × time_scale]
```

This allows standard KDTree usage in 4D Euclidean space.

### 3.3 Conflict Detection
Each point of the primary trajectory is queried against the KD-Tree. If any simulated drone appears within the specified spatial and temporal bounds, the conflict is reported. The function stops on the first conflict found.

A modular function is defined for reuse:

```python
def check_conflict_kdtree(...):
    return 'clear' or detailed conflict dictionary
```

---

## 4. Visualization

- Primary drone path: **blue line**
- Simulated drone paths: **orange points**
- Conflict point: marked with a **cross symbol**, annotated with time and location
- **Play button**: enables real-time animation with contextual annotations

---

## 5. How to Run

### Requirements:
- Google Colab (preferred)
- Python 3.10+
- Libraries: `plotly`, `scikit-learn`

### Steps:
1. Define the primary and simulated drone trajectories.
2. Run the conflict detection function.
3. Animate the result using the provided Plotly visualizer.

---

## 6. Edge Case Handling

The conflict detection correctly handles situations where drones are **spatially close but temporally far apart**. The tolerance is tunable by adjusting the **spatial radius** and **temporal threshold**.

---

## 7. Sample Conflict Output

```
   Conflict at t = 7.66s
   Primary point #159 → [12.771084337349398, 7.771084337349398, 2.16867469879518]
   Collides with Drone 0 at point [13.862254599169832, 7.746677959805442, 1.5897870746212588, 8.044692737430168]

```

## 8. Tools and Technologies

- **Python**: Main programming language  
- **Plotly**: 3D visualization  
- **scikit-learn**: KD-Tree structure  
- **Google Colab**: Cloud-based notebook environment

## 9. AI Assistance

Portions of this project were enhanced with the help of **ChatGPT (OpenAI)** for code structuring, conflict logic optimization, and visualization formatting.

---

## 10. Contact

**Bishwayan Sarkar**  
📞 +91-9678285952  
✉️ bishwayansarkar33@gmail.com
