# ECG classification
depository for deep learning course project
---------------------------------------------------------------------
![ECG gif](https://user-images.githubusercontent.com/119232867/211278114-10f78482-a06a-4384-8c6d-e086eec0d4fe.gif)

## Datasets
### Content:
Arrhythmia Dataset
- Number of Samples: 109446
- train / test: 80% / 20%
- Number of Categories: 5
- Sampling Frequency: 125Hz
- Data Source: Physionet's MIT-BIH Arrhythmia Dataset
- Classes: ['N': 0, 'S': 1, 'V': 2, 'F': 3, 'Q': 4]
- Classes proportion: [
- Dataset link : https://www.kaggle.com/shayanfazeli/heartbeat

MI (myocardial infarction) Dataset
- Number of Samples: 14552
- train / test: 
- Number of Categories: 2
- Sampling Frequency: 125Hz
- Data Source: PTB Diagnostic ECG Database
- Classes: ['normal': 0, 'abnormal': 1]
- Classes proportion: [0.28, 0.72]
- Dataset link : https://www.kaggle.com/shayanfazeli/heartbeat

### Preproccessing:

![image](https://user-images.githubusercontent.com/119232867/211274522-381393e4-10b3-49b1-8625-6eece113a67f.png)

- Sampled ECG heartbeat preproccessed by this scheme:
  - sa 
