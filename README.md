# SIENNA

## Abstract
BACKGROUND: Training of Artificial intelligence (AI) platforms for clinical imaging diagnostics and error reduction is typically data heavy. This limits applications where data is scarce and blurs computer vision model weaknesses. In magnetic resonance (MR) images, the identification and multiclassification of disease features typically uses tens of millions of spatial parameters that are analyzed over 30-50 convolutional neural networks (CNNs).  Model size does not correlate with ability to generalize to new data, requires higher compute energy to retrain, and these multi-layered architectures complicate identifying improvements to their diagnostic functionality.

PURPOSE:  Development of compact deep learning AI architectures and workflows that require few CNNs, minimal image data, and require only a few hundred thousand high quality parameters will expand clinical applications. Foremost, these data- and task-centric AI models push the boundaries of data optimization, inform on deep learning architectures and fill a gap to provide tools for rapid disease subtyping and rare disease analysis when data availability is limited. 

MATERIALS and METHODS: A focus on MRI brain tumor retrospective diagnostic analysis enables access to a variety of datasets and comparisons with multiple published computer vision AI architectures.  SIENNA is a compact AI model trained on a new non-processed DICOM FLAIR axial image dataset consisting of only 17 total patients for glioblastoma and metastasized tumors under IRB protocol, representing 387 total tumor type and non-tumor 2D scans distributed into 60-20-20 training-validation-testing sets. Adversarial training was implemented to challenge the model and avoid shortcut learning. Class size balance and augmentation by SMOTE ensured at least 108 minimal images per category. Training applied 100-run sampling and retraining on error prone challenging images. Final optimization of competitive performance was tuned by hyperparameters and via use of a new region-aware intensity algorithm for MRI data normalization before analysis.

RESULTS:  SIENNA comparative performance was validated against four representative state of the art AI computer vision models of various architectures and parameter sizes across four analyzed datasets, including multiple MRI machines, 1.5 and 3.0 Tesla energies, and multiple tumor types and modality. SIENNA consistently achieved highest performance metrics for accuracy, maintaining low standard of deviation and strong positive-negative case discrimination by area under the receiver operating characteristic curve (AUROC) values versus million parameter models. 

CONCLUSION:  SIENNA’s compact deep learning AI architecture is the smallest model to date that excels in performance across a range of tumor diagnostic use cases. SIENNA enables new flexible opportunities for initiating small dataset clinical collaborations towards rapid disease typing, subtyping or rare disease analysis enabled in a minimal parameter, easily retrained footprint.

This repository offers the pre-trained weights of SIENNA, specifically trained on clinical data. The python script retrieves sequentially pre-trimmed MRI scans from designated data paths, applies "Pixel Redistribution Enhancement, Masking, Optimization" (PREMO) for equalization, and predicts z-slices to be GBM, MET or tumor-free using SIENNA pre-trained architecture. The patient-specific results are then presented using metrics that quantify SIENNA's performance, such as Accuracy and F1-Score.
## Hardware Requirements

The training process was conducted on a Microsoft Windows 11 workstation equipped with an Intel(R) Core (TM) i7-10750H six-core CPU, 16 GB of system RAM, and a single NVIDIA GTX 1650 GPU boasting 4 GB of GPU RAM.

## Python Environment

Python libraries and modules required are listed in requirements.txt.

<pre>pip install -r requirements.txt </pre>


## SIENNA Architecture 

### Source code for testing SIENNA:

1. SIENNA pre-trained.h5: Pre-trained weights of SIENNA on clinical data. 
2. patient_wise_analysis.py: Reads MRI images, applies preprocessing (including the patented PREMO method), loads a pre-trained model, and evaluates its performance on the test data.
