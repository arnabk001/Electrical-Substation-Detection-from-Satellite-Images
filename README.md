# Electrical-Substation-Detection-from-Satellite-Images
Code for the ICETCI competition on "Machine Learning based Feature Extraction of Electrical Substations from Satellite Data"

In this project, we developed a machine learning model to automatically detect electrical substations from high-resolution satellite imagery. The primary motivation for this work was to enhance the efficiency and accuracy of mapping and monitoring electrical infrastructure, which is vital for maintenance and planning operations.

### Link for the Competition
https://competitions.codalab.org/competitions/32132

### Dataset
https://www.kaggle.com/arnabkarmakar001/substation-detection

## Methodology
The methodology involves classifying each pixel in an image into a binary category. The training dataset comprised 100 satellite data chips with approximately 1-meter resolution, where each chip contained at least one electrical substation feature. The primary challenge of this work is the limitation of training data. With only 100 satellite images, it is hard to train a deep-learning model that can provide good results and also generalize better. To train the machine learning model, we also used a set of points and polygons defining the Area of Interest (AOI). For validation, a testing dataset consisting of a 20-chip mosaic with substations and other features was employed. The non-square shape of the bounding boxes (provided as shapefiles) required a more nuanced approach to image segmentation, where we generated masks from the shapefiles to create precise pixel-level labels.

To implement the semantic segmentation, we leveraged the segmentation models library, which is a robust collection of deep learning models for image segmentation built on Keras and TensorFlow. This library includes various architectures such as `Unet`, `Linknet`, `PSPNet`, and `PAN`, and supports numerous backbones for each model. We experimented with several models and found the UNet model with ResNet-34 backbone performs the best. The model consists of 24.4M parameters and to properly train a model this big, we used extensive data augmentation and regularization techniques.

_Refer to the code (jupyter notebook) for more details of the model architecture and training_

Throughout the project, we iteratively trained and tested the models, adjusting parameters and improving the model's performance as indicated by the Intersection Over Union (IoU) score and F1-score metrics.

## Results
![Alt text](./__results___16_0.png?raw=true "Results")

## Conclusion

The unique contribution of this work lies in the application of semantic segmentation to the specific problem of electrical substation detection in high-resolution satellite images. This approach enabled pixel-level classification, which is particularly important for the accurate identification of complex substation structures.

This project stands out as a practical demonstration of how machine learning and remote sensing can be synergistically used for automated infrastructure detection. It also serves as a valuable example for others in the field on how to implement and train a semantic segmentation model using open-source tools.

In conclusion, in this project, we have successfully applied semantic segmentation techniques to detect electrical substations in satellite imagery. The model achieved an IoU score of 0.8964 and an F1-score of 0.9452 on the training set, and an IoU score of 0.7153 and an F1-score of 0.8048 on the validation set. This work not only showcases the potential of combining machine learning with remote sensing for infrastructure analysis but also adds to the body of knowledge with a practical implementation guide for similar applications.


