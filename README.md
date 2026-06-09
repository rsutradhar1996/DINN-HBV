# DINN-HBV

# Disease-Informed Neural Networks for Parameter Estimation of HBV Infection Model

This repository contains Jupyter notebook codes for parameter estimation of a hepatitis B virus (HBV) infection dynamics model using Disease-Informed Neural Networks (DINNs).

The main objective of these codes is to estimate unknown biological parameters of the HBV model by combining simulated data with the governing differential equations through a neural network based inverse modeling framework. The schematic diagram of DINNs is shown below.

## Schematic Representation of the DINNs Framework 
![Schematic of DINNs](Parameter%20estimation%20codes%20using%20DINNs/Figures/Schematic%20of%20DINNs.jpg)

## Overview of the Method

In the DINNs framework, the neural network is trained to approximate the state variables of the HBV infection model. The unknown model parameters are treated as trainable quantities and are estimated during the optimization process.

The total loss function contains two main parts:

1. **Data loss**, which measures the mismatch between the simulated data and the DINNs predictions.
2. **Residual loss**, which measures how well the DINNs predictions satisfy the governing HBV differential equations.

Thus, the method uses both data information and model-equation information to estimate the unknown parameters.

## General Structure of Each Notebook

Each notebook generally follows the steps below:

1. Import the required Python libraries.
2. Generate or load the synthetic HBV dataset.
3. Define the DINNs architecture.
4. Initialize the unknown parameters and neural network weights.
5. Train the DINNs model using the combined data and residual loss.
6. Print the final estimated parameter values.
7. Generate model predictions.
8. Plot the DINNs predictions together with the reference/simulated data.
9. Compute relative root mean squared error measures denoted as RRMSE.

For the experimental-noise notebooks, an additional step is included to add Gaussian noise to the clean synthetic data before training.


## Mathematical Model Used in the Codes

The data used in these notebooks are generated from the following HBV infection dynamics model:

$$
\frac{dX}{dt}=\lambda-\mu X-kVX,
$$

$$
\frac{dY}{dt}=kVX-\delta Y,
$$

$$
\frac{dD}{dt}=aY+\gamma(1-\alpha)D-\alpha\beta D-\delta D,
$$

$$
\frac{dV}{dt}=\alpha\beta D-cV.
$$

Here, $X$, $Y$, $D$, and $V$ represent uninfected hepatocytes, infected hepatocytes, intracellular capsids, and free virions, respectively. Based on the identifiability results, the parameter $\alpha$ is kept fixed, while the remaining eight model parameters,

$$
\lambda,\ \mu,\ k,\ a,\ \beta,\ \delta,\ c,\ \gamma,
$$

are estimated using the DINNs framework.



## Required Python Version and Libraries

The provided notebooks have been run using the following Python version:

```text
Python version: 3.12.13
```

The required Python libraries and the versions used are:

```text
NumPy version      : 2.0.2
Pandas version     : 2.2.2
Matplotlib version : 3.10.0
SciPy version      : 1.16.3
PyTorch version    : 2.11.0+cpu
```


To install the required packages, use:

```bash
pip install numpy pandas matplotlib scipy torch
```

For version-specific installation, use:

```bash
pip install numpy==2.0.2 pandas==2.2.2 matplotlib==3.10.0 scipy==1.16.3 torch
```

## System Configuration Used

The provided notebooks have been run on a Windows system equipped with an Intel(R) Core(TM) i5-10210U CPU @ 1.60 GHz, 8 GB RAM, and hard disk drive (HDD) storage.


## How to Run the Codes

The provided codes can be run using Jupyter Notebook or JupyterLab.

### Running in Jupyter Notebook or JupyterLab

First, clone the repository:

```bash
git clone https://github.com/rsutradhar1996/DINN-HBV.git
```

Then move into the repository folder:

```bash
cd DINN-HBV
```

Install the required Python libraries:

```bash
pip install numpy pandas matplotlib scipy torch
```

Open Jupyter Notebook or JupyterLab:

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

Then open the required `.ipynb` file and run all cells sequentially from top to bottom.


## Main Outputs

The notebooks generate the following outputs:

- Estimated HBV model parameters.
- DINNs-predicted state variables.
- Comparison plots between simulated data and DINNs predictions.
- Loss history during training.
- Relative root mean squared error denoted as RRMSE.
- Computation time, where included.

## Notes

1. Each notebook is independent and corresponds to a specific numerical experiment. The notebooks should be run cell by cell in the given order. The training cell usually takes the longest time because the neural network weights and the unknown biological parameters are optimized simultaneously.

2. The training time may vary depending on the number of iterations, neural network architecture, learning rate, and system configuration.





