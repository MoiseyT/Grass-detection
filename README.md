# Grass-detection (ML)
## Evaluation of the projective cover of herbaceous vegetation using convolutional neural networks (CNN)
Task - Determine the percentage of projective cover of grass vegetation in a photograph using ML. [Dataset](https://www.kaggle.com/datasets/timofeymoiseev/grass)
The process of describing of the grass grows conditions has played important role in environmental research. During that time in the natural science had developed a methodology of forests, grasslands, savannahs, urbanized areas assessment. Evaluation of the projective cover of herbaceous vegetation is one of the indicators of the state of ecosystems of pastures, lawns, parks. It is also used in forest rehabilitation strategies or for assessment of trends and status of the agricultural ecosystem.
## Study area
The study area was located within the northwestern Moscow on border with Moscow region. The native flora is high antropogenically transformed and composed by secondary forest (e.g. Tilia cordata, Betula pendula, Picea abies et al.) with diverse herbaceous layer. Moreover, materials for training and testing were collected within park areas. Field survey were conducted from July to August in 2022.
## Data collection
Dataset represented by different plant species, including lawns. This was done to include as many different leaf shapes (lanceolate, linear, etc.) as possible in the dataset to improve the model.
The place for photographing was chosen based on the following thesis:
- Images contain various plant communities most typical of a biome;
- The images included dead plant and soil surface.
Every image was made from a square area at a height of 1 m from the surface using an IPhone 11 camera with resolution of 4032 x 3024 pixels.
## Image Preprocessing
At the beginning, the images were divided into 2 parts with a resolution of 3024 x 2016. Then three experts marked 30 photos of 3024 x 2016 pixels in the first test sample by image. The images were split into tiles by 10 x 10 grid to improve the quality of the model. Two experts marked 10 photos by 10 x 10 grid also to test the model performance in the second test data. This is a time-consuming and labor-intensive process, but it allows comparing the result of work between the whole image and the tiles. Researchers in ecology with experience in determining the projective cover of herbaceous vegetation in situ were chosen as experts.
The author marked 1500 tiles of 202 x 302 pixels images for training the neural network. Train dataset contains images, that were divide into 100 equally fragments on a 10 x 10 grid. Then the projective coverage of a fragment was estimated.

![image](https://github.com/MoiseyT/Grass-detection/assets/101183971/d9a567e3-ee4f-43b5-87a0-7645a6e468fd)

## Proposed Algorithm

Deep convolutional neural networks (ResNet50 and GoogLeNet) were chosen to train the model. It was used pre-training models with ImageNet dataset. The code was created in the Python in the Google Colab software [Google Colab](https://colab.research.google.com/drive/1n1-Sa0CJDcQeIMOy0gFQJlY9s1pHD3zV?usp=sharing). The output layer of the CNN architecture was modified to be represented by a single neuron, which had to characterize the percentage of projective coverage.

During the learning process, fragments of a 202 x 302-pixel photo with the known value of the percentage of grass projective cover determined by the author are fed to the input of the neural network. The photos are then transformed to a format of 224 x 224 pixels (this is the resolution used in GoogLeNet and ResNet50 on the input layer).
