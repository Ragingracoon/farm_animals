# Farm animal identifier

 identifies certain farm animals that appear in pictures using AI



## The Algorithm

AI that Identifies whether a picture contains a pig a cow or a goat.
The code uses a collection of pictures of each of the different animals to give a percent chance that a picture is that paticular animal. this can help people learn about what different farm animals look like.

## Running this project

1. Make sure that both the Jetson Inference library and Python3 are installed on your Jetson Nano.
2. Download the model_best.pth.tar file and the farm_animals folder. Link to the files: https://drive.google.com/drive/folders/1lkcIms2aTFR4OIjoQWtKuK5p_UtZ3o3D?usp=sharing
model file: https://drive.google.com/file/d/1kRZxtIEJ0f9bjzTUVZ4PPYLgu6AFJt3r/view?usp=sharing
3. Open the terminal on your nano and navigate to the classification directory:
```
   $ cd jetson-inference/python/training/classification
```
4. Create two new directories, data and models:
```
   $ mkdir data
   $ mkdir models
```
5. Navigate to the models directory and create a new directory called farm_animals:
```
   $ cd models
   $ mkdir farm_animals
```
6. Upload the model_best.pth.tar file to the farm_animals directory in the models directory and upload the farm_animals folder to the data directory.
7. Navigate to the jetson-inference directory and run the docker:
```
   $ cd ../../../
   $ ./docker/run.sh
```
8. Navigate to the classification directory again:
```
   $ cd python/training/classification
```
9. Export the model to ONNX:
```
   $ python3 onnx_export.py --model-dir=models/farm_animals
```
10. Exit the docker and navigate to the classification directory again:
```
   $ exit
   $ cd python/training/classification
```
11. Set the NET and DATASET variables:
```
   $ NET=models/farm_animals
   $ DATASET=data/farm_animals
```
12. Run this command to see how it operates on an image from the cow folder:
```
   $ imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/cow/images700.jpg cow.jpg
```
13. Open the new image in VSCode to see how the model works or scroll up to see how the model classified the image if you are using a regular terminal.
14. To run the model on a different image, change this section of the code: /cow/images700.jpg 

15. if you want to change the image your testing change the image to one from a different folder

16. The first 'cow' refers to which set of images in the test folder you are choosing from. 'images700.jpg' is the image you are classifying in the set of images you chose. Finally, 'cow.jpg' is the name of the image that will be exported once the model finishes classifying it.

watch video demostration here: 
