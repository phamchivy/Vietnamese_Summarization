# Vietnamese Extractive Text Summarization with PhoBERT

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.11+](https://img.shields.io/badge/python-3.11-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.6.0-ee4c2c.svg)](https://pytorch.org/)

A state-of-the-art Vietnamese text summarization system using PhoBERT and advanced evaluation with FineSurE framework.

## 🎯 Overview

This project implements an extractive text summarization system specifically designed for Vietnamese texts. The system leverages PhoBERT (a Vietnamese-optimized BERT model) with binary classification to identify and extract the most important sentences from multi-document clusters.

### Key Features

- **Vietnamese-Optimized**: Built specifically for Vietnamese text characteristics
- **Multi-Document Summarization**: Handles clusters of related documents
- **Advanced Evaluation**: Integrates FineSurE framework with Google Gemini API

## 📊 Performance

### Training Performance

- **Training Accuracy**: 82.09% (final epoch)
- **Validation Accuracy**: 74.39% (stable across epochs)
- **Convergence**: Fast convergence within 3 epochs
- **Model Size**: PhoBERT-base (768 dimensions)

## 🏗️ Architecture

```
Input Documents → Sentence Segmentation → PhoBERT Encoding → 
Binary Classification → MMR Selection → Summary Output
```

### Model Components

1. **PhoBERT Encoder**: Pre-trained Vietnamese BERT model (768 dimensions)
2. **Binary Classifier**: Dropout (0.3) + Linear layer + Sigmoid activation
3. **MMR Selection**: Maximal Marginal Relevance for sentence selection
4. **FineSurE Evaluation**: Advanced semantic evaluation framework

## 📁 Dataset

**ViMs (Vietnamese Multi-document Summarization)**
- **Total**: 300 clusters (1,945 documents)
- **Used in Study**: 269 clusters for training/validation  
- **Test Set**: 30 clusters for evaluation
- **Average**: 6.0 documents per cluster (5-10 range)
- **Content**: News articles from VnExpress, Dân Trí, Tuổi Trẻ
- **Language**: Vietnamese

### Data Statistics

| Split | Clusters | Sentences | Avg Words/Cluster | Positive Ratio |
|-------|----------|-----------|-------------------|----------------|
| Train | 239 | 4,529 | ~2,500 | 28.1% |
| Validation | 30 | 449 | ~2,500 | 38.5% |
| Test | 30 | Variable | 2,673 | Variable |

## 🚀 Quick Start

### Prerequisites

Google Colab (recommended) or local GPU

### API Configuration

For FineSurE evaluation with **Google Gemini API** (Required):

```python
# Option 1: Google Colab Secrets (Recommended)
from google.colab import userdata
GOOGLE_API_KEY = userdata.get('GOOGLE_API_KEY')

# Option 2: Environment variable
import os
GOOGLE_API_KEY = os.getenv('GOOGLE_API_KEY')

# Get FREE API key: https://aistudio.google.com/app/apikey
```

**⚠️ Important Notes:**
- **FineSurE requires Google Gemini API** for fact-checking evaluation
- **Free tier available**: 15 requests/minute, 1M tokens/day
- **No cost** for research and evaluation purposes
- Alternative APIs (OpenAI, Claude) supported but Gemini recommended

## 📈 Advanced Evaluation

### Real Evaluation Results on ViMs Dataset

| Metric | Score | Standard Deviation | Description |
|--------|-------|-------------------|-------------|
| **ROUGE-1** | 0.3397 | ± 0.1268 | Unigram overlap with reference |
| **ROUGE-2** | 0.2640 | ± 0.0976 | Bigram overlap with reference |
| **ROUGE-L** | 0.2217 | ± 0.0650 | Longest common subsequence |
| **Fluency** | 0.8524 | ± 0.0403 | Linguistic quality score |
| **Coverage** | 0.8894 | ± 0.0364 | Content coverage score |
| **Coherence** | 0.9400 | ± 0.0770 | Logical flow score |

### Advanced Evaluation Metrics

**Traditional Metrics:**
- ROUGE-1, ROUGE-2, ROUGE-L: N-gram overlap assessment
- Compression ratio: Efficiency measurement
- Processing time: Performance benchmarking

**FineSurE Advanced Metrics** (via Gemini API):
- **Factual Consistency**: Information accuracy vs source documents  
- **Semantic Coherence**: Logical flow using Vietnamese context
- **Content Coverage**: Comprehensiveness assessment
- **Fluency Assessment**: Vietnamese linguistic quality

### Evaluation Results Breakdown

**Best Performing Cluster**: Cluster 279 (ROUGE-1: 0.5975)
**Linguistic Quality Metrics**:
- Fluency: 85.24% (Excellent for Vietnamese text)
- Coverage: 88.94% (Comprehensive content capture)  
- Coherence: 94.00% (Outstanding logical structure)

## 📊 Results Analysis

### Performance by Cluster Analysis

Our evaluation on 30 test clusters revealed significant performance variations:

| Performance Tier | ROUGE-1 Range | Clusters | Characteristics |
|-----------------|---------------|----------|-----------------|
| **Excellent** | 0.50 - 0.60 | ~10% | Clear topic focus, good structure |
| **Good** | 0.35 - 0.50 | ~60% | Standard news articles |  
| **Fair** | 0.20 - 0.35 | ~25% | Complex multi-topic clusters |
| **Poor** | < 0.20 | ~5% | Highly technical or fragmented content |

## 🔗 Resources

### Datasets
- [ViMs Dataset](https://github.com/CLC-HCMUS/ViMs-Dataset) - Vietnamese Multi-document Summarization
- [PhoBERT](https://github.com/VinAIResearch/PhoBERT) - Vietnamese BERT model

### Related Work
- [FineSurE](https://github.com/DISL-Lab/FineSurE-ACL24) - Fine-grained Summarization Evaluation
- [Underthesea](https://github.com/undertheseanlp/underthesea) - Vietnamese NLP toolkit

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

- **Author**: Phạm Chí Vỹ
- **Institution**: Hanoi University of Science and Technology (HUST)

---
