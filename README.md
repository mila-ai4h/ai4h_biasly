# Biasly: An Expert-Annotated Dataset for Subtle Misogyny Detection and Mitigation

This repository contains details about the dataset presented in the paper, Biasly: An Expert-Annotated Dataset for Subtle Misogyny Detection and Mitigation. The dataset itself can be accessed through our [Hugging Face repository](https://huggingface.co/datasets/mila-ai4h/biasly-data). 

The dataset is the first of its kind in that it provides detailed annotations for each misogynsitic instance, including sub-categories of misogyny, a continuous severity score, and potentially a rewritten version of the original datapoit with the misogyny reduced or entirely removed. More information on the dataset can be found in the original paper, to be published in ACL Findings 2024.

## The Dataset

The Biasly dataset consists of 10,000 unique datapoints, each annotated by threee different annotators, for a total of 30,000 annotations. More information on the raw data, annotation pipeline, and structure of the dataset is given below.

### Raw Data

The Biasly dataset consists of three-sentence pieces of text that originally came from movie subtitle data from North American films produced between 2012-2022 from The Movie Corpus at english-corpora.org. We filtered out documentaries as well as period pieces so that the corpus focuses on contemporary, colloquial language. The raw data, after being parsed into three-sentence datapoints, is also available on our [Hugging Face repository](https://huggingface.co/datasets/mila-ai4h/biasly-data).

### Annotation Pipeline

The annotation pipeline for each three-sentence datapoint is summarized below.

<img width="628" alt="biasly_figure1_revisions" src="https://github.com/brooklynsheppard/biasly_test/assets/96358007/a75839f9-d4f5-4b08-b331-360e6b008c6b">

### Dataset Structure

The dataset consists of the following columns for each instance. Note that many of the annotations rely on the datapoint first being labeled as misogynsitic, so in many cases, these columns are left empty.

`datapoint_id`: Each unique datapoint has a unique uuid. Since each datapoint was annotated three times, each uuid appears three times in the dataset.<br /> 
`datapoint`: The three-sentence bit of text that was annotated.<br /> 
`is_misogynistic`: Yes, No, or Unclear.<br /> 
`why_unclear`: If labeled as unclear, annotators were asked to provide an explanation as to why it was unclear.<br /> 
`misogynistic_inferences`: Contains one or more subcategories of misogyny from the list provided in Table 2 in the original paper.<br /> 
`other_inferences`: If the datapoint contained additional msiogynsitic inferences that were not a part of the subcategories provided, annotators were able to add their own inferences using free text.<br />
`inferences_explanation`: Annotators could optionally provide an explanation as to why they chose the misogynistic inference categories they did.<br /> 
`original_severity`: The severity of the misogyny within the datapoint. Ranges from 0 to 1000.<br />
`rewrite_possible`: Whether or not it was possible for the annotator to rewrite the datapoint to reduce or remove the misogyny. Either "Possible" or "Not Possible".<br /> 
`rewrite`: The datapoint, rewritten to remove or reduce the misogyny.<br /> 
`rewrite_severity`: The severity of the misogyny of the rewritten version.<br /> 
`annotator_id`: The id of the annotator. Ranges from A1 to A10.<br /> 
`annotator_background`: Academic background of the annotator. Either "Linguistics" or "Gender Studies".

## Contacts

For any questions regarding using the dataset for model training, please contact the co-first author, Brooklyn Sheppard, at brooklyn.sheppard1@ucalgary.ca

For any other questions, please contact the corresponding author, Allison Cohen at allison.cohen@mila.quebec
