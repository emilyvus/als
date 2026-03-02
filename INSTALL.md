# 🧬 ALS Project — Installation & Setup Guide

---

## 📋 Prerequisites

- [Conda](https://docs.conda.io/en/latest/miniconda.html) (Miniconda or Anaconda) installed on your system
- Git (to clone the repository)

---

## 🐧 Step 1 — Create a Conda Environment

### On **Linux** 🐧 or **macOS** 🍎

Open a terminal and run:

```bash
conda create -n als python=3.12 -y
```

> 💡 This creates a new isolated environment named **`als`** with Python 3.12.

Activate the environment:

```bash
conda activate als
```

You should see `(als)` at the beginning of your terminal prompt.

---

## 📦 Step 2 — Install Dependencies from `pyproject.toml`

Make sure you are in the root directory of the project (where `pyproject.toml` is located), then run:

```bash
pip install -e .
```

> 🔧 The `-e` flag installs the project in **editable mode**, so any local changes are immediately reflected without reinstalling.

This will install all required packages including:

| Package | Purpose |
|---|---|
| `numpy` | Numerical computing |
| `pandas` | Data manipulation |
| `scipy` | Scientific computing & statistics |
| `scikit-learn` | Machine learning (clustering, regression, SVM) |
| `matplotlib` | Plotting & visualization |
| `seaborn` | Statistical data visualization |
| `jupyterlab` | JupyterLab IDE |
| `notebook` | Classic Jupyter Notebook |
| `ipykernel` | Jupyter kernel for Python |

---

## 🔌 Step 3 — Register the Conda Environment as a Jupyter Kernel

```bash
python -m ipykernel install --user --name als --display-name "Python (als)"
```

> ✅ This makes the `als` environment available as a kernel inside JupyterLab and Jupyter Notebook.

---

## 🚀 Step 4 — Launch Jupyter and Run the Notebooks

### Option A — JupyterLab (recommended)

```bash
jupyter lab
```

### Option B — Classic Jupyter Notebook

```bash
jupyter notebook
```

Both commands will open a browser window. Navigate to the **`notebooks/`** folder and open any `.ipynb` file.

> 🌐 If the browser does not open automatically, copy the URL printed in the terminal (e.g., `http://localhost:8888/lab?token=...`) and paste it into your browser.

---

## 📂 Available Notebooks

| Notebook | Description |
|---|---|
| `clustering_comparison_SC.ipynb` | Comparison of clustering methods on variant data |
| `population_level_validation_tsne.ipynb` | Population-level validation using t-SNE |
| `genome_level_validation_pca.ipynb` | Genome-level validation using PCA |
| `gene_level_validation_heatmap.ipynb` | Gene-level validation using heatmaps |
| `als2als_prediction_SOD1.ipynb` | ML prediction of SOD1 gene variant counts using cluster-based leave-one-out validation |

---

## 🛑 Deactivating the Environment

When you are done, deactivate the conda environment:

```bash
conda deactivate
```

---

## 🗑️ Removing the Environment (Optional)

To completely remove the `als` environment:

```bash
conda remove -n als --all -y
```

---

## ❓ Troubleshooting

- **`conda: command not found`** — Make sure Conda is installed and your shell is initialized: `conda init bash` (or `zsh`), then restart your terminal.
- **Kernel not showing in Jupyter** — Re-run the `ipykernel install` command from Step 3.
- **Package conflicts** — Try upgrading pip first: `pip install --upgrade pip`, then re-run `pip install -e .`