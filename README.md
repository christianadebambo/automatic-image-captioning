# Automatic Image Captioning

This project implements an automatic image captioning system using deep learning techniques. Given an input image, the system generates a descriptive caption for the image. The project consists of several components:

- `build_vocab.py`: This script builds the vocabulary for the image captioning model. It processes the caption annotations in the COCO dataset and creates a vocabulary by tokenizing the captions and keeping track of word frequencies. The vocabulary is saved as a pickle file.
  
- `resize.py`: This script resizes the images in the dataset. It takes input images from a directory, resizes them to a specified size using the Python Imaging Library (PIL), and saves the resized images to an output directory. Resizing the images ensures that they have consistent dimensions for further processing.
  
- `train.py`: This script trains the image captioning model. It loads the preprocessed dataset, including the resized images and captions. The model consists of an Encoder CNN and a Decoder RNN. The Encoder CNN extracts image features, while the Decoder RNN generates captions based on the image features. The script uses the dataset to train the model, optimizing the model's parameters using gradient descent and backpropagation. The trained model checkpoints are saved for later use.
  
- `sample.py`: This script generates captions for new images using the trained model. It loads the saved Encoder and Decoder models, along with the vocabulary. Given an input image, it preprocesses the image, passes it through the Encoder to obtain image features, and then uses the Decoder to generate a caption based on the image features. The generated caption is printed as output.

## Requirements

- Python 3.x
- PyTorch
- torchvision
- pycocotools
- nltk

## Usage 

#### 1. Clone the repositories
```bash
git clone https://github.com/pdollar/coco.git
cd coco/PythonAPI/
make
python setup.py build
python setup.py install
cd ../../
git clone https://github.com/christianadebambo/automatic-image-captioning.git
cd automatic-image-captioning
```

#### 2. Download the dataset

```bash
pip install -r requirements.txt
chmod +x download.sh
./download.sh
```

#### 3. Preprocessing

```bash
python build_vocab.py   
python resize.py
```

#### 4. Train the model

```bash
python train.py    
```

#### 5. Test the model 

```bash
python sample.py --image='png/example.png'
```
