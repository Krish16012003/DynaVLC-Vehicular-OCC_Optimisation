# An Optimized Dynamic MAC Protocol for Vehicular Optical Camera Communication (DynaVLC)

This repository contains the project report and simulation code for "An Optimized Dynamic MAC Protocol for Vehicular Optical Camera Communication Networks." The project introduces **DynaVLC**, an intelligent and adaptive Medium Access Control (MAC) protocol designed to enhance the performance of Vehicular Optical Camera Communication (V-OCC) by dynamically adjusting to real-time traffic conditions.

## Project Overview

Traditional Radio Frequency (RF) systems for vehicular communication face growing spectrum congestion. Optical Camera Communication (OCC)—which uses vehicle LEDs as transmitters and cameras as receivers—offers a cost-effective, secure, and interference-free alternative. However, the standard protocol for this technology, IEEE 802.15.7, is semi-static and performs poorly in the highly dynamic vehicular environment.

The DynaVLC algorithm solves this by introducing a real-time feedback loop that tunes key MAC parameters based on live network metrics, transforming the rigid standard into a flexible system optimized for V-OCC.

## The Challenge: Limitations of Standard IEEE 802.15.7

The core issue with the standard is its rigidity. A fixed MAC configuration optimized for a dense traffic jam (high density, low speed) will be inefficient on an open highway (low density, high speed). DynaVLC addresses this by adapting to:
* **High Mobility & Dynamic Topologies:** Constant changes in vehicle position and link quality.
* **Varying Node Density:** Fluctuations between sparse and congested traffic.
* **Low Bandwidth of OCC:** The need for extremely efficient use of the limited data rate available through cameras.

## Key Innovations of the DynaVLC Algorithm

The DynaVLC algorithm implements a dual-axis optimization strategy, decoupling the management of network capacity from network volatility. This is achieved by adjusting MAC parameters based on two key real-time metrics: **vehicle density** and **average speed**.

The core adaptive mechanisms include:
* **Pressure Ratio (ρ) Heuristic:** A novel metric (`ρ = Required_Slots / Available_Slots`) that provides an instantaneous measure of network congestion.
* **Dynamic Multi-Superframe Order (MO) Adjustment:** The algorithm increases or decreases the number of superframes in a beacon interval based on the pressure ratio, expanding or shrinking the pool of available communication slots to match demand.
* **Dynamic Superframe Order (SO) Adjustment:** The active duration of a superframe is lengthened for high-speed traffic (to ensure link stability) and shortened for low-speed traffic (to reduce latency), based on average vehicle speed.
* **Dynamic CAP Reduction:** In high-load scenarios, the algorithm reclaims time from the contention-based period (CAP) and reallocates it to the guaranteed, collision-free period (CFP), prioritizing reliable data transmission when the network is busy.

## Performance Analysis & Results

Comparative simulations against the baseline IEEE 802.15.7 standard demonstrate significant performance gains, especially under high network load.

* **Throughput Improvement:** DynaVLC achieves a **~15% increase** in network throughput by minimizing wasted slots and accommodating higher demand.
* **Latency Reduction:** Most critically, the algorithm achieves a **~50% reduction** in maximum communication delay, ensuring that safety-critical messages are delivered predictably and promptly.

These results are validated and visualized in the `1_Performance_Analysis_Graphs.ipynb` notebook.


## Code & Simulations

This repository includes three Jupyter Notebooks that model and simulate the DynaVLC protocol.

1.  **`1_Performance_Analysis_Graphs.ipynb`:** A model-based simulation that directly compares the throughput and delay of Optimized DynaVLC against the baseline IEEE 802.15.7 standard, generating the core performance graphs.
2.  **`2_Algorithm_Logic_Simulation.ipynb`:** A high-level simulation demonstrating the core adaptive logic of the DynaVLC algorithm, showing how MO, SO, and CAP Reduction parameters change in response to varying traffic levels and weather conditions.
3.  **`3_Hybrid_RF_OCC_Vehicular_Simulation.ipynb`:** A comprehensive, dynamic simulation of a multi-lane highway environment. This notebook implements a hybrid resource allocator where vehicles dynamically switch between RF and OCC. It includes a dummy ML module that adjusts the switching threshold based on collisions, demonstrating a practical application of adaptive resource management in a complex vehicular network.

## Tech Stack

* **Language:** Python
* **Libraries:** NumPy, Matplotlib, Pandas

## How to Run the Simulations

1.  Clone the repository.
2.  Ensure you have a Python environment with Jupyter Notebook (or use Google Colab).
3.  Install the required libraries: `pip install numpy matplotlib pandas`
4.  Open and run the notebooks in the `code/` directory.

## Project Report

For a complete academic breakdown of the V-OCC landscape, the IEEE 802.15.7 standard, and the detailed mechanics of the DynaVLC algorithm, please see the full project report.

* [**Read the Full Project Report here**](./report/DynaVLC_Optimization_Project_Report_.pdf)
