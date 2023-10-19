# Analysis for the Image Detection using the textile fabric data 👕

<br/>

## 1. Dataset

**AITEX FABRIC IMAGE DATABASE**

The textile fabric database consists of 245 images of 7 different fabrics. There are 140 defect-free images, 20 for each type of  fabric. With different types of defects, there are 105 images.

Images have a size of 4096×256 pixels. Defective images have been denominated as follows: nnnn_ddd_ff.png, where nnnn  is the image number, ddd is the defect code, and ff is the fabric code.

- There is a mask of defect, denominated as: nnnn_ddd_ff_mask.png, where white pixels represent the defect area of the defective image.

- Defect free images have been denominated as follows: nnnn_000_ff.png, where defect code has been replaced by 0000 code.

- Defect free images 15 and 08 of fabrics types 00 and 03 (only an area of 256×256 is shown).

- Defect 19 on fabric 02 and its mask (only an area of 256×256 is shown).


<u>**link** : https://www.aitex.es/afid/ </u>

<br/>

## 2. Gathering Requirements

- Automation of process inspection
- Model determines whether fabric fails and automatically saves to Excel

  => Learn the classifier to determine the failure of the fabric, automate Excel input

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

## 4. Check feasibility

<br/>

* Create a test program



      
