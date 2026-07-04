# AI Data Analysis

A hands-on educational project demonstrating how to use **Python + Scikit-Learn + OpenAI API** to analyze financial customer data, generate predictions, and produce AI-assisted reports.

The content is presented as a **Jupyter Notebook**, interleaving code cells with Markdown explanations, aiming to be a clear, step-by-step, educational walkthrough.

## About the project

The notebook is split into two complementary examples:

### 1. Large-scale analysis and credit score prediction

A financial institution wants to reward customers with a good credit history, but the sheer number of customers makes manual review impractical. The notebook walks through a full classification pipeline:

- Reading the customer dataset (`assets/clientes.csv`) with `pandas`;
- Encoding categorical columns (profession, credit mix, payment behavior) with `LabelEncoder`;
- Splitting the data into training and test sets (`train_test_split`);
- Training two classification models — `RandomForestClassifier` and `KNeighborsClassifier` — to predict the `score_credito` column (`Good`, `Standard`, `Poor`);
- Comparing model accuracy (`accuracy_score`) to pick the best-performing one;
- Using the winning model to predict scores for a new batch of customers (`assets/novos_clientes.csv`).

### 2. Report generation via prompt

With predictions in hand, the second example shows how to turn that raw output into something readable for non-technical stakeholders:

- Visualizing the score distribution with a histogram (`plotly.express`);
- Filtering the customers eligible for the benefit (score `Good`);
- Sending that data as context to the **OpenAI API**, using a system prompt that instructs the model to act as a formal report generator;
- Automatically generating a text report ready for the company to use.

## Tech stack

- **Python 3**
- **Jupyter Notebook**
- **pandas** — data loading and manipulation
- **scikit-learn** — preprocessing (`LabelEncoder`), train/test split, and classification models (`RandomForestClassifier`, `KNeighborsClassifier`)
- **plotly** — data visualization (histogram)
- **openai** — report generation via the OpenAI API
- **python-dotenv** — environment variable loading (API key)

## Repository structure

```
AI_DataAnalysis/
├── assets/
│   ├── clientes.csv                          # Customer dataset used to train and test the models
│   ├── novos_clientes.csv                    # New customers, without a credit score, to be predicted
│   └── Apostila Jornada Python - Aula 3.pdf  # Supporting course material for the lesson this project is based on
├── main.ipynb                                # Main notebook with both examples
├── requirements.txt                          # Project dependencies
└── .gitignore
```

## Getting started

### Prerequisites

- Python 3.10+ installed
- An OpenAI API key (only required for the report-generation part)

### Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/VitaoDeveloper/AI_DataAnalysis.git
   cd AI_DataAnalysis
   ```

2. Create and activate a virtual environment (recommended):
   ```bash
   python -m venv .venv
   source .venv/bin/activate      # Linux/macOS
   .venv\Scripts\activate         # Windows
   ```

3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file in the project root with your OpenAI key:
   ```
   OPENAI_API_KEY=your_key_here
   ```

5. Open the notebook:
   ```bash
   jupyter lab main.ipynb
   ```
   or open `main.ipynb` directly in VS Code / Jupyter Notebook and run the cells in order.

> The first part of the notebook (credit score prediction) works without an API key. The key is only needed to run the final cells, which generate the report using the OpenAI API.

## About the data

The datasets (`clientes.csv` and `novos_clientes.csv`) contain financial and behavioral information for fictional customers — age, profession, annual salary, number of accounts and cards, payment history, total debt, and more — used as input features to predict `score_credito`.

## Context

This project was built as a practical exercise for a lesson on AI-powered data analysis, combining traditional Machine Learning concepts (supervised classification) with LLM-based natural language generation from data results.

## License

This project currently has no defined license. Feel free to use it as a study reference.
