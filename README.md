# LangGraph Data Preprocessing Pipeline

A sophisticated automated data preprocessing system built with LangGraph and powered by Google's Gemini-1.5-Pro LLM.

![Data Preprocessing Pipeline](https://images.unsplash.com/photo-1607798748738-b15c40d33d57?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80)

## Overview

This project implements an automated data preprocessing pipeline using LangGraph with Google's Gemini-1.5-Pro as the underlying large language model. The system intelligently applies a sequence of data cleaning and transformation operations to prepare datasets for machine learning applications.

## Pipeline Structure

The preprocessing pipeline follows a structured workflow:

```
┌─────────────┐
│  __start__  │
└─────────────┘
       │
       ▼
┌───────────────────────────┐
│ correcting_inconsistent_data │
└───────────────────────────┘
       │
       ▼
┌───────────────┐
│ missing_value │
└───────────────┘
       │
       ▼
┌──────────┐
│ encoding │
└──────────┘
       │
       ▼
┌──────────┐
│  scaler  │
└──────────┘
       │
       ▼
┌────────────┐
│  __end__   │
└────────────┘
```

### Processing Stages

1. **Starting Point** (`__start__`): Initializes the preprocessing workflow
2. **Data Consistency** (`correcting_inconsistent_data`): Identifies and corrects inconsistencies in the dataset
3. **Missing Data Handling** (`missing_value`): Detects and handles missing values using appropriate strategies
4. **Encoding** (`encoding`): Transforms categorical variables into numerical representations
5. **Scaling** (`scaler`): Normalizes numerical features to a standardized range
6. **Completion** (`__end__`): Finalizes the preprocessing workflow

## Prerequisites

- Python 3.10+
- LangGraph
- Google API key for Gemini-1.5-Pro

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/langgraph-preprocessing.git
   cd langgraph-preprocessing
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Create a `.env` file in the project root and add your Google API key:
   ```
   GOOGLE_API_KEY=your_api_key_here
   ```

## Usage

### Basic Example

```python
from pipeline import PreprocessingPipeline

# Initialize the pipeline
pipeline = PreprocessingPipeline()

# Load your dataset
dataset = pd.read_csv("your_dataset.csv")

# Run the preprocessing pipeline
processed_data = pipeline.run(dataset)

# Use the processed data for your machine learning model
model.fit(processed_data)
```

### Custom Configuration

You can customize each step of the pipeline:

```python
from pipeline import PreprocessingPipeline

pipeline = PreprocessingPipeline(
    missing_value_strategy="mean",
    encoding_method="one-hot",
    scaling_method="standard"
)

processed_data = pipeline.run(dataset)
```

## Configuration Options

### Missing Value Handling
- `mean`: Replace missing values with feature mean
- `median`: Replace missing values with feature median
- `mode`: Replace missing values with feature mode
- `constant`: Replace missing values with a constant
- `knn`: Impute missing values using K-Nearest Neighbors

### Encoding Methods
- `one-hot`: One-hot encoding for categorical variables
- `label`: Label encoding for ordinal variables
- `target`: Target encoding for high-cardinality categorical variables

### Scaling Methods
- `standard`: Standardization (zero mean, unit variance)
- `minmax`: Min-Max scaling to a specific range
- `robust`: Scaling using statistics robust to outliers

## Project Structure

```
langgraph-preprocessing/
├── pipeline/
│   ├── __init__.py
│   ├── nodes/
│   │   ├── __init__.py
│   │   ├── consistency.py
│   │   ├── missing_values.py
│   │   ├── encoding.py
│   │   └── scaling.py
│   └── utils.py
├── examples/
│   ├── basic_usage.py
│   └── custom_pipeline.py
├── tests/
│   └── test_pipeline.py
├── .env
├── requirements.txt
└── README.md
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [LangGraph](https://github.com/langchain-ai/langgraph) - For the graph-based workflow framework
- [Google Gemini-1.5-Pro](https://deepmind.google/technologies/gemini/) - For the underlying language model

---

⚠️ **Important Note**: This project requires a Google API key to access the Gemini-1.5-Pro model. Make sure to obtain an API key and store it in your `.env` file as `GOOGLE_API_KEY`. Never commit your API key to version control.