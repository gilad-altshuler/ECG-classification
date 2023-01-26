# ECG classification
Depository for deep learning course project
---------------------------------------------------------------------
![ECG gif](https://user-images.githubusercontent.com/119232867/211278114-10f78482-a06a-4384-8c6d-e086eec0d4fe.gif)
![R](https://user-images.githubusercontent.com/119232867/212991176-401d20e3-28e6-45c7-9ada-a9ea450ec73b.gif)

- [ECG-classification](#ECG-classification)
  * [About](#About)
  * [Datasets](#Datasets) 
  * [Proposed CNN Model](#proposed-cnn-model)
  * [Results](#results)
  * [Run](#Run)
  * [Files in The Repository](#files-in-the-repository)
  * [Acknowledgement](#Acknowledgement)

## About

Electrocardiogram (ECG) can be reliably used as a measure to monitor the functionality of the cardiovascular system.
In this project, we analyze the method based on deep convolutional neural networks for the
classification of heartbeats which is able to accurately classify
five different arrhythmias in accordance with the AAMI EC57
standard and a method for transferring the knowledge acquired on this task to the myocardial infarction (MI) classification task.

This project goals are 3:
- Design simple yet accurate model to the prediction task
- Try to transfer the learnt model for Arrhythmia task for MI task
- Comprehend the CNN layers and their meanings

## Datasets
### Content:
Arrhythmia Dataset
- Number of Samples: 109444
- train / test: 80% / 20%
- Number of Categories: 5
- Sampling Frequency: 125Hz
- Data Source: Physionet's MIT-BIH Arrhythmia Dataset
- Classes: ['N': 0, 'S': 1, 'V': 2, 'F': 3, 'Q': 4]
- Classes proportion: [0.83, 0.03, 0.07, 0.01, 0.07]
- Dataset link : https://www.kaggle.com/shayanfazeli/heartbeat

MI (myocardial infarction) Dataset
- Number of Samples: 14550
- train / test: 80% / 20%
- Number of Categories: 2
- Sampling Frequency: 125Hz
- Data Source: PTB Diagnostic ECG Database
- Classes: ['normal': 0, 'abnormal': 1]
- Classes proportion: [0.28, 0.72]
- Dataset link : https://www.kaggle.com/shayanfazeli/heartbeat

### Preprocessing:

![image](https://user-images.githubusercontent.com/119232867/211274522-381393e4-10b3-49b1-8625-6eece113a67f.png)

- Sampled ECG heartbeat preproccessed by this scheme: 
  - Splitting the continuous ECG signal to 10s windows and select a 10s window from an ECG signal.
  - Normalizing the amplitude values to the range of between zero and one.
  - Finding the set of all local maximums based on zero crossings of the first derivative.
  - Finding the set of ECG R-peak candidates by applying a threshold of 0:9 on the normalized value of the local maximums.
  - Finding the median of R-R time intervals as the nominal heartbeat period of that window (T).
  - For each R-peak, selecting a signal part with the length equal to 1.2T.
  - Padding each selected part with zeros to make its length equal to a predefined fixed length.
  
- After preprocessing

![image](https://user-images.githubusercontent.com/119232867/211292748-81743bde-22b8-4bdf-98d0-14be4dd28332.png)

- 5 example from dataset, and their labels

<img width="706" alt="examples" src="https://user-images.githubusercontent.com/119232867/212958647-b49dc5a8-3fe2-4d20-a5c5-e72ac935c979.PNG">

## Proposed CNN model

we wanted the model to be simple, yet accurate, and genaralizable enough to be able to transfer between the 2 datasets. We chose the CNN model:

![image](https://user-images.githubusercontent.com/119232867/214833897-5aa8d325-8a7e-4cfc-b2e2-12929f08fe4b.png)

with 4 convolution layers and 4 fully connected layers.

## Results

- Training the model on datasets:

![image](https://user-images.githubusercontent.com/119232867/214838845-87afa5a2-f984-40ba-8968-9d0c442d62c1.png)
![image](https://user-images.githubusercontent.com/119232867/214839242-8b55726f-911e-4430-a663-618af4546746.png)

comparing results:

![image](https://user-images.githubusercontent.com/119232867/214840428-75e101d6-cfa2-4f31-a6d4-499c3281efab.png)

- Transferring the Arrhythmia task model to MI task, with each number of trained layers:

![image](https://user-images.githubusercontent.com/119232867/214840015-992a1908-5faa-489e-adcd-f6f3d9385c20.png)
![image](https://user-images.githubusercontent.com/119232867/214840102-fd531af0-5a6d-40d2-8dd2-50a4a0fb3691.png)

- input through layers example:

![image](https://user-images.githubusercontent.com/119232867/214840246-6acd8277-08ed-49f1-b28e-6fdc362eb103.png)



## Run

All the codelines needed can be found in ECG_classification.ipynb.
To be able to run the dataset one need to:

(1) Download manually the datasets from https://www.kaggle.com/shayanfazeli/heartbeat.

(2) Uploading to your drive to the directory /content/drive/MyDrive/Deep_Learning/datasets (default in code)

(3) One can choose other directory in drive, but change the link in the code.*

*the last directory must be called "datasets"

This will allow the rest of code to use the heartbeats datasets.

## Files in The Repository

|File name         | Purpsoe |
|----------------------|------|
|`README.md`| readme|
|`ECG_classification.ipynb`| code section for the model and trials|
|`submissions`| directory for project submitted files|

## Acknowledgement
- ECG Heartbeat Classification: A Deep Transferable Representation, Kachuee et Al. 2018
