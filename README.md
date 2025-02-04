# Customer Segmentation with Local LLM (Ollama)

## Overview
This project performs **customer segmentation** using **local AI models** with **Ollama**. It:
- Generates **text embeddings** for customer job titles and reasons for joining.
- Uses **KMeans clustering** to segment customers.
- Applies **PCA** for visualization.
- Uses a **local LLM** (Llama3.2 or DeepSeek) to generate a customer profile for each segment.

## Features
✅ **Uses Local LLM & Embeddings** – No API costs, works offline.  
✅ **Customizable** – Easily switch between models (`llama3.2:latest` or `deepseek-r1:8b`).  
✅ **Scalable** – Works with any survey dataset.  

## Requirements
- **Python 3.8+**
- **Ollama** (pre-installed with models)
- **Dependencies:**
  ```bash
  pip install pandas numpy matplotlib scikit-learn
  ```

## Models Used
This project requires Ollama to be installed with at least one of the following models:
- **`llama3.2:latest`** (Fast & lightweight, 2GB)
- **`deepseek-r1:8b`** (More powerful, 4.9GB)

To check installed models:
```bash
ollama list
```

## Running the Project
### 1. Load & Preprocess the Data
- Ensure you have a survey dataset (`data/survey.csv`) with at least two columns:
  - `job_title` (Customer’s profession)
  - `join_reason` (Why they joined)

### 2. Generate Embeddings with Ollama
- The script **uses Ollama’s `mxbai-embed-large`** to create embeddings.
- Each `job_title` and `join_reason` is converted into vector representations.

### 3. Clustering & Visualization
- Uses **KMeans clustering** to segment customers.
- Applies **PCA** for reducing dimensionality and visualizing clusters.

### 4. Generate Customer Profiles using Local LLM
- Each segment is passed to a **local LLM (Llama3.2 or DeepSeek)**.
- The model generates a **customer avatar** summarizing key characteristics.

## Switching Between LLM Models
By default, the script uses **`llama3.2:latest`**. To use **DeepSeek**, modify this line:
```python
response = ollama.chat(model="deepseek-r1:8b", messages=[{"role": "user", "content": prompt}])
```

## Example Output
```
Segment 1 | Size: 34
**Job Title:** Data Scientist
**Desired Outcomes:** Improve AI skills for better job prospects
**Key Challenges:** Lack of hands-on projects
--------------------------------------------------
Segment 2 | Size: 27
**Job Title:** Software Engineer
**Desired Outcomes:** Transition into AI & ML roles
**Key Challenges:** Limited experience with deep learning
--------------------------------------------------
```

## Notes
- The more **data** you provide, the **better** the segmentation results.
- If embeddings take **too long**, consider a **smaller embedding model**.
- If results aren’t **detailed enough**, try using **`deepseek-r1:8b`**.

## Author
Developed by **Karthik** 🚀

