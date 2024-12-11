# PHI de-identification 
Under the Health Insurance Portability and Accountability Act (HIPAA) minimum necessary standard, HIPAA-covered entities (such as health systems and insurers) are required to make reasonable efforts to ensure that access to Protected Health Information (PHI) is limited to the minimum necessary information to accomplish the intended purpose of particular use, disclosure, or request.

In this solution accelerator we show how to use databricks lakehouse platform and John Snow Lab's SparkOCR and NLP for Health Care pre-trained models to:

1. Store clinical notes in pdf format in deltalake
2. Use [SparkOCR](https://nlp.johnsnowlabs.com/docs/en/ocr) to improve image quality and extract text from pdfs
3. Use [SparkNLP pre-trained models](https://nlp.johnsnowlabs.com/2020/08/04/deidentify_large_en.html) for phi extraction and de-identification


<img src="https://hls-eng-data-public.s3.amazonaws.com/img/phi-deid-ra.png" width=65%>

## Notebooks
<img src="https://hls-eng-data-public.s3.amazonaws.com/img/phi-deid-dataflow.png" width=30%>

 1. `pdf-ocr`: This notebook imports pdf files containing oncology reports and uses sparkOCR for image processing and text extraction. Resulting entities and text are stored in delta
 2. `phi-deidentification`: In this notebook we use pre-trained models to extract phi and mask extracted phi. Resulting obfuscated clinical notes are stored in delta for downstream analysis. 
 3. `config`: Utility notebook for setting up the environment
 
 ## License
Copyright / License info of the notebook. Copyright [2021] the Notebook Authors.  The source in this notebook is provided subject to the [Apache 2.0 License](https://spdx.org/licenses/Apache-2.0.html).  All included or referenced third party libraries are subject to the licenses set forth below.

|Library Name|Library License|Library License URL|Library Source URL| 
| :-: | :-:| :-: | :-:|
|Pandas |BSD 3-Clause License| https://github.com/pandas-dev/pandas/blob/master/LICENSE | https://github.com/pandas-dev/pandas|
|Numpy |BSD 3-Clause License| https://github.com/numpy/numpy/blob/main/LICENSE.txt | https://github.com/numpy/numpy|
|Apache Spark |Apache License 2.0| https://github.com/apache/spark/blob/master/LICENSE | https://github.com/apache/spark/tree/master/python/pyspark|
|Spark NLP |Apache-2.0 License| https://github.com/JohnSnowLabs/spark-nlp/blob/master/LICENSE | https://github.com/JohnSnowLabs/spark-nlp|
|MatPlotLib | | https://github.com/matplotlib/matplotlib/blob/master/LICENSE/LICENSE | https://github.com/matplotlib/matplotlib|
|Pillow (PIL) | HPND License| https://github.com/python-pillow/Pillow/blob/master/LICENSE | https://github.com/python-pillow/Pillow/|
|Spark NLP for Healthcare|[Proprietary license - John Snow Labs Inc.](https://www.johnsnowlabs.com/spark-nlp-health/) |NA|NA|
|Spark OCR |[Proprietary license - John Snow Labs Inc.](https://nlp.johnsnowlabs.com/docs/en/ocr) |NA|NA|

|Author|
|-|
|Databricks Inc.|
|John Snow Labs Inc.|

## Disclaimers
Databricks Inc. (“Databricks”) does not dispense medical, diagnosis, or treatment advice. This Solution Accelerator (“tool”) is for informational purposes only and may not be used as a substitute for professional medical advice, treatment, or diagnosis. This tool may not be used within Databricks to process Protected Health Information (“PHI”) as defined in the Health Insurance Portability and Accountability Act of 1996, unless you have executed with Databricks a contract that allows for processing PHI, an accompanying Business Associate Agreement (BAA), and are running this notebook within a HIPAA Account.  Please note that if you run this notebook within Azure Databricks, your contract with Microsoft applies.

The job configuration is written in the RUNME notebook in json format. The cost associated with running the accelerator is the user's responsibility.

## Instruction
To run this accelerator, set up JSL Partner Connect [AWS](https://docs.databricks.com/integrations/ml/john-snow-labs.html#connect-to-john-snow-labs-using-partner-connect), [Azure](https://learn.microsoft.com/en-us/azure/databricks/integrations/ml/john-snow-labs#--connect-to-john-snow-labs-using-partner-connect) and navigate to **My Subscriptions** tab. Make sure you have a valid subscription for the workspace you clone this repo into, then **install on cluster** as shown in the screenshot below, with the default options. You will receive an email from JSL when the installation completes.

<br>
<img src="https://raw.githubusercontent.com/databricks-industry-solutions/oncology/main/images/JSL_partner_connect_install.png" width=65%>

Once the JSL installation completes successfully, clone this repo into a Databricks workspace. Attach the RUNME notebook to any cluster running a DBR 11.0 or later runtime, and execute the notebook via Run-All. A multi-step-job describing the accelerator pipeline will be created, and the link will be provided. Execute the multi-step-job to see how the pipeline runs.

---

[Deploy to azure](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fsouthworks%2Focr-phi-masking%2Fmain%2Fdeploy-azure%2Fmain.json)
