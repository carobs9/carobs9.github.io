---
title: "Directory-to-Graph Visualization"
excerpt: "Turn any folder into an interactive tree graph in the browser."
collection: portfolio
permalink: /portfolio/dir-to-graph/
---

> Visual tool to explore folder structures as interactive trees. A small Python CLI walks a directory, exports a JSON tree, and a D3.js viewer renders it as a zoomable, collapsible graph.

## Project at a Glance

`dir_to_graph` is a lightweight toolkit for understanding the structure and size of any folder on your machine. It has two main pieces:

- A **Python CLI** (`dir-to-graph`) that walks a directory and produces a `data.json` file describing the tree (folders, files, and their sizes).
- An **HTML/D3.js viewer** (`index.html`) that reads `data.json` and renders an interactive tree diagram, with node size roughly proportional to size on disk.

You point it at a directory, generate the JSON once, and then browse the hierarchy visually in your browser.

## How It Works

1. **Directory walk**  
   The CLI traverses the directory recursively with sensible defaults for ignored paths (e.g., `.git`, virtualenvs, `__pycache__`, etc.).

2. **Tree and metadata**  
   For each folder and file, the tool records:
   - `id`: full absolute path (unique per node)
   - `name`: short basename used as the label
   - `type`: `"folder"` or `"file"`
   - `size_bytes`: file/folder size in bytes (or `None` if skipped or out of budget)
   - `children`: list of child nodes

3. **Time-bounded size calculation**  
   For very large trees, you can pass a **time budget** (`--max-seconds`) so folder-size computation aborts gracefully instead of hanging. When the budget is exceeded, remaining sizes are set to `None` but the tree is still fully built.

4. **JSON output**  
   The tree is serialized into a D3-friendly JSON structure using `networkx.readwrite.json_graph.tree_data` and written to `data.json`.

5. **Visualization**  
   `index.html` loads `data.json`, converts it into a `d3.hierarchy`, applies `d3.tree`, and renders:
   - Circles for nodes (folders in one color, files in another)
   - Curved links between parent and children
   - Tooltips with full path and human-readable size (e.g., KB/MB/GB)
   - Click-to-expand/collapse behavior for folders

## Example Usage

From the repository root:

```bash
cd dir_to_graph
python main.py /path/to/your/directory
```

This will:

- Walk `/path/to/your/directory`.
- Generate a `data.json` describing the tree.
- Save it (by default) in your current working directory.

Then start a simple HTTP server and open the viewer:

```bash
python -m http.server 8000
# In your browser: http://localhost:8000/index.html
```

With `index.html` and `data.json` in the same folder, the tree visualization will appear and you can interactively explore the directory.

## CLI Options

The CLI supports a few useful flags:

- `PATH` (positional, optional): directory to analyze (default: current directory).
- `-o, --output-dir`: where to write `data.json` (default: current working directory).
- `-i, --ignore`: directory names to ignore (can be passed multiple times; defaults include `.git`, `.venv`, `bin`, `__pycache__`, `.ipynb_checkpoints`).
- `--max-seconds`: approximate time budget for computing folder sizes (default: `15.0`; `0` disables the limit).

These options make it easy to run the tool on everything from a tiny project folder to a large codebase, while keeping performance under control.

## Python Library API

Beyond the CLI, you can also use `dir_to_graph` as a regular Python library:

```python
from dir_to_graph import build_tree_json, write_tree_json

tree = build_tree_json("/path/to/dir", max_seconds=10)
print(tree["name"], tree["children"][0]["name"])

out_path = write_tree_json("/path/to/dir", output_dir=".", filename="data.json")
print("wrote", out_path)
```

This is handy when you want to embed directory visualizations into other applications, scripts, or notebooks.

## What I Focused On

- Designing a **clear JSON schema** that works smoothly with `d3.hierarchy`.
- Handling **large directories** gracefully with time-limited size computation.
- Building a **simple, self-contained viewer** (single `index.html`) that you can drop into any static server.
- Keeping the codebase readable and extensible for future visualizations (e.g., different layouts or color encodings).

## Tech Stack

- **Python 3.10+**
- **NetworkX** for graph representation and JSON export
- **NumPy** (dependency of some graph operations)
- **D3.js** for the interactive browser visualization
- Standard library modules: `os`, `json`, `time`, `argparse`

## Explore the Code

You can find the full implementation, README, and usage details here:

- GitHub repository: [carobs9/dir_to_graph](https://github.com/carobs9/dir_to_graph)

This portfolio entry gives the high-level overview; the repository dives into installation, requirements, and more usage examples.