# Mphasis-DeepInsights-Text-Summarizer

Text Summarizer solution is an optimal way to tackle the problem of information overload by reducing the size of long documents into a few sentences . Neural-network-based models have the ability to automatically learn the distributed representation for sentences and documents. This summarizer is built using Transfer Learning and Transformer based models which use self attention. The input can have a maximum of 512 words and gives output of 3 sentences (approximately 30 words).

## Amazon SageMaker

### Input :

**Usage Methodology for the algorithm:**

The input has to be a '.txt' file with 'utf-8' encoding. PLEASE NOTE: If your input .txt file is not 'utf-8' encoded, model will not perform as expected
1. To make sure that your input file is 'UTF-8' encoded please 'Save As' using Encoding as 'UTF-8'
2. The input can have a maximum of 512 words (Sagemaker restriction)
3. Input should have atleast 3 sentences (Model limitation)
4. Supported content types: text/plain

### Output:

Content type: text/plain

### Invoking endpoint

AWS CLI Command
If you are using real time inferencing, please create the endpoint first and then use the following command to invoke it:

`aws sagemaker-runtime invoke-endpoint --endpoint-name "endpoint-name" --body fileb://input.txt --content-type text/plain --accept text/plain result.txt`

**Substitute the following parameters:**

* "endpoint-name" - name of the inference endpoint where the model is deployed
* input.txt - input file
* text/plain - MIME type of the given input file (above)
* result.txt - filename where the inference results are written to.

### Python

Real-time inference snippet (more detailed example can be found in sample notebook):

```sample_txt = 'location of input text file
transformer = model.transformer(1, 'ml.m5.xlarge') 
transformer.transform(sample_txt, content_type="text/plain")
transformer.wait()
print("Batch Transform output saved to " + transformer.output_path)
```

## Resources

1. [Sample Notebook](text_summary_marketplace.ipynb) 
2. [Sample Input](SampleInput)
3. [Sample Output](SampleOutput) 
