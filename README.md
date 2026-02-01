# Solar Energy Modeling & Optimization

This repository contains a mathematical modeling framework designed to optimize photovoltaic (PV) panel orientation for maximum energy yield and economic return.

Developed as part of the *Mathematics 1b* (01002) course at the Technical University of Denmark (DTU), the project integrates vector calculus with real-world energy market data to simulate solar performance in Danish weather conditions.

## ⚡ Project Overview

The core objective is to determine the optimal tilt ($\theta$) and azimuth ($\phi$) angles for a solar panel setup to maximize two distinct metrics:
1.  **Total Energy Output (kWh):** Maximizing raw generation based on solar irradiance flux.
2.  **Economic Efficiency (DKK):** Minimizing household electricity costs by aligning generation with consumption patterns and volatile spot prices (Nord Pool).

## 🧠 Methodology

### Mathematical Modeling
* **Solar Position:** Uses `pvlib` to track solar Zenith and Azimuth angles specific to DTU's coordinates ($55.79^\circ$ N, $12.52^\circ$ E).
* **Flux Integration:** Calculates the instantaneous flux through the panel surface using vector projection:
    $$\text{Flux} = \int_{T} (\vec{S} \cdot \vec{n}) \, dt$$
    Where $\vec{S}$ is the solar irradiance vector and $\vec{n}$ is the panel's normal vector.
* **Numerical Integration:** Utilizes Simpson's rule (`scipy.integrate.simpson`) to aggregate power into total energy over daily and yearly intervals.

### Economic Optimization
* **Spot Price Integration:** Ingests hourly electricity prices (`Elspotprices_2023_hourly.csv`) and typical household consumption profiles.
* **Grid Interaction:** Simulates the cost/benefit of self-consumption vs. selling excess power back to the grid (including tariffs and fees).

## 🛠 Tech Stack

* **Core Logic:** Python, NumPy, SymPy
* **Solar Physics:** `pvlib` (Photovoltaic Library)
* **Optimization & Integration:** `scipy`
* **Data Handling:** Pandas (CSV processing for spot prices)
* **Visualization:** Matplotlib

## 🚀 Usage

The project is divided into physical modeling and economic optimization modules.

1.  **Install Dependencies:**
    ```bash
    pip install numpy pandas matplotlib scipy pvlib sympy
    ```

2.  **Run Economic Optimization:**
    To find the optimal angles based on 2023 spot prices:
    ```bash
    python Energiforbrug_Optimering/Energiforbrug_Optimering.py
    ```

3.  **Visualize Solar Positions:**
    To plot elevation curves for a specific date:
    ```bash
    python Solpositionsmodellering/solarposition_models.py
    ```

## 📊 Results

The simulation performs a grid search over valid $\theta$ and $\phi$ angles. 
* **Output:** Generates `energy_data.csv` containing hourly generation profiles for the optimal configuration.
* **Insights:** The model demonstrates that the angle for maximum *energy* often differs from the angle for maximum *profit*, primarily due to the correlation between peak spot prices and evening consumption.

---
## Project Team
DTU*# README for Solpanel 04 Project (01002 Matematik 1b

- Yuxuan Zhang (s234807)
- Oscar Thorsted Svendsen (s224177)
- Carl Schmidt-Svejstrup (s234840)
- Mikkel Broch-Lips (s234860)
- David Lindahl (s234817)
- Nikolaj Holst Jakobsen (s234818)
