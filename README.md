# ECG classification
depository for deep learning course project
---------------------------------------------------------------------
![ECG gif](https://user-images.githubusercontent.com/119232867/211278114-10f78482-a06a-4384-8c6d-e086eec0d4fe.gif)

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
- train / test: 
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

