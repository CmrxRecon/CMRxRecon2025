# CMRxRecon2025

## About
**Welcome to the Cardiac MRI Reconstruction Challenge 2025 (CMRxRecon2025)！**  
The CMRxRecon2025 (Towards Foundation Model) Challenge is a part of the 28th International Conference on Medical Image Computing and Computer Assisted Intervention, MICCAI 2025, which will be held from September 23rd to 27th 2025 in Daejeon, Republic of Korea.


[Website](https://cmrxrecon.github.io/2025) |
[Dataset](https://www.synapse.org/Synapse:syn64952554/datasets/) |
[GitHub](https://github.com/CmrxRecon/CMRxRecon2025/) |
[Publications](#Publication-references)

## Motivation
The objective of establishing the CMRx series challenges is to provide a benchmark that enables the research community to contribute to the work of accelerated CMR imaging with universal approaches that allow more diverse applications and better performance in real-world deployment in various environments. The previous CMRxRecon2023 and CMRxRecon2024 datasets did not cover multiple centers, multiple vendors, and multiple diseases. Therefore, this year we aim to fill these gaps and make an important leap towards real-world clinical scenarios.

## Background
Cardiac MRI (CMR) has become an essential tool for diagnosing and evaluating cardiovascular diseases, offering multi-parametric, high-resolution anatomical and functional data. CMR reconstruction from highly under-sampled k-space data has gained significant attention in recent research. Numerous AI-based image reconstruction algorithms have shown potential in improving imaging performance and patient experience in recovering high-quality images from aggressively undersampled k-space measurements. However, the complexity and diversity of CMR scans in real-world applications, involving various image contrasts, sampling trajectories, equipment vendors, anatomical structures, and disease types, present a great challenge for existing AI-based reconstruction methods, which are usually developed for only one or a few specific scanning settings. In practice, there are often inevitable distribution mismatches between the training data and target data, due to the diversities listed above. **Therefore, building and validating universal and robust reconstruction models for handling these diversities remains a critical technical challenge for multi-parametric CMR imaging.**

![CMRxSeries](https://github.com/CmrxRecon/CMRxRecon2025/blob/main/CMRxSeries2025.png)

We aim to make an important leap towards real-world clinical scenarios by extending the challenge scope in two directions:
**1) To evaluate the robustness and generalization performance of reconstruction foundation models in more than 5 centers and 10 scanners, all those data are unseen during the training stage.**
**2) To evaluate the clinical performance of reconstruction foundation models under no less than 5 cardiovascular diseases (e.g., hypertrophic cardiomyopathy, dilated cardiomyopathy, myocardial infarction, coronary artery disease, arrhythmias), all those data are unseen during the training stage.**

This repository contains Matlab code for data loaders, undersampling functions, evaluation metrics, and reference implementations of simple baseline methods. It also contains implementations for methods in some of the publications of the CMRxRecon project.

## Challenge tasks
**The 'CMRxRecon2025' challenge includes two regular tasks (announced during MICCAI annual meeting) and two special tasks (announced during SCMR annual meeting). The tasks are awarded independently, so each team can choose to participate any one of them.** For each task, participants can submit one model each (which can be four different models, or they can submit just one model, but they must submit it separately for each task). Please note that for the four tasks, the training dataset we provide is the same; however, the validation and test datasets are different for each of the four tasks. 

**Our objective is to evaluate the model's generalization performance across diverse centers and scanners (Regular TASK 1), diseases (Tegular TASK 2), magnetic fields (Special TASK 1), and populations (Special TASK 2).**

![TaskText](https://github.com/CmrxRecon/CMRxRecon2025/blob/main/TaskText2025.png)

**Regular TASK 1: CMR reconstruction model for multi-center multi-vendor evaluation**

This task primarily focuses on addressing the issue of declining generalization performance between multiple centers. Participants are required to train the reconstruction model on the training dataset and achieve good multi-contrast cardiac image reconstruction results on the validation and test datasets. It is important to note that for this task, we will include data from two entirely new centers in the validation set (not present in the training set), and the test set will contain data from five entirely new centers (not present in the training set, including the two centers that appeared in the validation set).

**Regular TASK 2: CMR reconstruction model for multi-disease evaluation**

This task primarily focuses on evaluating the reliability of the model in applications involving different cardiovascular diseases. Participants are required to train the reconstruction model on the training dataset and achieve good performance in disease applications on the validation and test datasets. It is important to note that for this task, we will include data for two diseases that have not appeared in the training set in the validation set, and the test set will contain data for five diseases that have not appeared in the training set (including the two diseases that appeared in the validation set).
Please note that to ensure the model training process is not biased by the type of disease, we will not disclose the disease information for each data point in the training and validation dataset.

**Special TASK 1: CMR reconstruction model for 5T evaluation**

This task primarily focuses on addressing the issue of declining reconstruction generalization performance under different magnetic field strengths, especially those not included in the training data. Participants are required to train the reconstruction model on the training dataset (mainly consisting of 1.5T and 3.0T) and achieve good multi-contrast cardiac image reconstruction results on the validation and test datasets (5.0T).

**Special TASK 2: CMR reconstruction model for pediatric imaging evaluation**

This task primarily focuses on addressing application issues in pediatric cardiac imaging. Participants are required to train the reconstruction model on the training dataset (mainly consisting of adults over 20 years old) and achieve good multi-contrast cardiac image reconstruction results on the validation and test datasets (minors under 18 years old). Please note that to ensure the model training process is not biased by age information, we will not disclose the age of each data point in the training dataset.

![TaskImage](https://github.com/CmrxRecon/CMRxRecon2025/blob/main/TaskImage2025.png)

## Documentation

### The CMRxRecon2025 Dataset
A total of 600 volunteers are recruited for multi-protocal CMR imaging in different imaging centers. **The dataset includes multi-coil, multi-modality, multi-view k-space data from 5+ medical centers and 10+ MRI scanners from GE, Philips, Siemens, United Imaging. Their field strengths include 1.5T, 3.0T, and 5.0T (for special tasks). They also cover many different diseases, such as hypertrophic cardiomyopathy, dilated cardiomyopathy, myocardial infarction, coronary artery disease, and arrhythmias.**

**The released dataset includes 200 cases for training, 100 cases for validation, and 300 cases for test.**

Training cases including fully sampled k-space data and sampling trajectories will be provided in '.mat' format.

Validation cases include under-sampled k-space data, sampling trajectories, and autocalibration signals (ACS, 20 lines or 20x20 regions) with various acceleration factors in '.mat' format.

Test cases include fully sampled k-space data, undersampled k-space data, sampling trajectories, and autocalibration signals (ACS, 20 lines or 20x20 regions). Test cases will not be released before the challenge ends.

![DataImage](https://github.com/CmrxRecon/CMRxRecon2025/blob/main/DataImage.png)

## Package Structure
* `CMRxReconDemo`: contains parallel imaging reconstruction code
* `CMRxReconMaskGeneration`: contains code for varied undersampling mask generation in different tasks
* `Evaluation`: contains image quality evaluation code for validation and testing
* `Submission`: contains the structure for challenge submission

## Contact
The code is provided to support reproducible research. If the code is giving syntax error in your particular configuration or some files are missing then you may open an issue or email us at CMRxRecon@outlook.com

## Publication references
You are free to use and/or refer to the CMRxRecon challenge and datasets in your own research after the embargo period (Dec 2025), provided that you cite the following manuscripts: 

**Reference of the CMR imaging acquisition protocol: **
1.  Wang Z, Huang M, Shi Z, et al., Enabling ultra-fast cardiovascular imaging across heterogeneous clinical environments with a generalist foundation model and multimodal database. arXiv preprint arXiv:2512.21652, 2025.
2.	Wang C, Lyu J, Wang S, et al. CMRxRecon: A publicly available k-space dataset and benchmark to advance deep learning for cardiac MRI. Scientific Data, 2024, 11(1): 687.
3.	Wang Z, Wang F, Qin C, et al. CMRxRecon2024: A Multimodality, Multiview k-Space Dataset Boosting Universal Machine Learning for Accelerated Cardiac MRI. Radiology: Artificial Intelligence. 2025, 7(2): e240443.
4.	Lyu J, Qin C, Wang S, et al. The state-of-the-art in Cardiac MRI Reconstruction: Results of the CMRxRecon Challenge in MICCAI 2023. Medical Image Analysis. 2025. 101: 103485.
5.	Wang C, Li Y, Lv J, et al. Recommendation for Cardiac Magnetic Resonance Imaging-Based Phenotypic Study: Imaging Part. Phenomics. 2021, 1(4): 151-170. 
6.	Wang S, Qin C, Wang C, et al. The Extreme Cardiac MRI Analysis Challenge under Respiratory Motion (CMRxMotion). arXiv preprint arXiv:2210.06385, 2022.

**Reference for previously developed reconstruction algorithms: **
1.	Wang C, Jang J, Neisius U, et al. Black blood myocardial T2 mapping. Magnetic resonance in medicine. 2019, 81(1): 153-166. 
2.	Lyu J, Wang S, Tian Y, Zou J, Dong S, Wang C, Aviles-Rivero AI, Qin J. STADNet: Spatial-Temporal Attention-Guided Dual-Path Network for cardiac cine MRI super-resolution. Medical Image Analysis, 2024;94:103142.
3.	Lyu J, Li G, Wang C, et al. Region-focused multi-view transformer-based generative adversarial network for cardiac cine MRI reconstruction. Medical Image Analysis, 2023: 102760. 
4.	Lyu J, Tian Y, Cai Q, Wang C*, Qin J. Adaptive channel-modulated personalized federated learning for magnetic resonance image reconstruction. Computers in Biology and Medicine, 2023, 165: 107330.
5.	Qin C, Schlemper J, Caballero J, et al. Convolutional recurrent neural networks for dynamic MR image reconstruction. IEEE transactions on medical imaging, 2018, 38(1): 280-290. 
6.	Qin C, Duan J, Hammernik K, et al. Complementary time-frequency domain networks for dynamic parallel MR image reconstruction. Magnetic Resonance in Medicine, 2021, 86(6): 3274-3291. 
7.	Lyu J, Tian Y, Cai Q, et al. Adaptive channel-modulated personalized federated learning for magnetic resonance image reconstruction. Computers in Biology and Medicine, 2023, 165: 107330.
8.	Lyu J, Tong X, Wang C. Parallel Imaging With a Combination of SENSE and Generative Adversarial Networks (GAN). Quantitative Imaging in Medicine and Surgery. 2020, 10(12): 2260-2273. 
9.	Lyu J, Sui B, Wang C, et al. DuDoCAF: Dual-Domain Cross-Attention Fusion with Recurrent Transformer for Fast Multi-contrast MR Imaging. International Conference on Medical Image Computing and Computer-Assisted Intervention. Springer, Cham, 2022: 474-484.
10.	Ouyang C, Schlemper K, et al. Generalizing Deep Learning MRI Reconstruction across Different Domains, arXiv preprint arXiv: 1902.10815, 2019.
11.	Shangqi Gao, Hangqi Zhou, Yibo Gao, Xiahai Zhuang. BayeSeg: Bayesian Modeling for Medical Image Segmentation with Interpretable Generalizability. Medical Image Analysis Volume 89, 102889, 2023 (Elsevier-MedIA 1st Prize & MICCAl Best Paper Award 2023) 
