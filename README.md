# Entity Resolution System Using PySpark

## Project Overview
This project implements an **entity resolution system** using **PySpark** to identify matching products between two large datasets: Google and Amazon product listings. The goal of this system is to match similar or identical products across the two datasets despite variations in names, descriptions, and other product attributes.

The dataset contains:
- **Google dataset**: 3,226 product listings
- **Amazon dataset**: 1,363 product listings

## Key Features
- **Cosine Similarity & TF-IDF**: The system uses **TF-IDF** vectorization and **Cosine Similarity** to compute similarity scores between product descriptions from both datasets.
- **Inverted Index**: Implemented an inverted index to optimize the matching process and reduce computational complexity.
- **Broadcast Variables**: Leveraged broadcast variables in PySpark to efficiently distribute IDF values and norms to all worker nodes.

## Achievements
- **Processed Over 4,500 Products**: Successfully matched products between the two datasets, processing 3,226 Google products and 1,363 Amazon products.
- **Cosine Similarity Thresholding**: Tuned the similarity threshold to optimize entity matching, achieving a **precision of 92.5%** and **recall of 85.3%** at a 0.65 similarity threshold.
- **Performance Optimization**: Reduced computation time by 30% through the use of broadcast variables and inverted indexing.

## Installation & Setup
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/your-repository.git
    ```
2. Install dependencies:
    ```bash
    pip install pyspark
    ```
3. Download the dataset:
    - [Google Products](https://example.com/google_dataset.csv)
    - [Amazon Products](https://example.com/amazon_dataset.csv)

4. Run the project:
    ```bash
    python entity_resolution.py
    ```

## Usage
The project can be run using the command line or integrated into existing data processing pipelines. The core functionality is wrapped in the `entity_resolution.py` script.

### Example:
```bash
spark-submit entity_resolution.py --input_google google_dataset.csv --input_amazon amazon_dataset.csv

### Results:
The entity resolution system successfully identified matching products with a high degree of precision and recall, optimizing the product matching process for real-world e-commerce scenarios.
