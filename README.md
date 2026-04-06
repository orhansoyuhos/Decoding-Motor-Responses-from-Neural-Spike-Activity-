# Decoding motor responses from neural spike activity

The primary objective of this project was to decode and understand the motor responses of rats during tilting events, leveraging machine learning tools to analyze neural spike times from the motor cortex. The project involved organizing recorded spike time data and generating peri-event rasters and histograms to visually represent neural activity. The key tool developed was a Peri-Stimulus Time Histogram (PSTH) classifier, designed to categorize different motor responses to clockwise and counterclockwise tilts. To further refine classification performance, Principal Component Analysis (PCA) was integrated with the PSTH classifier. The methodologies employed were adapted from Foffani and Moxon (2004).

## Requirements

- Python 3.x
- numpy
- scipy
- matplotlib
- scikit-learn
- seaborn
- pandas

## Data

Each week's notebook loads a corresponding JSON data file (e.g. `hw1.json`, `hw3.json`, `hw4.json`) containing `events` and `neurons` keys with spike time arrays. These files are not included in the repository due to their size and must be obtained separately.

## Weekly Breakdown

**Week 1 — Raster Plots, PSTH & Receptive Field Analysis**
- Computes spike times relative to stimulus onset for 2 neurons (`sig003a`, `sig016b`) across 2 events
- Generates raster plots and normalized PSTHs at 1ms, 5ms, 10ms, and 20ms bin sizes
- Receptive field analysis: background firing rate, threshold, response latency, peak firing rate, and response magnitude

**Week 2 — Entropy & Mutual Information**
- Calculates spike train entropy, mutual information between two neurons, and joint mutual information for multiple stimuli

**Week 3 — PSTH Classifier**
- Builds a nearest-template classifier using leave-one-out cross-validation across 29 neurons and 4 event types
- Classifies each trial by Euclidean distance to the mean PSTH template per event
- Best accuracy: **79%** at 50ms bin size (mutual information: 1.05 bits)

**Week 4 — PCA + PSTH Classifier**
- Constructs a Multineuronal Time Series (MNTS) from all trials and neurons, z-scores it, and applies PCA
- Projects data onto the top 4 principal components and runs the same leave-one-out classifier
- Accuracy: **54%** — raw PSTH features outperformed PCA-compressed features for this dataset

## Reference

Foffani, G., & Moxon, K. A. (2004). PSTH-based classification of sensory stimuli using ensembles of single neurons. *Journal of Neuroscience Methods, 135*(1-2), 107–120. https://doi.org/10.1016/j.jneumeth.2003.12.011

![bim280](https://github.com/orhansoyuhos/Decoding-Motor-Responses-from-Neural-Spike-Activity-/assets/44211738/5a341266-88c3-40fa-94b9-e5990758f311)
