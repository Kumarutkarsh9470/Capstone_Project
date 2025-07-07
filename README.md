# Capstone_Project
Overview

This project implements an end-to-end dynamic pricing solution for urban parking lots. It:

Performs extensive exploratory data analysis (EDA) on parking occupancy and related features.

Engineers domain-specific features (occupancy ratios, rolling averages, vehicle type encoding, special-day flags).

Implements three pricing models:

Baseline Linear: Price adjusts incrementally based on occupancy ratio.

Demand-Based: Uses a weighted demand function incorporating occupancy, queue length, traffic, and special days.

Competitive-Aware: Factors in competitor prices to optimize local pricing.

Simulates real-time data ingestion and processing using Pathway’s streaming API.

Visualizes live price trajectories with Bokeh and Panel.

Tech Stack

Python 3.8+

Google Colab: Development and execution environment.

Pandas & NumPy: Data manipulation and numerical operations.

scikit-learn: Feature encoding and basic modeling.

Pathway: Real-time stream processing and windowed aggregations.

Bokeh & Panel: Interactive, live visualizations embedded in notebooks.

Mermaid: Architecture diagram in README.

Architecture Diagram :
![Untitled diagram _ Mermaid Chart-2025-07-07-174001](https://github.com/user-attachments/assets/63899bba-483d-4a4f-8c4d-bdb91a802d74)
Visit the link to see 

Architecture & Workflow

Data Loading: The CSV file is loaded and parsed into a Pandas DataFrame, combining date and time into a single Timestamp column.

EDA:

Missing values and distributions are analyzed.

Temporal trends (occupancy ratio over time) and spatial patterns (if geodata available) are visualized.

Correlation matrix to identify key drivers.

Feature Engineering:

Occupancy Ratio: occ_ratio = Occupancy / Capacity.

Rolling Averages: occ_roll3 over 3 half-hour intervals.

Special-Day Flag: Binary encoding if a given day has special events.

Vehicle Type Encoding: One-hot encode vehicle categories.

Model Implementations:

Model 1 (Baseline Linear): Sequential price updates based on occupancy.

Model 2 (Demand-Based): Demand signal = weighted sum of features; price scales from a base.

Model 3 (Competitive-Aware): Combines demand price with competitor pricing input.

Real-Time Simulation:

Pathway streams the half-hour records at a controlled rate.

Tumbling Window: Daily windows aggregate max/min occupancy to infer demand fluctuation.

Price Computation: Window outputs feed Bokeh updates continuously.

Visualization:

The delta_window table is bound to a Bokeh plot via Panel.

Live line and scatter glyphs show daily dynamic prices as the stream runs.

Running the Notebook

Clone the repo and open in Google Colab.

Ensure dataset.csv is in the root or upload via Colab file browser.

Run all cells in order:

Install dependencies

Load & prepare data

EDA

Feature engineering & model definitions

Real-time Pathway pipeline

Visualization
