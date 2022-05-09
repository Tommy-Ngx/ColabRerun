# food-recognition-app
DL Project Apr 2022


<h1 align="center">🍔🍟🍗 Food analysis by AI 🍞🍖🍕</h1>

YOLACT : https://youtu.be/CbnwrQq7x-8

<p align="center">

<!--  <img src="https://visitor-badge.laobi.icu/badge?page_id=lannguyen0910.food-detection-yolov5" alt="visitors" />
  
 <a><img  src="./static/assets/demo/pipeline.png"></a>
  <br>
</p>-->


<p align="center">
    <a href="./LICENSE"><img src="https://img.shields.io/github/license/Naereen/StrapDown.js.svg" alt="MIT" /></a>
  <a><img src="https://img.shields.io/badge/DL%20Final%20Project%20-2022-1f425f.svg" alt="Python" /></a> 
  <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Made%20with-Python-1f425f.svg" alt="Python" /></a> 
<!--    <a href="https://github.com/lannguyen0910/food-detection-yolov5/stargazers">
    <img src="https://img.shields.io/github/stars/lannguyen0910/food-detection-yolov5?style=flat-square" alt="Stars"/>
    </a>
 <a href="https://github.com/lannguyen0910/food-detection-yolov5/fork">
 <img src="https://img.shields.io/github/forks/lannguyen0910/food-detection-yolov5.svg?style=flat-square" alt="Forks"/>
 </a>
 <a href="https://github.com/lannguyen0910/food-detection-yolov5/issues">
<img src="https://img.shields.io/github/issues/lannguyen0910/food-detection-yolov5?style=flat-square" alt="Issues"/>
</a>
<a href="https://github.com/lannguyen0910/food-detection-yolov5/pulls">
<img src="https://img.shields.io/github/issues-pr/lannguyen0910/food-detection-yolov5?style=flat-square" alt="Pull Requests"/>
</a> -->
</p>

<!--
## 🌳 **Folder Structure**
<details>
  <summary><strong>Details</strong></summary>
```
food-detection-yolov5
|
│   app.py                    # Flask server
|   modules.py                # inference stage, export result files, csv,...
|
└───api      
│   └─── ...
│   └─── api.py               # make request, update db
│   └─── secret.py            # get reponse 
|
└───model                     
│   └─── ...
│   └─── detect.py            # image detection
│   └─── video_detect.py      # video detection
|
└───static
│   └─── ...
│   └─── assets               # contain upload files, detection files
│   └─── css                  # custom css files, bootstrap
│   └─── js
|       └─── ...
│       └─── client.js        # custom js for templates
│       └─── chart.js         # nutrients analysys with charts
|
└───templates
│   └─── ...  
│   └─── index.html           # upload files' page
│   └─── url.html             # input URLs' page    
```
</details> -->
   

<details open> <summary><strong>Dev logs</strong></summary>
<strong><i>[11/04/2022]</i></strong>  Data Crawling and labelling </b>. <br>
<strong><i>[Week 2]</i></strong>  Train model YOLOv5 latest versions/segmentaion by Unet.<br>
 <strong><i>[Week 3]</i></strong> Update soon <br>
 <strong><i>[Week 4]</i></strong> Update soon <br>
 <strong><i>[Final]</i></strong> Presentation 
</details>


 ## 🌟 **Inference**
- File structure
```
this repo
│   app.py
└───configs
│     └───classification          # Contains classification's configurations
|             └───test.yaml 
│     └───detection          # Contains detection's configurations
|             └───....
│     └───segmentation          # Contains segmentation's configurations
|             └───....
```



## 🌟 **Dataset**
- Detection: [link](https://drive.google.com/drive/folders/14rJclN97hZqe6bmGkTjnvPaDBBIF4v5w?usp=sharing) (merged OID and Vietnamese Lunch dataset)
- Classification: [link](https://drive.google.com/drive/folders/11PH1ZF3ZCMKDQvxrblBA-Zy02iWgM4lq?usp=sharing) (MAFood121)
- Semantic segmentation: [link](https://mm.cs.uec.ac.jp/uecfoodpix/UECFOODPIXCOMPLETE.tar) (UECFood)

## 🌟 **Dataset details**
<details>
<summary>To train the food detection model, we survey the following datasets:</summary>
  
  - <a href="https://storage.googleapis.com/openimages/web/index.html">Open Images V6-Food</a>: Open Images V6 is a huge dataset from Google for Computer Vision tasks. To solve our problem, we extracted from a large dataset on food related labels. The extracted set includes 18 labels with more than 20,000 images.
  - <a href="http://foodcam.mobi/dataset.html">School Lunch Dataset</a>: includes 3940 photos of a lunch of Japanese high school students, taken at the same frontal angle with the goal of assessing student nutrition. Labels consist of coordinates and types of dishes are attached and divided into 21 different dishes, in the dataset there is also a label "Other Foods" if the dishes do not belong to the remaining 20 dishes.
  - <a href="https://drive.google.com/drive/folders/1PLrsJBS1EtJLY6RpEriASTfQ5WRlPQAt?usp=sharing">Vietnamese Food</a>: a self-collected dataset on Vietnamese dishes, including 10 simple dishes of our country such as: Pho, Com Tam, Hu Tieu, Banh Mi,... Each category has about 20-30 images, divided 80-20 for training and evaluation.
  
We aggregate all the above datasets to proceed training. Dishes that appear in different sets will be grouped into one to avoid duplication. After aggregating, a large data set of 60,305 images with 44 different foods from all regions of the world.
<br>
  
In addition, we find that if we expand the problem to include classification, the dataset will increase significantly. Therefore, to further enhance the diversity of dishes, we collect additional datasets to additionally train a classification model:
  - <a href="http://www.ub.edu/cvub/mafood121/">MAFood-121</a>: consisting of 21,175 training image samples. The dishes are selected from the top 11 most popular cuisines in the world according to Google Trends statistics, these cuisines come from many countries around the world, especially Vietnam. For each type of cuisine, 11 typical traditional dishes are selected. The dataset has a total of 121 different types of dishes, each belonging to at least 1 of 10 food categories: Bread, Eggs, Fried, Meat, Noodles, Rice, Seafood, Soup, Dumplings, and Vegetables . 85% of the images are used for training and the remaining 15% for evaluation.
  - <a href="https://data.vision.ee.ethz.ch/cvl/datasets_extra/food-101/">Food-101</a>: includes 101 different types of dishes, with 101,000 sets of photos. For each dish, 250 images were used as test images and the remaining 750 images were used for training. The training images in this set still have a lot of noise, sometimes the colors are too sharp or some of the data samples are mislabeled, these noises are intentional by the author (mentioned in the study).
  
We also perform the aggregation of the two data sets above into one. The new set includes <b>93,748 training images</b> and <b>26,825 evaluation images</b> with a total of <b>180 different dishes</b>. It can be seen that the number of dishes has increased significantly, if the model detects a dish labeled "Other Foods", the classification model will be applied to this dish and classified again.
</details>


## 📙 **Credits**

- Custom template: https://github.com/kaylode/theseus.
- YOLOv5 official repo: https://github.com/ultralytics/yolov5.
- Semantic segmentation models: https://github.com/qubvel/segmentation_models.pytorch
- Base code for android app: https://github.com/cmdbug/YOLOv5_NCNN.
- Ncnn by Tencent: https://github.com/Tencent/ncnn
- Edamam API: https://developer.edamam.com/food-database-api-docs.
- Chart.js: https://github.com/chartjs/Chart.js.
