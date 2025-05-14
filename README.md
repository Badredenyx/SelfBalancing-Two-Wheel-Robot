# 🤖 SelfBalancing Two-Wheel Robot

Welcome to the **SelfBalancing Two-Wheel Robot** project! This Simulink-based model demonstrates a classic control challenge: keeping a two-wheeled robot balanced upright using feedback control strategies.

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com/Badredenyx/SelfBalancing-Two-Wheel-Robot/actions)
[![MATLAB](https://img.shields.io/badge/MATLAB%20Compatibility-10.7-blue)](https://mathworks.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## 📖 Table of Contents

* [✨ Key Features](#-key-features)
* [⚙️ Installation](#️-installation)
* [🚀 Usage](#-usage)
* [🛠 Configuration](#-configuration)
* [📐 Architecture Diagram](#-architecture-diagram)
* [🧪 Examples](#-examples)
* [🤝 Contributing](#-contributing)
* [📄 License](#-license)

---

## ✨ Key Features

* **Balanced Control**: Implements a PID controller to stabilize the robot around its upright equilibrium.
* **Physical Modeling**: Uses Simscape Multibody to capture realistic dynamics.
* **Modular Blocks**: Organized into mechanism, controllers, joint interfaces, and converters.
* **Visualization**: 3D model rendered via `Two wheel Robot.png` for easy inspection.
* **Scalable**: Parameters can be tuned for different wheel sizes, masses, and control gains.

---

## ⚙️ Installation

1. **Prerequisites**:

   * MATLAB & Simulink R2021b (v10.7) or later.
   * Simscape Multibody Toolbox.

2. **Clone the repository**:

   ```bash
   git clone https://github.com/Badredenyx/SelfBalancing-Two-Wheel-Robot.git
   cd SelfBalancing-Two-Wheel-Robot
   ```

3. **Open the model**:

   * Double-click `SelfBalanicingRobot.slx` in MATLAB's Current Folder browser.

4. **Install any missing toolboxes** as prompted by Simulink.

---

## 🚀 Usage

1. **Open & Inspect**:

   * Launch `SelfBalanicingRobot.slx`.
   * Explore the top-level two-wheel robot subsystem and underlying blocks.

2. **Simulate**:

   * Click **Run** or type:

     ```matlab
     sim('SelfBalanicingRobot.slx');
     ```

3. **Visualize**:

   * The `Scope` blocks display angle, wheel position, and control signals.
   * Use the 3D viewer to see the robot’s response in real time.

---

## 🛠 Configuration

Configuration parameters are organized by subsystem:

* **Mechanism Configuration**: Gravity, joint linearization
* **PID Controller**: Gains (P, I, D), filter, saturation limits
* **PS-Simulink Converters**: Units, domain settings
* **Joints & Transforms**: Limits, stiffness, damping, poses

> 🔧 **Tip:** Use Model Explorer (View → Model Explorer) to search for parameter names like `P`, `SpringStiffness`, or `TranslationStandardOffset`.

---

## 📐 Architecture Diagram

![Two-Wheel Robot](Two%20wheel%20Robot.png)

> Figure: Top-level view of the Self-Balancing Two-Wheel Robot model.

---

## 🧪 Examples

Below is an example script to run automated parameter sweeps on the PID gains:

```matlab
% Example: Sweep P gain from 10 to 100
for P_gain = linspace(10,100,5)
    set_param('SelfBalanicingRobot/PID Controller','P',num2str(P_gain));
    out = sim('SelfBalanicingRobot.slx');
    fprintf('P = %g, Peak Angle = %g\n', P_gain, max(out.angle_rad));
end
```

---

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repo. 🍴
2. Create a feature branch: `git checkout -b feature/YourFeature`
3. Commit your changes: `git commit -m "Add awesome feature"`
4. Push to your branch: `git push origin feature/YourFeature`
5. Open a Pull Request.

Be sure to follow [Contributor Guidelines](CONTRIBUTING.md) (coming soon!).

---

## 📄 License

This project is licensed under the **MIT License**. See [LICENSE](LICENSE) for details.
