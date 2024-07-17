# Robot-Vision
376.055 TU-Wien Robot-Vision Class deformation

In this project the work "Dynamic Point Field" , by Sergey Prokudin, will be evaluated.
It will be done in tow way, the first is the evaluation of the Chamfer distance of the predicted and target points cloud and the second is a visual representation with color coding for the point which corresponds to their origianl/source coordinates.

### Surface reconstruction
The first section is used for surface reconstruction, since CAD-models lack the need vertices to work with them as dense point clouds.
This part is straight from the work "Dynamic point fields".
Note: Surface_Preprocessing_for_Same_Class_Deformation.ipynb is the same code for surface reconstruction as in the main code but was used a testing code and then to get some prepare test object for the trained models.

The only thing that need to be set are the two models which i want to train the model with , e.g. the path to the source and target model.

### Deformation
This is the main part of this project. At first some functions are defined (normalizing and adding color corresponding to the coordinates) , followed by loading the point clouds for the training ( best results are shown for source:table0025 and target:table0020)
After the SIREN model and the training code the DEformation begins.

### Deformation without guidance
Both object from before ( from the surface reconstruction) are used in the given model. 

Important parameters: 
      AIAP_WEIGHT
      CHAMFER_WEIGHT
      GUIDED_WEIGHT
      
This three weights influence the deformation of the cloud. 
The AIAP is a constrain of how much the original shape should be retaind.
The Chamfer is for the deformation, to deform the source as close as possible to the target.
Guided uses correspondences (features) between the clouds to "guide" the deformation i the right direction
(The best results were achieved by these values AIAP_WEIGHT = 1.0e3,CHAMFER_WEIGHT=1.0e3 and GUIDED_WEIGHT= either 1.0e4 or 1.0e5)

This project depends on hardcoding for the selection of the models, for the testing the model that will be tested has to "uncommented" and entered into the model.


### Deformation withguidance
Here the selection for the model is hardcoded since the correspondences were selected manually, which means these point cloud are "preprocessed" via the Surface_Preprocessing_for_Same_Class_Deformation.ipynb and the best points were search manually. 

!!! Which means these models should be used as their are and not to bee created again, since this can change the best corresponding points !!!


This project depends on hardcoding for the selection of the models, for the testing the model that will be tested has to "uncommented" and entered into the model.
Important parameters: 
      AIAP_WEIGHT
      CHAMFER_WEIGHT
      GUIDED_WEIGHT



The results are plausible but the guidance training is not robust or versatile, since is uses manually picked points for the correspondance for speciic models.
Further testing with "Neural DEscriptor Fields" is recomended.

