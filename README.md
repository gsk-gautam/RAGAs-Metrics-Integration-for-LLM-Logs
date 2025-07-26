
# 🔍 RAGAs Metrics Integration for LLM Logs

## 📌 Objective

This project evaluates LLM outputs using **RAGAs metrics**—a set of standardized evaluation scores that measure:

- **Faithfulness**: How well the response aligns with the provided context.
- **Answer Relevancy**: How relevant the answer is to the user query.
- **Context Precision**: How precisely the output uses the context without drifting.

Each log entry contains:
- A `system` prompt (used as *context*)
- A `user` prompt (used as *query*)
- The `expected_output` (used as *answer*)

The goal is to compute RAGAs scores for each entry and export the results in a clean JSON format.

---

## ✅ Approach

1. **Parse the Input**:
   - Read the `logs.json` file, which contains metadata and a list of conversation items.
2. **Extract Prompts**:
   - Use the `system` prompt as *context*, the `user` prompt as *query*, and the assistant response as *answer*.
3. **Compute Scores**:
   - Use a placeholder function to simulate RAGAs metrics.
   - For real applications, integrate a library like `ragas` or custom LLM similarity scorers.
4. **Export Results**:
   - Save scores in `ragas_scores_output.json`.

---

## 🛠️ Libraries Used

| Library | Purpose |
|--------|---------|
| `json` | Read/write structured data |
| `random` | Generate simulated scores |
| *(Optional)* `ragas` | For real metric computation (not used in current simulation) |

---

## ⚙️ Assumptions and Simplifications

- **Score Simulation**: Since no live LLM scoring is integrated, scores are simulated within a realistic range:
  - `faithfulness`: 0.85 – 0.99
  - `answer_relevancy`: 0.80 – 0.98
  - `context_precision`: 0.83 – 0.97
- **Input Format**: Assumes a consistent structure:
  - `input` includes both `system` and `user` roles.
  - `expectedOutput` contains one or more assistant replies.
- **No External Calls**: All scoring is done offline via simulation.

---

## 📁 Project Structure

```
ragas-metrics-integration/
│
├── logs.json                    # Input data
├── ragas_scores_output.json     # Output with computed RAGAs metrics
├── ragas_metric_simulator.py    # Main processing script
├── RAGAs_Metrics_Colab.ipynb    # Optional notebook version
└── README.md                    # This file
```

---

## 🚀 How to Run

### 🖥️ Local Environment

```bash
git clone https://github.com/your-username/ragas-metrics-integration.git
cd ragas-metrics-integration
python ragas_metric_simulator.py
```

Make sure `logs.json` is in the root directory.

### ▶️ Run in Google Colab

- Open [`RAGAs_Metrics_Colab.ipynb`](https://colab.research.google.com/drive/YOUR_NOTEBOOK_ID) (replace with actual link)
- Upload your `logs.json` file
- Run the notebook cells to compute and save the output

---

## 📊 Sample Output

```json
[
  {
    "id": "41ae71ea-59db-46b7-af56-d8f5026ead56",
    "faithfulness": 0.94,
    "answer_relevancy": 0.91,
    "context_precision": 0.96
  }
]
```

---

## 🧠 Future Enhancements

- Replace random scoring with real LLM-based evaluation (e.g., `ragas`, `bertscore`, `GPT4 judge`)
- Add dashboards to visualize metric distributions
- Support batch evaluation and error handling for malformed entries

---

## 📄 License

This project is for educational and internal evaluation purposes. You are free to adapt and extend it for your specific use case.

---
