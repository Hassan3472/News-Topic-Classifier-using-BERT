
# News-Topic-Classifier-using-BERT

## Project Overview
This project focuses on fine-tuning a BERT model for news topic classification. The goal is to classify news headlines into four distinct categories: World, Sports, Business, and Sci/Tech.

## Objective
The primary objective is to build an accurate and efficient news topic classifier using a pre-trained BERT model, demonstrating the fine-tuning process and providing a live inference demo.

## Dataset Source
The dataset used is the AG News dataset, which contains real news headlines. A subset of 4,000 training samples and 800 test samples was used for faster training on a free Colab GPU.

## Data Validation Performed
- **Dataset Loading**: Verified that the AG News dataset was loaded correctly from Hugging Face, confirming the number of samples in the full train and test sets.
- **Subset Creation**: Ensured that the specified subset sizes for training (4,000 samples) and testing (800 samples) were correctly applied.
- **Tokenization**: Applied `BertTokenizer` with `truncation=True`, `padding=True`, and `max_length=128` to convert text into numerical representations. The tokenizer's output format was set to PyTorch tensors.
- **Label Renaming**: Renamed the 'label' column to 'labels' to meet the Hugging Face Trainer's expectations.

## Models Used
- **Pre-trained Model**: `bert-base-uncased` from Hugging Face Transformers library.
- **Classification Head**: A 4-class classification head was added on top of the BERT model to predict the news topics.

## Hyperparameter Tuning
The following hyperparameters were used for fine-tuning:
- **Number of Training Epochs**: 10
- **Per Device Train Batch Size**: 16
- **Per Device Eval Batch Size**: 32
- **Learning Rate**: 2e-5
- **Weight Decay**: 0.01
- **Evaluation Steps**: 250 (approximately once per epoch)
- **Save Steps**: 250 (approximately once per epoch)

## Evaluation Metrics
The model's performance was evaluated using:
- **Accuracy**: The proportion of correctly classified samples.
- **F1-Score**: The weighted average of precision and recall, providing a balanced measure of the model's performance, especially useful for imbalanced classes (though not explicitly handled here, it's a good general metric).

## Best Model
The model was trained for 10 epochs. The final evaluation results after training indicate the performance of the fine-tuned model.

## Pipeline Export
The fine-tuned model and its tokenizer were saved to the `./saved_model` directory.

## Key Results
**Initial Evaluation (before training):**
- Accuracy : 25.50%
- F1 Score : 10.66%
- Eval Loss: 1.4560

**Final Evaluation (after training):**
- Accuracy  : 91.13%
- F1 Score  : 91.16%
- Eval Loss : 0.5484

The fine-tuned BERT model achieved high accuracy and F1-score on the test set, demonstrating its effectiveness in classifying news headlines into the specified categories. A Gradio interface was deployed to provide a live demo of the classifier.

