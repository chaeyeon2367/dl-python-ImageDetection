<br/>
<br/>


# Analysis for the Image Detection using the textile fabric data 👕

A program that uses artificial intelligence to identify defects such as stains, scratches, and tears in textile fabric dataset

<br/>

## 1. Dataset

**AITEX FABRIC IMAGE DATABASE**

The textile fabric database consists of 245 images of 7 different fabrics. There are 140 defect-free images, 20 for each type of  fabric. With different types of defects, there are 105 images.

Images have a size of 4096×256 pixels. Defective images have been denominated as follows: nnnn_ddd_ff.png, where nnnn  is the image number, ddd is the defect code, and ff is the fabric code.

- There is a mask of defect, denominated as: nnnn_ddd_ff_mask.png, where white pixels represent the defect area of the defective image.

- Defect free images have been denominated as follows: nnnn_000_ff.png, where defect code has been replaced by 0000 code.

- Defect free images 15 and 08 of fabrics types 00 and 03 (only an area of 256×256 is shown).

- Defect 19 on fabric 02 and its mask (only an area of 256×256 is shown).


<br/>
<br/>

- **Good** 

<img width="813" alt="Capture d’écran 2023-10-26 à 16 03 34" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/63888437-1145-4d90-9f2c-8fc76e422e45">

- **Defective**

<img width="807" alt="Capture d’écran 2023-10-26 à 16 04 50" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/73e6664d-aeb8-4d5a-af5d-564b0b4d35de">



- **Data Analysis**

<img width="621" alt="Capture d’écran 2023-10-26 à 16 07 48" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/1c90fcbf-4a1a-46a5-ac71-f0ef2fffc8fc">


=> Similar types of defects appear in various directions and locations


<u>**link** : https://www.aitex.es/afid/ </u>

<br/>

## 2. Gathering Requirements

- Automation of process inspection
- Model determines whether fabric fails and automatically saves to Excel

  => Learn the classifier to determine the failure of the fabric, automate Excel input

<br/>

<img width="656" alt="Capture d’écran 2023-10-26 à 15 16 49" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/4d73e43d-3fdc-4812-a656-1985404be54a">

<br/>

## 3. Specification

<br/>

* Supporting environment
  * Test Environment
    1) Local, MacOS, 16RAM
    2) Limited program operation speed (batch behavior)
    3) Primary Tuned Test Algorithm Performance

  * Final Target
    1) real-time operational program : 256 x 256 based on image 1fps , GPU
    2) Tuned final algorithm performance

<br/>



## 4. Program structure

<br/>

  * Test Program


<img width="475" alt="Capture d’écran 2023-10-26 à 15 45 58" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/91d3116b-b47c-4351-a2ff-a078a786409b">


  * Official Program


<img width="613" alt="Capture d’écran 2023-10-26 à 15 50 47" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/f152cbcd-7f3b-4613-bfb0-945909354cf5">


  * Training program

    
<img width="617" alt="Capture d’écran 2023-10-26 à 15 53 04" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/8d0f3141-6336-4b07-a5d0-be98572e22c2">


  * Transmission priority


<img width="569" alt="Capture d’écran 2023-10-26 à 16 02 53" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/099add3e-303c-4eb6-bb4e-6e04596a73cf">

<br/>


## 5. Algorithm


<img width="617" alt="Capture d’écran 2023-10-26 à 15 53 04" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/8d0f3141-6336-4b07-a5d0-be98572e22c2">

- Utilization of CNN architectures suitable for multi-scale feature analysis (utilizing skip connections, Inception, etc.)
- Application of data augmentation to enhance algorithm accuracy (e.g., flip, rotation, translation)
- Data serialization for efficient training (using TFRecord)
- Performing oversampling to address data imbalance


<br/>


## 6. Data preparation -TFRecord

TFRecord is a binary format for storing large amounts of data(dataset) efficiently.

The main advantages of using TFRecord include:

  1. **Efficiency**: TFRecord is a binary format, which makes it highly efficient for both reading and writing large datasets. It reduces the storage space required and accelerates data loading, which is crucial for training deep learning models on massive datasets.
  2. **Serialization**: It enables easy serialization of complex data structures, such as images, audio, and sequences of numerical data. This serialization process is crucial for preparing data for machine learning tasks.
  3. **Parallelization**: TFRecord files can be split into multiple shards, allowing for parallel processing and input pipeline optimization. This is beneficial when working with multi-core CPUs or distributed computing frameworks.
  4. **Compression**: TFRecord supports data compression, which can further reduce storage and speed up data loading, especially when dealing with large datasets.
Random Access: It allows for efficient random access to data, making it suitable for tasks like shuffling and batching data during training.
  5. **Flexibility**: TFRecord can store data of varying data types, including images, audio, text, and numerical data, making it a versatile choice for machine learning applications.

<br/>


## 7. Data Augmentation

This data augmentation technique helps increase the diversity of the training dataset and can improve the model's robustness and generalization.

  1. **Flip**: It randomly flips the image both left-right and up-down with a 50% probability.
  2. **Rotate**: It randomly rotates the image by a random angle between 0 and 360 degrees with a 50% probability. The interpolation method used is 'BILINEAR' for smoother rotation.
  3. **Translation**: It randomly applies translation to the image by shifting it horizontally and vertically within the range of -10 to 10 units. The decision to apply translation is determined with a 50% probability. It uses 'BILINEAR' interpolation for smoother transformation.

After these augmentation operations, the method returns the augmented image along with its label. 

<br/>


## 8. Inception Model(GoogLeNet)

<img width="797" alt="Capture d’écran 2023-10-26 à 16 48 08" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/a41454d8-8cc7-4323-928c-7fa904ff151f">

<u>**Ressource** : https://cloud.google.com/tpu/docs/inception-v3-advanced?hl=fr </u>

The Inception architecture, also known as GoogleNet, is known for its ability to capture multi-scale features efficiently.

- My model uses a series of inception blocks to capture multi-scale features in the input image, and it concludes with fully connected layers to make a binary classification prediction. 
- My model is designed to handle images with a resolution of 256x256 pixels and three color channels.

<br/>



## 9. Results

- Test program results

<img width="670" alt="Capture d’écran 2023-10-27 à 12 03 40" src="https://github.com/chaeyeon2367/dl-python-ImageDetection/assets/63314860/8d871059-741c-4571-bebc-520123df655e">

<br/>

  1. I initially set a threshold of 0.5 to classify defects in textile image data. However, the model training results showed that it sometimes incorrectly predicted "fail" as "true" in the range of 0.5 to 0.7.
  2. Therefore, I concluded that adjusting the threshold appropriately, considering the trade-off between false negatives and false positives, is the best way to fine-tune it for the application.
  3. So, tuning the threshold to better suit the application is the most effective approach.



