# Mini-Project for Fundamentals of Machine Learning Course
![background](./materials/ai_wp.jpg)
This repository contains the code and data for a mini-project on facial expression recognition using machine learning algorithms.

## 📑 Project Policy
- Team: group should consist of 3-4 students.

    |No.| Student Name    | Student ID |
    | --------| -------- | ------- |
    |1| Nguyễn Trung Đức | 21110269 |
    |2| Nguyễn Ngọc Huynh| 21110310 |
    |3| Lê Công Khánh    | 21110320 |
    |4|||

- The submission deadline is strict: **11:59 PM** on **June 22nd, 2024**. Commits pushed after this deadline will not be considered.

## 📄 Report
- The dataset is imbalanced: The least common label is 1 (Disgust) and the most common is 3 (Happy)

    ![](/materials/distribution.png)
- This imbalance led to the precision of class 3 in the confusion matrix having the highest score, while class 1 has the lowest score. This indicates that models is more biased towards class 3

    ![](/materials/confusion_matrix.png)
    *Confusion matrix of Random Forest model on the original dataset*
- The dimension of the images is large: (1 x 48 x 48 = 2304 pixels (features)). Therefore, dimension reduction is necessary to achieve faster training times. Models run on dimension-reduced dataset by PCA train faster than those using the original data
    - Because training took longer on Google Colab, we benchmarked on a machine with a 12 core, 24 thread, 3.9Hz CPU, for 3 models (KNN, Logistic Regression, Random Forest):
        | | Original Data    | PCA Data |
        | --------| -------- | ------- |
        |Training| $\approx$ 10 minutes | $\approx$ 2 minutes |
        |Parameters Tuning| $\approx$ 1 hour 10 minutes| $\approx$ 30 minutes |
        |Cross Validation| $\approx$ 30 minutes| $\approx$ 15 minutes |
    
- We also experimented with SVM for the dataset. Although it is slower than other algorithms, it gave slightly better results
- Besides that, we experimented with 2 CNN models: VGG and ResNet. We could train them to outperform 3 ML models we used, but due to time and resource limitations, we could not train for more epochs. So we just used the last layer in both the VGG and ResNet models to train for 2 epochs.

### 💪 Performance
Performance of models on test set:

|Model|Accuracy|Precision|Recall|F1|
|-----| ------ | ------- | ---- |--|
|KNN|0.34|0.36|0.34|0.33|
|Logistic Regression|0.35|0.33|0.35|0.34|
|Random Forest|0.47|0.49|0.47|0.45|
|VGG (2 epoch)|0.25| - | - | - |
|ResNet (2 epoch)|0.33| - | - | - |

=> The Random Forest model gave the best performance on different metrics among the others.

Other improvements:
- Oversampling and Undersampling to prevent imbalance
- Experimenting with other simple Deep Learning models and comparing them with more Machine Learning models

## 📦 Project Structure

The repository is organized into the following directories:

- **/data**: This directory contains the facial expression dataset. You'll need to download the dataset and place it here before running the notebooks. (Download link provided below)
- **/notebooks**: This directory contains the Jupyter notebook ```EDA.ipynb```. This notebook guides you through exploratory data analysis (EDA) and classification tasks.

## ⚙️ Usage

This project is designed to be completed in the following steps:

1. **Fork the Project**: Click on the ```Fork``` button on the top right corner of this repository, this will create a copy of the repository in your own GitHub account. Complete the table at the top by entering your team member names.

2. **Download the Dataset**: Download the facial expression dataset from the following [link](https://mega.nz/file/foM2wDaa#GPGyspdUB2WV-fATL-ZvYj3i4FqgbVKyct413gxg3rE) and place it in the **/data** directory:

3. **Complete the Tasks**: Open the ```notebooks/EDA.ipynb``` notebook in your Jupyter Notebook environment. The notebook is designed to guide you through various tasks, including:
    
    1. Prerequisite
    2. Principle Component Analysis
    3. Image Classification
    4. Evaluating Classification Performance 

    Make sure to run all the code cells in the ```EDA.ipynb``` notebook and ensure they produce output before committing and pushing your changes.

5. **Commit and Push Your Changes**: Once you've completed the tasks outlined in the notebook, commit your changes to your local repository and push them to your forked repository on GitHub.


Feel free to modify and extend the notebook to explore further aspects of the data and experiment with different algorithms. Good luck.
