# Disease Prediction Project

## Summary
The Disease Prediction Project is designed to assist healthcare providers, especially in regions with limited resources, in predicting diseases based on selected symptoms. This project includes two main files:
- **disease_prediction.py**: The core app where users input symptoms, and the model predicts possible diseases.
- **main.ipynb**: This Jupyter Notebook is responsible for training the machine learning model, performing exploratory data analysis (EDA), and testing different models to find the most effective one for use in the app.

Artificial Intelligence (AI) and Machine Learning (ML) are integral to this project. By training an ML model on a dataset of symptoms and diseases, the app can provide quick disease predictions based on user input, allowing healthcare providers to make faster and more informed decisions.

## File Breakdown

### `disease_prediction.py`
- **Purpose**: This file is the main driver for the web-based app that allows users to select symptoms and get predictions for potential diseases using a trained machine learning model.
- **Role of AI/ML**: The app loads a pre-trained MLP model that processes the symptoms inputted by the user and returns predictions for the most likely diseases.

#### Libraries Used:
1. **Streamlit**:
   - Manages the web interface of the app, allowing users to select symptoms from dropdowns.
   - Provides a simple, intuitive layout for ease of use by non-technical users.

2. **Pandas**:
   - Loads and processes symptom data for the model.
   - Converts input symptoms into a format usable by the prediction model.

3. **TensorFlow/Keras**:
   - Loads the pre-trained MLP model and uses it to make predictions on the input symptoms.
   - Provides the framework for deploying the trained model within the app.

4. **Plotly**:
   - Supports visualizations (if needed) for displaying additional data insights in an interactive manner.

5. **NumPy**:
   - Assists with efficient handling of arrays and numerical operations in the app.

#### Methods Used:
1. **`display_dropdowns()`**:
   - Displays the dropdown menus for users to select symptoms.
   - Dynamically updates the UI to reflect user input.

2. **`on_select_change()`**:
   - Captures user symptom selections and triggers the prediction process.
   - Updates the displayed prediction based on user input.

### `main.ipynb`
- **Purpose**: This notebook handles training the machine learning models. It explores different neural network architectures to determine the best performer for predicting diseases based on symptoms.
- **Role of AI/ML**: Various models are trained and evaluated, and the best-performing one is exported for use in the app.

#### Libraries Used:
1. **Pandas**:
   - Loads and prepares the dataset for training.
   - Handles missing data and encodes categorical variables (e.g., diseases and symptoms).

2. **Seaborn & Matplotlib**:
   - Visualizes the dataset during EDA to understand trends, distributions, and relationships between symptoms and diseases.

3. **Scikit-learn**:
   - Provides tools for data preprocessing, including One-Hot Encoding and splitting the dataset into training and test sets.
   - Facilitates model evaluation through accuracy metrics.

4. **TensorFlow/Keras**:
   - Defines and trains neural network models (MLP, CNN, LSTM).
   - Compiles and optimizes the models to minimize loss and maximize accuracy.

5. **Plotly**:
   - Offers interactive visualizations for analyzing model performance during training.

6. **NumPy**:
   - Efficiently manages large arrays and numerical computations during model training.

#### Models Explored:
1. **Multi-Layer Perceptron (MLP)**:
   - The MLP model was implemented using Keras's `Sequential` API. It consists of fully connected layers that process symptoms as input and predict the likelihood of different diseases.
   - **Pro**: Simple and effective for structured data such as tabular inputs, where symptoms are treated as independent features.
   - **Con**: May struggle with data that requires understanding complex spatial or temporal relationships.
   - **Accuracy**: ~81%. This model was chosen because it provided the best balance between accuracy and computational efficiency. It was easier to deploy in low-resource environments and performed well on the dataset.

2. **Convolutional Neural Network (CNN)**:
   - CNNs were tested for their ability to capture local patterns in the data. However, this model was more computationally intensive than the MLP model and provided only a slight improvement in accuracy.
   - **Pro**: Effective for capturing local patterns or spatial relationships in data.
   - **Con**: Computationally expensive and not significantly better in terms of accuracy compared to the MLP.
   - **Accuracy**: ~80.5%. Not selected due to higher resource demands and marginal performance gains.

3. **Recurrent Neural Network (RNN) with LSTM**:
   - LSTM networks were explored due to their ability to model sequences and temporal dependencies in data. However, this model struggled with the dataset, likely because it was not well-suited for sequential processing.
   - **Pro**: Excellent for tasks where the order of inputs (symptoms) matters.
   - **Con**: Slower to train and performed poorly on this dataset.
   - **Accuracy**: ~2.25%. This model was not chosen due to its poor performance and high computational cost.

#### Model Selection
After evaluating all three models, the **MLP** was selected as the final model due to its strong accuracy (~81%) and low computational cost. It effectively learned the patterns in the training data and generalized well to the test data. The CNN performed reasonably well but was too resource-intensive, and the LSTM model failed to perform on the dataset.

## Conclusion
The Disease Prediction Project targets communities with limited healthcare resources, such as rural clinics or developing countries, where access to advanced diagnostic tools is constrained. This app stands out from platforms like WebMD and IBM Watson because it allows users to select multiple, specific symptoms and get a clear prediction based on a lightweight machine learning model. Unlike broader platforms that rely on large-scale computational resources and provide vague symptom matching, this project focuses on efficient and precise predictions, suitable for low-resource environments. The MLP model was chosen for its accuracy, computational efficiency, and ease of deployment, making it ideal for regions with limited healthcare infrastructure.



