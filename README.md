# AI Driven discovery; Rare Celluar Behaviour

## Contributions 
- **Author**: Toumai Rouse
- **Supervisor:** Ashley Cadby
- **Co-Supervisors:** Rebecca Betts, Olga Chambers

This project could have only been done with my supervisor/co-supervisors' help, support, and advice. Futhermore, I was provided with a solid foundation of code to build off of and collaborate with to support the whole research team; as Olga and Rebecca have previously written, much of the code I am presenting. I have used their code and advice as a stepping stone to add my contribution to the broader project.

## Affiliations
- [School of Mathematical and Physical Sciences](https://www.sheffield.ac.uk/mps)<br><br>
<img src="https://github.com/user-attachments/assets/7001dc4f-61dd-4629-8bb3-64960ae3bd5f" width="300" height="100"><br><br>
- [SURE Scheme](https://students.sheffield.ac.uk/sure)<br><br>
<img src="https://github.com/user-attachments/assets/9e4a1079-bdeb-4edd-9490-f6caa0fbf6ee" width="250" height="100"><br>

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
Facebook's [Dectectron2](https://github.com/facebookresearch/detectron2) machine vision model was used to segment the phase-contrast images. The model was trained and fine-tuned on a dataset of annotated images, classifying amoebas and yeast. 

### Feature Extraction
## Results
## Discussion/Conclusion
