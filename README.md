# TRACER Pre-Production Model

## About The Project

[cite_start]The TRAcking Community Exposures and Releases (TRACER) model is designed to simulate emissions of volatile organic compounds (VOCs) from unconventional oil and gas development (UOGD). [cite: 16, 18] [cite_start]Current emission models often do not accurately reflect recent UOGD practices, and TRACER was developed to address this gap. [cite: 17]

[cite_start]Based on the Mechanistic Air Emissions Simulator (MAES), the TRACER model can simulate emissions for over 50 VOC species, including alkanes, alkenes, and aromatics. [cite: 18, 19] [cite_start]It covers complex pre-production activities like drilling, hydraulic fracturing, mill-out, and flowback with detailed time resolution. [cite: 19]

The model is a versatile tool for applications such as:
* [cite_start]Compiling emission inventories [cite: 20]
* [cite_start]Assessing health impacts [cite: 20]
* [cite_start]Evaluating air quality [cite: 20]

[cite_start]To make it accessible for policymaking and environmental health research, the model includes a Graphical User Interface (GUI). [cite: 21] [cite_start]The GUI is a standalone executable for Windows, built using Python 3. [cite: 22]

***

## Key Features

* [cite_start]**Detailed Timeline Simulation**: Simulates high-resolution operational timelines for pre-production activities at UOGD sites. [cite: 19] [cite_start]You can use real, logged data or generate simulated timelines using a Monte Carlo approach based on field data. [cite: 56, 64]
* [cite_start]**Comprehensive VOC Modeling**: Models emissions for more than 50 different VOC species. [cite: 19]
* [cite_start]**Flexible Emission Rates**: Incorporates several adjustable emission rate datasets from recent field studies and EPA tools. [cite: 86, 87, 88] [cite_start]Users can also provide their own emission data. [cite: 93]
* **Atmospheric Dispersion**: Integrates two types of dispersion models:
    * [cite_start]A **Gaussian plume model** with pre-defined and customizable meteorological conditions. [cite: 97, 104, 105]
    * [cite_start]Integration with pre-computed **AERMOD** simulation outputs. [cite: 97, 112]
* [cite_start]**Data Visualization and Export**: Allows users to plot results directly in the interface and export data to `.csv` files for further analysis. [cite: 50, 53]

***

## Getting Started

### Prerequisites

[cite_start]The TRACER Pre-Production Module is a standalone executable file designed for Windows platforms. [cite: 22]

### Installation

1.  [cite_start]Download the repository as a ZIP file. [cite: 25] [cite_start](Note: The final version will be archived on the Collett Research Group website or a dedicated GitHub repository. [cite: 26])
2.  [cite_start]Extract all the contents of the ZIP file into a single folder. [cite: 27]
3.  [cite_start]Ensure the `config`, `input`, and `output` folders are located in the same directory as the main executable. [cite: 28]

***

## Quick Start Guide

1.  Run the `HEI_GUI.exe` application to launch the model. [cite_start]A graphical interface will appear after a few seconds. [cite: 28, 29]
2.  [cite_start]**Step 1: Load Operation Timeline.** [cite: 32]
    * [cite_start]Use the "Timeline source" dropdown to load a timeline from a real operational log file. [cite: 59]
    * [cite_start]Alternatively, go to the "Advanced Modes" to simulate an ensemble of timelines. [cite: 63]
3.  [cite_start]**Step 2: Choose Emission Factors.** [cite: 35]
    * [cite_start]Select a pre-defined set of emission factors from the "Emission source" dropdown menu and click "Load". [cite: 35]
    * [cite_start]Use the "Species" dropdown menu to select the specific pollutant you want to model. [cite: 39]
4.  [cite_start]**Step 3: Load or Simulate Atmospheric Dispersion.** [cite: 41]
    * [cite_start]Select a dispersion model using the "Dispersion configuration" dropdown. [cite: 41]
    * [cite_start]If using the **Gaussian plume model**, select the atmospheric conditions and enter the downwind distance from the source. [cite: 43, 45]
    * [cite_start]If using the **AERMOD model**, select the appropriate AERMOD output file. [cite: 45]
    * [cite_start]Click the "Load/Simulate" button to process the dispersion. [cite: 48]
5.  [cite_start]**Step 4: Plot and Export Results.** [cite: 50]
    * [cite_start]Use the "What to plot" menu to choose the data you wish to visualize. [cite: 50]
    * Click the "Plot" button to generate the figure in the canvas. [cite_start]You can customize the plot using the toolbar above the canvas. [cite: 51, 54]
    * [cite_start]Click the "Export" button to save the plotted data as a `.csv` file in the `output/ExportData/` folder. [cite: 53]

