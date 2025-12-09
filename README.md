# LoRaWAN Indoor Localization Pipeline

Tools for turning raw multi-gateway LoRaWAN RSSI measurements into clean, modeling-ready datasets for indoor localization. The workflow covers ingestion, timestamp normalization, uplink-level deduplication, anomaly detection/removal, signal smoothing (Kalman filtering), feature engineering, and leakage-safe time splits for training and evaluation. A baseline random forest model and its trained weights are included for reference.

## What’s Inside
- Data cleaning and validation of multi-gateway uplinks (time ordering, deduplication, gateway/device integrity checks).
- Anomaly handling with statistical and model-based filters to drop corrupted RSSI samples.
- Signal smoothing with Kalman filtering to reduce measurement noise before modeling.
- Time-aware, leakage-safe train/test partitioning and time-series cross-validation folds.
- Baseline ML example (random forest) plus a saved model artifact.

## Getting Started
1) `pip install -r requirements.txt`
2) Place your raw measurement data alongside the project files (update paths in the workflow where needed).
3) Run the workflow end-to-end to regenerate cleaned splits and model-ready features.

## Notes
- Train/test splits keep all receptions from the same uplink together to avoid leakage.
- Gateway identifiers are preserved for per-gateway bias handling and encoding.
- If gateway RSSI bias is suspected, calibrate per gateway before training.
