# Lightweight Phishing Email Detection for SMEs

 

Can a simple machine learning model catch phishing emails, including AI-written ones, almost as well as a transformer, at a fraction of the computing cost?

 

This is my MSc Applied IT research project at Wintec (INFO802 Research in IT).

 

## Problem

 

Generative AI helps attackers write polished, convincing phishing emails. Small and medium-sized enterprises (SMEs) rarely have the budget, staff or hardware to run the heavy models that lead published detection studies. This project measures detection performance and computing cost side by side in one controlled experiment.

 

## Data

 

- **Dataset 1:** Kaggle Phishing Email Dataset (Alam, 2024). After cleaning, 82,077 emails remained. I used a stratified sample of 20,000 emails, split into 16,000 for training and 4,000 for testing. [Kaggle dataset link]

- **Dataset 2:** AI-generated phishing corpus (Eze & Shamir, 2024). 713 unique emails, paired with 713 legitimate emails to make a balanced test set of 1,426. This data is not included in this repository. [Original source link]

 

## Method

 

A quantitative experiment. Every model used the same cleaned data, 80/20 split, metrics and random seed (42).

 

- **Naïve Bayes** with TF-IDF features

- **Logistic Regression** with TF-IDF features

- **DistilBERT**, fine-tuned for two epochs on a Tesla T4 GPU

 

## Results

 

| Model | F1 (%) | Recall on AI-generated phishing (%) | Training time (s) | Model size (MB) |

| --- | --- | --- | --- | --- |

| Naïve Bayes | 96.8 | 55.4 | 52.6 | 3.6 |

| Logistic Regression | 98.1 | 88.5 | 40.4 | 2.4 |

| DistilBERT | 98.6 | 32.1 | 197.8 | 267.8 |

 

Key findings:

 

- Logistic Regression scored within 0.5 F1 points of DistilBERT.

- DistilBERT trained about 4.9 times slower and its model was 109 times larger.

- Logistic Regression caught 88.5% of AI-generated phishing, against 32.1% for DistilBERT.

 

## Tools

 

Python, scikit-learn, Hugging Face Transformers, Google Colab, Excel.

 

## How to run

 

1. Open the notebook in Google Colab: [Colab notebook link]

2. Download Dataset 1 from Kaggle and upload it to Colab.

3. Choose a GPU runtime, then select Runtime > Run all.

 

## Limitations

 

- The AI-generated corpus is small and comes from one generator (DeepAI).

- I used one sample and one random seed, without a formal significance test.

- DistilBERT ran on a GPU and the lightweight models on a CPU.

 

## Ethics

 

I used only public, secondary data and no human participants. No email text is quoted, the AI-generated corpus was used only to test detection and was not redistributed, and I created no new phishing emails.

 

## Author

 

Chandima Sewwandi Widyathilaka Wipulaguna, MSc Applied IT student, Wintec, Hamilton, New Zealand.

LinkedIn: [www.linkedin.com/in/chandima-sewwandi-88379bb1]