***

## Model Configuration

### Operation Timeline

You can define the sequence and duration of operations in two ways:

* [cite_start]**Using a Real Timeline**: If you have operational logs, you can format them in an Excel (`.xlsx`) file. [cite: 56] [cite_start]The file should specify the start and end times for the operations listed in Table D1 of the Appendix. [cite: 56] [cite_start]Place the completed file in the `input/RealLogFiles/` directory. [cite: 58]
* [cite_start]**Simulating a Timeline**: If real logs are unavailable, you can use the built-in Mechanistic Air Emissions Simulator (MAES) to generate timelines. [cite: 63, 64] [cite_start]This feature uses a Monte Carlo simulation based on statistical distributions from real-world operations in the DJ Basin. [cite: 64, 65]
    * [cite_start]To generate a new set of timelines, select "Generate new," choose a duration file, and set the number of wells, number of runs, and a start time. [cite: 68, 70, 72, 73, 74]
    * [cite_start]To use a previously generated set, select "Use existing" and load the desired ensemble. [cite: 79, 80]

### Emission Rates

[cite_start]The model includes three pre-packaged emission rate datasets: [cite: 86]
* [cite_start]`DJ_Basin_2019_2023_Zhang_et_al_2025.xlsx`: Derived from observations in Broomfield, CO between 2019 and 2023. [cite: 86]
* [cite_start]`DJ_Piceance_Basin_2013_2016_Hecobian_et_al_2019.xlsx`: Derived from tracer ratio experiments in the DJ and Piceance basins. [cite: 87]
* [cite_start]`EPA_Oil_and_Gas_Tool_2020.xlsx`: Derived from the 2020 EPA Nonpoint Oil and Gas Emissions Estimation Tool. [cite: 88]

[cite_start]Users can also create their own emission rate files by following the format of the provided spreadsheets and adding them to the `input/EmissionFiles/` folder. [cite: 93, 94]

### Dispersion Models

The model can be coupled with two types of atmospheric dispersion models:

* [cite_start]**Gaussian Plume Model**: This model calculates pollutant concentration based on the emission rate, wind speed, and stability class. [cite: 98] [cite_start]The model provides six pre-defined sets of meteorological conditions (e.g., "Moderate wind, clear sky") or allows the user to define custom parameters in the advanced settings. [cite: 104, 105, 108]
* [cite_start]**AERMOD Model**: The GUI can directly read and use the output from previously run AERMOD simulations. [cite: 112] [cite_start]Place the AERMOD output files in the `input/DispersionFiles/` directory to make them accessible in the program. [cite: 112]

***

## Citing This Work

Please cite the following publications when using the TRACER model or its results:

* For the TRACER model application and VOC emissions from unconventional oil and gas operations:
    > Zhang, W., Pan, D., Ku, I.-T., Pierce, J., & Collett, J. J. (in preparation). [cite_start]Using Ambient Concentration Measurements to Quantify Volatile Organic Compound Emissions from Unconventional Oil and Gas Operations. [cite: 125, 126]

* For the underlying Mechanistic Air Emissions Simulator (MAES) structure:
    > Allen, D. T., Cardoso-Saldaña, F. J., Kimura, Y., Chen, Q., Xiang, Z., Zimmerle, D., Bell, C., Lute, C., Duggan, J., & Harrison, M. (2022). A Methane Emission Estimation Tool (MEET) for predictions of emissions from upstream oil and gas well sites with fine scale temporal and spatial resolution: Model structure and applications. [cite_start]*Science of The Total Environment*, *829*, 154277. [cite: 118, 119, 120]

## References

* EPA. (2020). [cite_start]*2020 EPA Nonpoint Oil and Gas Emissions Estimation Tool*. [cite: 121]
* Hanna, S. (1982). *Handbook on Atmospheric Diffusion*. [cite_start]Department of Energy. [cite: 122]
* Hecobian, A., Clements, A. L., Shonkwiler, K. B., Zhou, Y., MacDonald, L. P., Hilliard, N., Wells, B. L., Bibeau, B., Ham, J. M., & Pierce, J. R. (2019). Air toxics and other volatile organic compound emissions from unconventional oil and gas development. [cite_start]*Environmental Science & Technology Letters*, *6*(12), 720-726. [cite: 123, 124]
