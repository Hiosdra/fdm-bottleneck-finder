# 3D Printer Speed Bottleneck Finder

A web-based tool to simulate acceleration physics and volumetric flow constraints to identify the true printing speed limits of your 3D printer setup.

## 🚀 Live Demo

Visit the live tool at: **[https://hiosdra.github.io/fdm-bottleneck-finder/](https://hiosdra.github.io/fdm-bottleneck-finder/)**

## ✨ Features

- **Interactive Physics Simulation**: Real-time calculation of achievable speeds based on acceleration, jerk, and volumetric flow limits
- **Multiple Print Types**: Separate analysis for infill, walls, top/bottom surfaces, and travel moves
- **Visual Analysis**: 
  - Speed vs. distance graphs showing how move length affects achievable speed
  - Flow rate visualization
  - Bottleneck identification (acceleration vs. volumetric flow vs. user settings)
- **Deep Move Analysis**: Detailed breakdown of time costs and efficiency for specific move distances
- **Optimization Recommendations**: Actionable suggestions to reduce print time based on your limiting factors
- **Responsive Design**: Works seamlessly on desktop and mobile devices

## 🎯 Use Cases

- **Profile Optimization**: Identify which parameter changes will have the biggest impact on print time
- **Hardware Upgrade Planning**: Understand if upgrading hotend flow capacity or improving acceleration will benefit your prints more
- **Slicer Tuning**: Set realistic speed values that account for acceleration physics
- **Print Time Estimation**: Better understand why your actual print speeds differ from configured speeds

## 📊 What It Analyzes

The tool calculates the **actual achievable speed** for moves of different lengths, considering:

1. **Acceleration Limits**: How quickly your printer can speed up and slow down
2. **Volumetric Flow Limits**: Maximum melt rate of your hotend (e.g., E3D V6 ~15 mm³/s, Volcano ~25 mm³/s)
3. **User-Configured Speeds**: Speed limits set in your slicer
4. **Jerk/Junction Deviation**: Instantaneous speed change capability

For short moves, acceleration becomes the primary bottleneck. For longer moves with high speeds, volumetric flow often limits performance.

## 🛠️ Usage

1. Open the [live tool](https://hiosdra.github.io/fdm-bottleneck-finder/)
2. Enter your printer's specifications:
   - **Physical Limits**: Nozzle size, max volumetric flow, layer height, line width
   - **Slicer Speeds**: Configured speeds for different move types
   - **Kinematics**: Acceleration values and jerk/square corner velocity
3. View the real-time graphs and analysis:
   - Switch between speed and flow rate views
   - Use the slider in "Deep Move Analysis" to examine specific move distances
4. Review optimization suggestions to identify upgrade or configuration changes

## 💻 Local Development

Since this is a static website, you can run it locally with any web server:

### Option 1: Python
```bash
# Python 3
python -m http.server 8000

# Then open: http://localhost:8000
```

### Option 2: Node.js
```bash
npx serve .

# Then open the URL provided
```

### Option 3: VS Code
Use the "Live Server" extension and right-click `index.html` → "Open with Live Server"

## 📁 Repository Structure

```
.
├── index.html          # Main application (standalone, all-in-one file)
├── README.md          # This file
└── JUNIE.md           # Junie workflow information
```

## 🔧 Technologies Used

- **Vanilla JavaScript**: No build process required
- **Tailwind CSS**: Via CDN for styling
- **Chart.js**: Interactive graphs
- **Lucide Icons**: Modern icon set

## 📝 Technical Details

The physics calculations use a simplified trapezoidal motion profile:
- Acceleration phase from jerk velocity to max velocity
- Cruise phase at constant velocity (if move is long enough)
- Deceleration phase back to jerk velocity

The tool identifies which factor (acceleration, volumetric flow, or configured speed) limits performance for each move type and distance.

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs or suggest features via [Issues](https://github.com/Hiosdra/fdm-bottleneck-finder/issues)
- Submit pull requests with improvements
- Share feedback on the calculations or UI/UX

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

Created to help the 3D printing community optimize their print profiles and understand printer limitations.
