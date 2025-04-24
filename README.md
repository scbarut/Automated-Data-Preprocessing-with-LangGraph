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


## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [LangGraph](https://github.com/langchain-ai/langgraph) - For the graph-based workflow framework
- [Google Gemini-1.5-Pro](https://deepmind.google/technologies/gemini/) - For the underlying language model

---

⚠️ **Important Note**: This project requires a Google API key to access the Gemini-1.5-Pro model. Make sure to obtain an API key and store it in your `.env` file as `GOOGLE_API_KEY`. Never commit your API key to version control.
