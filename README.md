# American_Isolated_Sign_Language_Detection
Google American Sign Language detection using state-of-art deep learning models

<img src="https://camo.githubusercontent.com/cb42c646117de94a5ca0ea0e6b71b88178544bd0719a10d944f8b4aa6b1430fd/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f686f6c69737469635f706970656c696e655f6578616d706c652e6a7067">

The project's purpose is to classify solitary American Sign Language (ASL) signs. We have trained a TensorFlow Lite model on labeled landmark data obtained with the MediaPipe Holistic Solution.

- Files - 
train_landmark_files/[participant_id]/[sequence_id].parquet The landmark data. The landmarks were extracted from raw videos with the MediaPipe holistic model. Not all of the frames necessarily had visible hands or hands that could be detected by the model.

Landmark data should not be used to identify or re-identify an individual. Landmark data is not intended to enable any form of identity recognition or store any unique biometric identification.

frame - The frame number in the raw video.
row_id - A unique identifier for the row.
type - The type of landmark. One of ['face', 'left_hand', 'pose', 'right_hand'].
landmark_index - The landmark index number. Details of the hand landmark locations can be found here.
[x/y/z] - The normalized spatial coordinates of the landmark. These are the only columns that will be provided to your submitted model for inference. The MediaPipe model is not fully trained to predict depth so you may wish to ignore the z values.
train.csv

path - The path to the landmark file.
participant_id - A unique identifier for the data contributor.
sequence_id - A unique identifier for the landmark sequence.
sign - The label for the landmark sequence.

- Landmark and data - https://github.com/google/mediapipe/tree/master

For this project, I have used transformer and LSTM.

## 🔗 Contributors & Credits
Supreetha Naik https://github.com/supreetn

Sushmita Joshi https://github.com/sushmita3105

Madhura Pandit https://github.com/madhurapandit

Swetha Subramanian https://github.com/swethasubu93
