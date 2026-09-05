# World Model: Real-Time Indoor Scene Understanding for Robotics

## Overview

**World Model** is a computer vision project focused on real-time indoor scene understanding for robotics. The system detects and segments important household objects from indoor images, providing a visual understanding of the surrounding environment that can serve as a perception component for future household robotics applications.

The project uses **YOLO11n-Seg**, a lightweight instance segmentation model, fine-tuned on a custom household-object dataset.

---

## Project Information

| Item              | Details                                |
| ----------------- | -------------------------------------- |
| Course            | CSE445 – Machine Learning              |
| Project           | World Model                            |
| Task              | Household Object Instance Segmentation |
| Model             | YOLO11n-Seg                            |
| Framework         | Ultralytics YOLO                       |
| Training Platform | Google Colab                           |
| GPU               | NVIDIA Tesla T4                        |

---

## Group Members

| Name                 | Student ID | Email                                                                   |
| -------------------- | ---------: | ----------------------------------------------------------------------- |
| Md. Tanveer Ahmed    | 2311582042 | [tanveer.ahmed07@northsouth.edu](mailto:tanveer.ahmed07@northsouth.edu) |
| S.M. Mahin           | 2132140642 | [s.m.mahin@northsouth.edu](mailto:s.m.mahin@northsouth.edu)             |
| Zidan Zafar Rudra    | 2013747642 | [zidan.rudra@northsouth.edu](mailto:zidan.rudra@northsouth.edu)         |
| Shameem Ahmed Rizwan | 2233704642 | [shameem.rizwan@northsouth.edu](mailto:shameem.rizwan@northsouth.edu)   |


**Group:** Group-13

---

## Objective

The main objective of this project is to develop a computer vision system capable of identifying and precisely segmenting common household objects in indoor environments.

This visual perception capability can later be extended toward robotic applications such as:

* Indoor environment understanding
* Object-aware navigation
* Household object interaction
* Scene perception for autonomous robots
* Object-based decision making

---

## Dataset

The original dataset contains **187 images** with **39 object classes**. Due to the relatively small dataset size and significant class imbalance, **18 important household-object classes** were selected for the initial model.

### Selected Classes

1. Bed
2. Chair
3. Fan
4. Door
5. Table
6. Sink
7. Curtain
8. Window
9. Commode
10. Mirror
11. Sofa
12. Bidet Shower
13. Tap
14. Shower
15. Floor Drain
16. Air Conditioner
17. Toilet Paper Holder
18. Toothbrush Holder

### Dataset Split

| Split      |  Images |
| ---------- | ------: |
| Training   |     131 |
| Validation |      34 |
| Testing    |      17 |
| **Total**  | **182** |

Only images containing at least one of the selected 18 classes were retained.

---

## Model

The project uses **YOLO11n-Seg**, a lightweight YOLO11 instance segmentation model.

A pretrained YOLO11n-Seg model was fine-tuned on the custom household-object dataset.

### Training Configuration

* **Epochs:** Up to 100
* **Image Size:** 432 × 432 during training
* **Batch Size:** 16
* **Early Stopping:** Patience = 20
* **GPU:** NVIDIA Tesla T4
* **Task:** Instance Segmentation

For evaluation and prediction, the image size was automatically adjusted to **448 × 448** to satisfy the model's stride requirement.

---

## Results

The final model was evaluated on the **unseen test set of 17 images**.

### Overall Test Performance

| Metric    |    Box |       Mask |
| --------- | -----: | ---------: |
| Precision | 73.99% | **70.43%** |
| Recall    | 47.64% | **48.76%** |
| mAP@50    | 53.29% | **47.94%** |
| mAP@50-95 | 37.91% | **29.48%** |

The primary metric for this project is **Mask mAP@50**, since the main task is instance segmentation.

### Best Performing Classes

Several classes showed promising segmentation performance:

* **Sink:** 99.5% mAP@50
* **Air Conditioner:** 99.5% mAP@50
* **Commode:** 88.1% mAP@50
* **Sofa:** 81.0% mAP@50
* **Window:** 72.8% mAP@50
* **Curtain:** 69.5% mAP@50

Performance was weaker for low-frequency classes such as chair, tap, shower, bidet shower, and toilet paper holder.

---

## Qualitative Results

The trained model was used to generate predictions on all **17 test images**.

The predictions demonstrate that the model can detect and segment multiple household objects within the same indoor scene.

Prediction outputs are generated and stored locally during the Colab execution.

---

## Limitations

The current version has several limitations:

1. The dataset is relatively small, with only 131 training images.
2. The class distribution is highly imbalanced.
3. Some classes contain very few training examples.
4. Low-frequency objects are harder for the model to detect consistently.
5. The current system focuses on object-level instance segmentation rather than complete room-level scene understanding.

Therefore, the current model should be considered a **baseline perception model** rather than a production-ready robotic vision system.

---

## Future Work

Future improvements will focus on:

* Increasing the number of training images
* Collecting more examples for underrepresented classes
* Applying suitable data augmentation
* Expanding the number of recognized household objects
* Improving segmentation accuracy
* Introducing room-level scene understanding
* Integrating object perception with robotic navigation and interaction
* Developing a real-time robotic perception pipeline

---

## Notebook

The complete implementation and experimental workflow are available in the Jupyter/Google Colab notebook:

**`World_Model.ipynb`**

The notebook contains the dataset preparation, model training, evaluation, and prediction pipeline.

---

## Conclusion

The initial **World Model** successfully demonstrates household object instance segmentation using YOLO11n-Seg. On the unseen test set, the model achieved **70.43% mask precision, 48.76% mask recall, and 47.94% mask mAP@50**.

Although performance is limited by the small and imbalanced dataset, the results provide a functional baseline for developing a more comprehensive indoor scene understanding system for robotics.
