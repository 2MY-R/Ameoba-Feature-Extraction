# AI Driven discovery; Rare Celluar Behaviour

## Contributions 
- **Author**: Toumai Rouse
- **Supervisor:** Ashley Cadby
- **Co-Supervisors:** Rebecca Betts, Olga Chambers

I could have only done this project with my supervisor/co-supervisors' help, support, and advice. Futhermore, I was provided with a solid foundation of code to build off of and collaborate with to support the whole research team; as Olga and Rebecca have previously written, much of the code I am presenting. I have used their code and advice as a stepping stone to add my contribution to the broader project.

## Affiliations
- [School of Mathematical and Physical Sciences](https://www.sheffield.ac.uk/mps)<br><br>
<img src="https://github.com/user-attachments/assets/7001dc4f-61dd-4629-8bb3-64960ae3bd5f" width="300" height="100"><br><br>
- [SURE Scheme](https://students.sheffield.ac.uk/sure)<br><br>
<img src="https://github.com/user-attachments/assets/9e4a1079-bdeb-4edd-9490-f6caa0fbf6ee" width="250" height="125"><br>

## Contents
- [Abstract](https://github.com/2MY-R/Ameoba-Feature-Extraction/blob/main/README.md#abstract)
## Abstract

**How can artificial intelligence accelerate our understanding of rare, critical biological events?** Due to their infrequent occurrence, rare biological events remain primarily uncharacterised, often pivotal in disease progression or immune response. To bridge this knowledge gap, we propose a machine learning-driven approach to systematically analysing vast microscopy datasets. By leveraging advanced computer vision techniques, we aim to identify and quantify these elusive biological phenomena with unprecedented efficiency.<br><br>
Our study focuses on developing a robust foundation for future artificial intelligence models by extracting essential morphological, temporal and spatial features from amoeba and yeast cells, serving as proxies for macrophages and pathogens. We employed Facebook's Detectron2 to segment and analyse phase-contrast microscopy footage, producing a rich and structured dataset for future analysis. This initial phase involved building upon and tuning a comprehensive feature extraction pipeline to capture the dynamic behaviour of cells.<br><br>
Through this research, we seek to establish a framework for understanding the underlying mechanisms of rare biological events. By uncovering the critical factors influencing these events, we anticipate aiding the development of novel therapeutic strategies and preventative measures. Ultimately, our goal is to harness the power of artificial intelligence to transform our ability to study and intervene in complex biological processes.

## Introduction


## Methodology
&nbsp; This section presents the process we have developed to analyse microscopy images taken in phase-contrast to capture the spatial, temporal, and morphological features of amoebas frame by frame. The procedure is better described in two sections, covering the phase-contrast image segmentation and the post-segmentation processing of these images to generate structured datasets of features which can be used for further research and machine learning models.<br>
  
### Segmentation
Facebook's [Dectectron2](https://github.com/facebookresearch/detectron2) machine vision model was used to segment the phase-contrast images. The model was trained and fine-tuned on a dataset of annotated images, classifying amoebas and yeast. The model was used as a config file in [Segmentation.ipynb](Segmentation.ipynb) to segment PNG images of amoebas and yeast. For this example, a subset of 10 frames was used as a proof of concept for the feature extraction process. Ameoba and yeast were individually segmented using the trained model and stored separately. In this instance, only the amoeba was required. As such, the TIF files folder has been shared and can be viewed using software such as ImageJ. The frames and pre and post-segmentation processing can be seen in Figures 1 and 2, respectively. The choice to use a trained segmentation model over an image processing program such as OTSU is because of the usual and complex shapes amoeba can be found in from frame to frame; therefore, utilising an AI model to segment the images yields a higher level of accuracy in identifying amoeba over a high number of frames. The feature extraction process can begin once this stage has been completed for the desired number of frames. 
<p align = "center">
  <img src="https://github.com/user-attachments/assets/5e362955-3d2d-480f-8c79-93c351bf71ac" width="400" height="400">
</p>
<p align="center">
    <strong>Figure 1:</strong> Shows an example of the images taken in phase-contrast<br>
                of amoeba and yeast.
</p>

<p align = "center">
  <img src="https://github.com/user-attachments/assets/8e21c6c3-238b-46e4-a10e-b1c0e26e3b23" width="400" height="400">
</p>
<p align="center">
    <strong>Figure 2:</strong> A screenshot of a segmented frame opened using Imagej <br>
                of amoeba and yeast in grey and white, respectively.
</p>

### Feature Extraction
The next step in this process is to extract the amoeba's spatial, temporal and morphological features in the phase-contrast images. This process begins using the newly created segmented masks to classify and document each amoeba across all the frames. The tracking process is carried out in [Tracking.ipynb](Tracking.ipynb), which was cleverly written by Rebecca Betts and uses two other frequently called upon PY files ([utils.py](utils.py) and [mask_funcs.py](mask_funcs.py)) containing practical methods used throughout the rest of the project. The classification of amoeba can also be visualised as colour-coded outlines, as shown in [Figure 3](#Figure-3).<br><br> Combining the masks and their tracked progression through each frame allows us to begin analysing the masks in and between frames and collect/store the features of amoeba in pandas data frames. The extraction process is executed by [Feature_Extraction.ipynb](Feature_Extraction.ipynb). The program utilises a two-pronged approach to collecting different features; the first uses torch tensors and methods to analyse the images, and the other implements Scipy's region props library. Torch tensors are used to temporarily store and work with the data given a high number of amoeba that can be present within a frame at varying resolutions; this approach makes the process considerably more manageable; for a similar reason, cells are analysed in batches of 100. The final bit of the code concerns tidying the datasets to reduce the number of invalid data frames and None values, which could disrupt future machine learning processes, with final data frames saved as CSV files inside [final_cells](final_cells). The CSV files can be viewed as tables shown in [Table 1](https://github.com/2MY-R/Ameoba-Feature-Extraction/blob/059b78cf8dc22bf004e3f62e689134c12a0f5154/final_cells/cell_1.csv). Finally, using [plot_cells.ipynb](plot_cells.ipynb), the features are plotted as graphs to represent the extracted data better stored in [feature_plots](feature_plots).


<p align = "center" id='Figure-3'>
  <img src="https://github.com/2MY-R/Ameoba-Feature-Extraction/blob/21f1381981a8c636482a8c28198747ccbc119122/show%20tracks/0000.jpg" width="400" height="400">
</p>
<p align="center">
    <strong>Figure 3:</strong> An example of the classified and tracked amoeba overlayed<br>
                the phase-contrast image.
</p>

## Results
&nbsp; The project has yielded several positive outcomes for the research team I was a part of. My contribution now has streamlined the process of analysing raw phase-contrast images using segmentation and feature extraction. Furthermore, I have expanded upon feature extraction, increasing the number of features being collected/stored by implementing SciPy. I have also begun utilising pandas data frames and nested dictionaries to engineer the extracted data more efficiently. Finally, I improved the data cleaning process to output a directory of only viable cells that can be meaningfully tracked for extended periods. These datasets can be used readily for research and testing going forward.<br><br>
The combined use of the programs allows the collection of amoebas:<br><br>
- Area
- Speed
- Perimeter
- x coordinate
- y coordinate
- Eccentricity (How elliptical the amoeba is 1 being a circle)
- Orientation
- Major-axis
- Minor-axis<br><br>
[feature_plots](feature_plots) shows plots of the most relevant features for each cell, and [Figure 4](#Figure-4) is an example of one of these plots. The full tables of recorded values for each cell can be found in [final_cells](final_cells).
<p align = "center" id='Figure-4'>
  <img src="https://github.com/2MY-R/Ameoba-Feature-Extraction/blob/ad4c6eeeac8e0e44f4ca660d425ca521dd537222/feature_plots/cell_1.png" width="600" height="600">
</p>
<p align="center">
    <strong>Figure 4:</strong> An example of the relevant plots for each ameoba<br>
                against time.
</p>

## Discussion/Conclusion
&nbsp; In Conclusion, There are several ways the code demonstrated can be improved upon, as well as a plethora of new projects which can stem from it.<br><br>
The next step which could be taken to improve the code is to find an improved relation between the computational units produced by the feature extraction program to give a real-world meaning to their output such that researchers in the biological and medical fields can more readily work with the data. Furthermore, updating the tracking application to 'remember' cells as they drift on and off screen would provide a more robust dataset of viable cells. However, this is a minor issue due to the generally slow nature of cells; this would allow for more reliable data capture at the edges of frames.<br><br>

<img src ="https://github.com/user-attachments/assets/7001dc4f-61dd-4629-8bb3-64960ae3bd5f" width="300" height="100">
<img src ="https://github.com/user-attachments/assets/9e4a1079-bdeb-4edd-9490-f6caa0fbf6ee" width="250" height="125">






