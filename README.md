
# Isolated Sign Language Recognition using Deep Learning technologies
Google American Sign Language detection using state-of-art deep learning models is a Kaggle competition (https://www.kaggle.com/competitions/asl-signs). The project's purpose is to classify solitary American Sign Language (ASL) signs. We trained a transformer and LSTM models on labeled landmark data. The delivarable is a TensorFlow Lite model fro mobile application. 

## Data 
The landmarks were extracted from raw videos with the MediaPipe holistic model.
![ASL](https://camo.githubusercontent.com/cb42c646117de94a5ca0ea0e6b71b88178544bd0719a10d944f8b4aa6b1430fd/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f686f6c69737469635f706970656c696e655f6578616d706c652e6a7067)
The landmark data are in parquet. Each parquet file had followings columns: 
    
    frame - The frame number in the raw video.
    row_id - A unique identifier for the row.
    type - The type of landmark. One of ['face', 'left_hand', 'pose', 'right_hand'].
    landmark_index - The landmark index number.
    [x/y/z] - The normalized spatial coordinates of the landmark. These are the only columns that will be provided to the model for inference.

## Exploratory Data Analysis

- Approx 94K parquet files, each consist of a combination of landmarks data (movement) that represent one single sign - 250 unique labels in the dataset
- Each frame has four landmark types - Each type has a fixed number of landmark indices
    ![Lanmark-indices](https://github.com/supreetn/American_Isolated_Sign_Language_Detection/assets/109064336/ae79632e-dc57-4c40-9594-6543bf0e04af) 
    Taking 543 landmarks per frame created a very bulky data for modelt o process, thus only important landmarks are considered - left hand, right hand and only the lip & head outline indices in face. 
- All training data was required to have constant number of frames to be given as input to model. As majority video landmark files had frames in range 5 - 30, the n_frames is 30.
    ![Frame-Frequency](https://github.com/supreetn/American_Isolated_Sign_Language_Detection/assets/109064336/76aa707e-c7eb-45c3-bf78-60648275c050)

## Feature Engineering
![Workflow](https://github.com/supreetn/American_Isolated_Sign_Language_Detection/assets/109064336/bd9fb599-c87a-43ca-a2b8-ce5d8799a31b)

## Methodology
- *Transformer-LSTM*:   
    The architecture combines Transformer and LSTM layers for sequence processing.  Multi-head attention focuses on key sequence elements. LSTM layers handle sequential data. A 30% dropout prevents overfitting. Two dense layers with softmax produce class probabilities.
- *LSTM*:   
    The model takes flattened 3D hand movement sequences and predicts ASL sign labels. It includes three dense layers with normalization, ReLU activation, and 0.07 dropout. An LSTM layer captures temporal dynamics. The output layer yields sign label probabilities, selecting the highest probability as the prediction.
- *Inference Model*:    
    For inference, extra layers were added to adapt the model to the 3-dimensional testing data for the competition. The model initially trained on 2D input, with specific indices and a shape, was adjusted to handle this new format. This adaptation process was applied for inference of testing data (approx. 40,000 videos).
## Results 
- The results of the two models with infrence is given below.
    ![Results](https://github.com/supreetn/American_Isolated_Sign_Language_Detection/assets/109064336/6ebc91e4-8833-4ae3-84b6-2fcc8037fb24)
- Graph for accuracy and error for LSTM model training.
    ![LSTM_model](https://github.com/supreetn/American_Isolated_Sign_Language_Detection/assets/109064336/c5e3755c-9cbd-4bef-87aa-7a0585062f04)
- - Graph for accuracy and error for Transformer - LSTM model training.
    ![Transformer-LSTM model](https://github.com/supreetn/American_Isolated_Sign_Language_Detection/assets/109064336/265432b7-41f4-4fc4-9797-5b36d460505f)


## 🔗 Contributors & Credits
Supreetha Naik https://github.com/supreetn

Sushmita Joshi https://github.com/sushmita3105

Madhura Pandit https://github.com/madhurapandit

Swetha Subramanian https://github.com/swethasubu93
