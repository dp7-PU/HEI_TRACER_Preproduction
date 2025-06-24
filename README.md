# TRACER Pre-Production Model

## About The Project

The TRAcking Community Exposures and Releases (TRACER) model is designed to simulate emissions of volatile organic compounds (VOCs) from unconventional oil and gas development (UOGD). Current emission models often do not accurately reflect recent UOGD practices, and TRACER was developed to address this gap.

Based on the Mechanistic Air Emissions Simulator (MAES), the TRACER model can simulate emissions for over 50 VOC species, including alkanes, alkenes, and aromatics. It covers complex pre-production activities like drilling, hydraulic fracturing, mill-out, and flowback with detailed time resolution.

The model is a versatile tool for applications such as:
* Compiling emission inventories
* Assessing health impacts
* Evaluating air quality

To make it accessible for policymaking and environmental health research, the model includes a Graphical User Interface (GUI). The GUI is a standalone executable for Windows, built using Python 3.

***

## Key Features

* **Detailed Timeline Simulation**: Simulates high-resolution operational timelines for pre-production activities at UOGD sites. You can use real, logged data or generate simulated timelines using a Monte Carlo approach based on field data.
* **Comprehensive VOC Modeling**: Models emissions for more than 50 different VOC species.
* **Flexible Emission Rates**: Incorporates several adjustable emission rate datasets from recent field studies and EPA tools. Users can also provide their own emission data.
* **Atmospheric Dispersion**: Integrates two types of dispersion models:
    * A **Gaussian plume model** with pre-defined and customizable meteorological conditions.
    * Integration with pre-computed **AERMOD** simulation outputs.
* **Data Visualization and Export**: Allows users to plot results directly in the interface and export data to `.csv` files for further analysis.

***

## Getting Started

### Prerequisites

The TRACER Pre-Production Module is a standalone executable file designed for Windows platforms.

### Installation

1.  Download the repository as a ZIP file. (Note: The final version will be archived on the Collett Research Group website or a dedicated GitHub repository.)
2.  Extract all the contents of the ZIP file into a single folder.
3.  Ensure the `config`, `input`, and `output` folders are located in the same directory as the main executable.

***

## Quick Start Guide

1.  Run the `HEI_GUI.exe` application to launch the model. A graphical interface will appear after a few seconds.
2.  **Step 1: Load Operation Timeline.**
    * Use the "Timeline source" dropdown to load a timeline from a real operational log file.
    * Alternatively, go to the "Advanced Modes" to simulate an ensemble of timelines.
3.  **Step 2: Choose Emission Factors.**
    * Select a pre-defined set of emission factors from the "Emission source" dropdown menu and click "Load".
    * Use the "Species" dropdown menu to select the specific pollutant you want to model.
4.  **Step 3: Load or Simulate Atmospheric Dispersion.**
    * Select a dispersion model using the "Dispersion configuration" dropdown.
    * If using the **Gaussian plume model**, select the atmospheric conditions and enter the downwind distance from the source.
    * If using the **AERMOD model**, select the appropriate AERMOD output file.
    * Click the "Load/Simulate" button to process the dispersion.
5.  **Step 4: Plot and Export Results.**
    * Use the "What to plot" menu to choose the data you wish to visualize.
    * Click the "Plot" button to generate the figure in the canvas. You can customize the plot using the toolbar above the canvas.
    * Click the "Export" button to save the plotted data as a `.csv` file in the `output/ExportData/` folder.

***

## Model Configuration

### Operation Timeline

You can define the sequence and duration of operations in two ways:

* **Using a Real Timeline**: If you have operational logs, you can format them in an Excel (`.xlsx`) file. The file should specify the start and end times for the operations listed in Table D1 of the Appendix. Place the completed file in the `input/RealLogFiles/` directory.
* **Simulating a Timeline**: If real logs are unavailable, you can use the built-in Mechanistic Air Emissions Simulator (MAES) to generate timelines. This feature uses a Monte Carlo simulation based on statistical distributions from real-world operations in the DJ Basin.
    * To generate a new set of timelines, select "Generate new," choose a duration file, and set the number of wells, number of runs, and a start time.
    * To use a previously generated set, select "Use existing" and load the desired ensemble.

### Emission Rates

The model includes three pre-packaged emission rate datasets:
* `DJ_Basin_2019_2023_Zhang_et_al_2025.xlsx`: Derived from observations in Broomfield, CO between 2019 and 2023.
* `DJ_Piceance_Basin_2013_2016_Hecobian_et_al_2019.xlsx`: Derived from tracer ratio experiments in the DJ and Piceance basins.
* `EPA_Oil_and_Gas_Tool_2020.xlsx`: Derived from the 2020 EPA Nonpoint Oil and Gas Emissions Estimation Tool.

Users can also create their own emission rate files by following the format of the provided spreadsheets and adding them to the `input/EmissionFiles/` folder.

### Dispersion Models

The model can be coupled with two types of atmospheric dispersion models:

* **Gaussian Plume Model**: This model calculates pollutant concentration based on the emission rate, wind speed, and stability class. The model provides six pre-defined sets of meteorological conditions (e.g., "Moderate wind, clear sky") or allows the user to define custom parameters in the advanced settings.
* **AERMOD Model**: The GUI can directly read and use the output from previously run AERMOD simulations. Place the AERMOD output files in the `input/DispersionFiles/` directory to make them accessible in the program.

***

## Citing This Work

Please cite the following publications when using the TRACER model or its results:

* For the TRACER model application and VOC emissions from unconventional oil and gas operations:
    > Zhang, W., Pan, D., Ku, I.-T., Pierce, J., & Collett, J. J. (in preparation). Using Ambient Concentration Measurements to Quantify Volatile Organic Compound Emissions from Unconventional Oil and Gas Operations.

* For the underlying Mechanistic Air Emissions Simulator (MAES) structure:
    > Allen, D. T., Cardoso-Saldaña, F. J., Kimura, Y., Chen, Q., Xiang, Z., Zimmerle, D., Bell, C., Lute, C., Duggan, J., & Harrison, M. (2022). A Methane Emission Estimation Tool (MEET) for predictions of emissions from upstream oil and gas well sites with fine scale temporal and spatial resolution: Model structure and applications. *Science of The Total Environment*, *829*, 154277.

## References

* EPA. (2020). *2020 EPA Nonpoint Oil and Gas Emissions Estimation Tool*.
* Hanna, S. (1982). *Handbook on Atmospheric Diffusion*. Department of Energy.
* Hecobian, A., Clements, A. L., Shonkwiler, K. B., Zhou, Y., MacDonald, L. P., Hilliard, N., Wells, B. L., Bibeau, B., Ham, J. M., & Pierce, J. R. (2019). Air toxics and other volatile organic compound emissions from unconventional oil and gas development. *Environmental Science & Technology Letters*, *6*(12), 720-726.
