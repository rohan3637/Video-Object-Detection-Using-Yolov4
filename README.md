# Video-Object-Detection:
Real time object detection, tracking and classification using Deep Learning techniques.

# Tasks:
-The stated task is to use Deep Learning models to detect, track and classify animals and vehicles in a video in real-time.

-We will prepare our own custom dataset, label them and train our own custom model from scratch for this task.



# Approach:

![obj detector flow chart](https://user-images.githubusercontent.com/58647922/123631841-d813b000-d834-11eb-84df-77aed74036d5.png)


-We will train and run custom Object Detections with Darknet in the Cloud through Google Colab.

-In order to create a custom object detector we will need the following:

1. Labeled Custom Dataset
2. Custom .cfg file
3. obj.data and obj.names files
4. train.txt file (test.txt is optional here as well)

# Step 1: Gathering and Labeling a Custom Dataset

-We will gather datasets of animals and vehicles from Google's Open Images Dataset and use OIDv4 toolkit to generate labels.

-You can also mass download images from Google Images and use LabelImg, an annotation tool, for drawing bounding boxes and to label each image.

-Finally, we should have a folder with images and text files (containing labels as well as co-ordinates of bounding boxes for each image) as our training dataset and validation dataset as well as classes.txt file containg name of classes we want to classify, one class per line.

# Step 2: Moving our Custom Datasets Into our Cloud VM

-Now, we need to move our datasets into cloud VM so that when it comes the time we can actually train and validate our model.

-We will first zip our train and validation folder, upload it to google drive in a seperate folder (custom_model in my case), copy in the zips and unzip them in our cloud VM.

# Step 3: Configuring Files for Training

-This step inolves configuring our custom .cfg, obj.data, obj.names, train.txt and test.txt files.

-The .cfg file contains our model architect. We need to prepare the .cfg to fit our needs based on our object detector.

-The obj.names file contains one class name per line in the same order as our 'classes.txt' file from the dataset generation step.

-The obj.data file contains the info. about no. of classes, path variable for test.txt, train.txt and obj.names files. It also contains backup path where we will save the weights to of our model throughout training. 

-Create a backup folder in your google drive and put its correct path in obj.data file.

-The last configuration files needed before we can begin to train our custom detector are the train.txt and test.txt files which hold the relative paths to all our training images and valdidation images.

-generate_train.py and generate_test.py are scripts that eaily generate these two files with proper paths to all images.

-upload all these files to cloud VM from google drive and run generate_train.py and generate_test.py to generate train.txt and test.txt.

# Step 5: Train our Custom Object Detector.

## yolov4 model architecture: 

![image](https://user-images.githubusercontent.com/58647922/130737344-52e088e1-6e60-402d-8eaf-f6fffd0a4f5b.png)

![image](https://user-images.githubusercontent.com/58647922/130737383-7b18e7d2-a4f6-4dbe-a3e5-64252bfe2c91.png)


Loss curves:


<img src="https://user-images.githubusercontent.com/58647922/123946017-61a1ba00-d9bc-11eb-958d-4ec7c4c3e69e.png" width=800 height=500>

<img src="https://user-images.githubusercontent.com/58647922/123946061-69615e80-d9bc-11eb-9d9b-56b7b8a0c465.png" width=800 height=500>

<img src="https://user-images.githubusercontent.com/58647922/123946107-7716e400-d9bc-11eb-91ee-e1e37770443e.png" width=800 height=500>





# Step 6:Evaluation and testing our model:

Performance metrics:

class_id = 0, name = Lion, ap = 83.33%   	 (TP = 6, FP = 4) 

class_id = 1, name = Tiger, ap = 76.00%   	 (TP = 4, FP = 1) 

class_id = 2, name = Elephant, ap = 100.00%   	 (TP = 6, FP = 2) 

class_id = 3, name = Motorcycle, ap = 82.57%   	 (TP = 7, FP = 1) 

class_id = 4, name = Car, ap = 69.75%   	 (TP = 11, FP = 7) 

 for conf_thresh = 0.25, precision = 0.65, recall = 0.81, F1-score = 0.73 
 
 for conf_thresh = 0.25, TP = 29, FP = 20, FN = 7, average IoU = 47.16 % 

 IoU threshold = 50 %, used Area-Under-Curve for each unique Recall 
 
 mean average precision (mAP@0.50) = 0.803298, or 82.33 %


Images:

<img src="https://user-images.githubusercontent.com/58647922/123947107-9a8e5e80-d9bd-11eb-901a-7cdff1afdd12.png" width=800 height=500>

<img src="https://user-images.githubusercontent.com/58647922/123947271-d45f6500-d9bd-11eb-9c9e-be82004db8d4.png" width=800 height=500>

<img src="https://user-images.githubusercontent.com/58647922/123947524-1b4d5a80-d9be-11eb-942e-52131f5e4a0a.png" width=800 height=500>

Videos:

https://user-images.githubusercontent.com/58647922/123947889-80a14b80-d9be-11eb-8086-9926759ccbb2.mp4


https://user-images.githubusercontent.com/58647922/123949628-65374000-d9c0-11eb-93a9-1cb8c8f83bd0.mp4


https://user-images.githubusercontent.com/58647922/123949678-73855c00-d9c0-11eb-991f-3b8f0f548523.mp4


https://user-images.githubusercontent.com/58647922/130736776-10ad1a76-7a3f-41bc-a053-a5ce93d8a814.mp4


https://user-images.githubusercontent.com/58647922/130736864-3929e08f-43a1-492a-83e6-f8741dc66a7e.mp4










