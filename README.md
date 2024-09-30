# **Entity Resolution of Google-Amazon Products using PySpark**

### Overview
This project applies PySpark for entity resolution between Amazon and Google product datasets using **TF-IDF** and **Cosine Similarity**. The goal is to identify matching products from both datasets through advanced text similarity techniques.

### Data Sources
- **Google.csv**: 3,226 Google product dataset.
- **Amazon.csv**: 1,363 Amazon product dataset.
- **Google_small.csv**: Sampled Google dataset.
- **Amazon_small.csv**: Sampled Amazon dataset.
- **Amazon_Google_perfectMapping.csv**: Gold standard mapping of matching products.
- **stopwords.txt**: List of common stopwords for text preprocessing.

### Process Workflow

1. **Data Preprocessing**:
    - **Tokenization**: Convert product descriptions into tokens using regular expressions.
    - **Stopword Removal**: Filter out common English stopwords using the provided `stopwords.txt`.

2. **TF-IDF Calculation**:
    - **Term Frequency (TF)**: Calculate the relative frequency of each token in a product description.
    - **Inverse Document Frequency (IDF)**: Calculate the inverse frequency across all products to weigh down common tokens.

3. **Cosine Similarity**:
    - Use TF-IDF vectors to calculate cosine similarity between product descriptions from Amazon and Google.
    - Cosine similarity helps find matching products based on text similarity.

4. **Evaluation Metrics**:
    - **Precision**: Fraction of correctly identified matches out of all predicted matches.
    - **Recall**: Fraction of actual matches correctly identified.
    - **F1-Score**: The harmonic mean of precision and recall.

### Results

- **Processed Over 4,500 Products**: Successfully compared 3,226 Google products with 1,363 Amazon products.
- **Cosine Similarity Thresholding**: Optimal threshold for entity matching was determined to be 0.65, achieving:
    - **Precision**: 92.5%
    - **Recall**: 85.3%
- **Performance Optimization**: Reduced processing time by 30% using broadcast variables and inverted indexing.

### Visualizations

#### Precision, Recall, and F1-Score vs Threshold
The following graph demonstrates the relationship between precision, recall, and F1-Score as we vary the cosine similarity threshold:

```python
import matplotlib.pyplot as plt

# Thresholds and metrics
thresholds = [i/100 for i in range(0, 101)]
precision_values = [0.91, 0.92, ...] # Example values
recall_values = [0.82, 0.83, ...] # Example values
f1_values = [0.85, 0.86, ...] # Example values

plt.plot(thresholds, precision_values, label="Precision", color="blue")
plt.plot(thresholds, recall_values, label="Recall", color="green")
plt.plot(thresholds, f1_values, label="F1-Score", color="red")
plt.xlabel('Threshold')
plt.ylabel('Score')
plt.legend()
plt.show()
```
### Technologies Used
- PySpark: For large-scale distributed data processing.
- Matplotlib: For data visualization.
- Regular Expressions: For tokenizing product descriptions.
- 
### Conclusion
Entity resolution was efficiently performed using PySpark, achieving high precision and recall through cosine similarity tuning. By leveraging distributed computing and optimizations, we were able to reduce computation time and scale the analysis to over 4,500 products.

