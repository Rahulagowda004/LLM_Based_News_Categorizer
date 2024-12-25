# News Classifier using DistilBERT

## Model Description

- **Developed by**: Rahul A Gowda
- **Model Type**: Encoder Based Model
- **License**: Apache-2.0
- **Fine-tuned from model**: DistilBERT-base-uncased
- **Repository**: [LLM-Based News Categorizer](https://github.com/Rahulagowda004/LLM_Based_News_Categorizer)

This model is fine-tuned for the task of news article classification, categorizing articles into four classes: World, Sports, Business, and Sci/Tech. The fine-tuning was done using the AG-News dataset.

## How to Get Started with the Model

### Installation

To use this model, you need to install the `transformers` library. You can do this with the following command:

```bash
pip install transformers
```

### Using the Model

#### Using the Pipeline API

You can easily classify text using the high-level `pipeline` API from Hugging Face. Here's how to get started:

```python
from transformers import pipeline

pipe = pipeline("text-classification", model="rahul004/News-Categorizer")

# Example of usage
result = pipe("Tesla's stock price hits a new high!")
print(result)
```

#### Loading the Model Directly

If you prefer more control over the tokenization and model inference, you can load the model and tokenizer manually:

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("rahul004/News-Categorizer")
model = AutoModelForSequenceClassification.from_pretrained("rahul004/News-Categorizer")

# Example of usage
text = "Apple announces new iPhone features at annual event"
inputs = tokenizer(text, return_tensors="pt", truncation=True, padding=True)

outputs = model(**inputs)
print(outputs)
```

## Training Data

The model has been fine-tuned on the **AG-News** dataset. This dataset consists of news articles classified into four categories:

- **World**: Articles related to world news.
- **Sports**: Articles about sports events and topics.
- **Business**: Articles focused on business and financial news.
- **Sci/Tech**: Articles related to science and technology.

## Training Details

- **Number of Epochs**: 4
- **Training Loss**: 0.124300
- **Validation Loss**: 0.920658
- **Accuracy**: 92.06%
- **F1 Score**: 92.05%

## How to Fine-Tune the Model

If you wish to fine-tune this model on your own dataset, you can use the following approach:

1. Load the dataset using Hugging Face's `datasets` library.
2. Tokenize the dataset using the pre-trained tokenizer.
3. Define the training arguments and metrics (like accuracy and F1 score).
4. Use the `Trainer` API to train the model.

Refer to the [Hugging Face documentation](https://huggingface.co/docs) for more details on fine-tuning models.

## Model Evaluation

The model was evaluated on the validation set of the AG-News dataset. The evaluation results are as follows:

- **Training Loss**: 0.124300
- **Validation Loss**: 0.920658
- **Accuracy**: 92.06%
- **F1 Score**: 92.05%

These metrics demonstrate the effectiveness of the fine-tuning process, and the model achieves high accuracy in classifying news articles.

## License

This model is licensed under the Apache-2.0 license. See the LICENSE file for more details.

## Model Card

You can find the model card on the Hugging Face Model Hub here: [News Classifier Model](https://huggingface.co/rahul004/News-Categorizer)

---

### Acknowledgments

This model was trained using the AG-News dataset, and Hugging Face's Transformers library was instrumental in the fine-tuning process. Thanks to the open-source community for providing these resources.
```
