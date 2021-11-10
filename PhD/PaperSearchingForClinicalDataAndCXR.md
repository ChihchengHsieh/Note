## No clinical data

### [Predicting COVID-19 Pneumonia Severity on Chest X-ray With Deep Learning](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7451075/)

This paper feed the CXR image as input and get multiple binary and numerical output. It doens't use clinical data in the application.

### [Clinically Accurate Chest X-Ray Report Generation](http://proceedings.mlr.press/v106/liu19a/liu19a.pdf)

This paper using the CXR image only to generate keywords for the text report. Then, it use reinforcement learning to contruct those keywords to sentences.

### [Creation and validation of a chest X-ray dataset with eye-tracking and report dictation for AI development](https://www.nature.com/articles/s41597-021-00863-5)

This is the paper for CXR dataset, it provide two examples in the end of the paper. The first one using eye tracking data to boost the performance of model (prediction model). The second experiments using CXR image only to generate the fixation heatmap and the decision.

### [PadChest: A large chest x-ray image dataset with multi-label annotated reports](https://www.sciencedirect.com/science/article/pii/S1361841520301614)
Just a dataset paper with some annotation strategy.

### [Multi-modal Understanding and Generation for Medical Images and Text via Vision-Language Pre-Training](https://arxiv.org/abs/2105.11333)

The one from Kore. It talks about pre-training and multimodal learning. However, it sitll feed the report text as input. And, it perform multitask learninig, which can generate multiple outputs for different tasks, including Diagnosis Classification, Image-Report Retrieval, Medical Visual Question Answering and Radiology Report Generation.


### [Clinically Accurate Chest X-Ray Report Generation](http://proceedings.mlr.press/v106/liu19a.htmlx)
Cool one using the CXR image to generate the topics of the report. Then, conditionally generate the sentences corresponding to these topics. And the end, a reinforcement learning system is used for fine-tuning readibility and clinical accuracy. This paper uses both MIMIC and OPEN-I.

## Have clinical data
