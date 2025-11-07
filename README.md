# Trend-Aware Neural Networks for Climate Forecasting

This repository contains the implementation of the GRU and TCN models with composite loss function for weather forecasting presented in:

> **Improving Forecasts of Climatic Variables with Noise or Sharp Transitions through Trend-Aware Neural Networks**
> 
> Maira Aracne, Luciano Caroprese, Camilla Lops, Tommaso Ruga, Ester Zumpano, Sergio Montelpare
> 

## Overview

The repository provides Google Colab notebooks implementing GRU and TCN models with a novel composite loss function that combines point-wise accuracy with trend awareness through moving averages.

## What This Repository Provides

-  Complete code
-  Model architectures (GRU and TCN)
-  Composite loss function implementation
-  Hyperparameters used in the paper

The repository doesn't provide the datasets described in the paper - see Data Availability. Researchers can train models on their own meteorological data using this code.

## Requirements

- Python 3.11.11
- PyTorch 2.5.1+cu121
- CUDA-compatible GPU 
- Google Drive account

See `requirements.txt` for complete dependencies.

## Repository Structure
```
├── notebooks/
│   ├── GRU_solarStation.ipynb    # GRU model for solar stations
│   ├── TCN_solarStation.ipynb    # TCN model for solar stations
│   ├── GRU_windStation.ipynb     # GRU model for wind station
│   └── TCN_windStation.ipynb     # TCN model for wind station
├── requirements.txt
├── LICENSE
└── README.md
```


### Setup

1. Upload the desired notebook to Google Colab

2. Mount your Google Drive when prompted:
```python
   from google.colab import drive
   drive.mount('/content/drive')
```

3. Ensure your data follows the required structure in Google Drive:

   **For solar station notebooks:**
```
   MyDrive/Colab Notebooks/datasets/energy/
   ├── dataset_0_look_forward_days_1.xlsx
   ├── dataset_0_look_forward_days_2.xlsx
   ├── dataset_0_look_forward_days_3.xlsx
   ├── dataset_1_look_forward_days_1.xlsx
   ├── dataset_1_look_forward_days_2.xlsx
   ├── dataset_1_look_forward_days_3.xlsx
   └── results/  (output directory)
```

   **For wind station notebooks:**
```
   MyDrive/Colab Notebooks/datasets/energy/
   ├── dataset_0_look_forward_days_1.xlsx
   ├── dataset_0_look_forward_days_2.xlsx
   ├── dataset_0_look_forward_days_3.xlsx
   └── results/  (output directory)
```

4. Run all cells in the notebook

### Notebooks Description

- **GRU_solarStation.ipynb / TCN_solarStation.ipynb**: 
  - Forecasts GHI, temperature, atmospheric pressure and relative humidity
  - Uses data from Casaccia (dataset_0) and Ottana (dataset_1) meteorological stations
  - 3-day forecast horizon

- **GRU_windStation.ipynb / TCN_windStation.ipynb**:
  - Forecasts wind speed and direction
  - Uses data from Site 3 (dataset_0) and wind station
  - 3-day forecast horizon

 **Note 1:** The paper focuses on 3-day forecasts. The code can also produce 1-day and 2-day forecasts for comparison purposes.
 **Note 2:** Change the value of the hyperparameter α ∈ [0,1] to test the standard/point-wise loss (α = 0) and composite loss (0 < α < 1).

## Key Features

- Composite loss function balancing point-wise accuracy with temporal coherence
- Trend-aware component using moving averages
- Dual architecture implementations (GRU and TCN)
- Real-world validation on three Italian meteorological sites

## Data Availability

Due to privacy and data sharing agreements, the datasets cannot be publicly distributed. The code is provided for transparency and reproducibility. Researchers with similar meteorological datasets can adapt this code for their own data.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions regarding the code or methodology:
- Luciano Caroprese: luciano.caroprese@unich.it
- Maira Aracne: m.aracne@unidav.it
