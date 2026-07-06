Knowledge Graph Generation and Visualization

This project demonstrates how to generate synthetic personal and job data, construct a knowledge graph from that data, and visualize it in both 2D and interactive 3D formats. It also includes utilities for searching within the graph and saving/loading it from disk.



📚 Table of Contents

Overview

Features

Installation

Usage

Notebook Sections

Saving \& Loading Graphs

Project Structure

License



🧠 Overview

Knowledge graphs are powerful tools for representing relationships between entities. This notebook walks through:



Creating synthetic datasets

Building a multi‑type node graph

Visualizing the graph in 2D and 3D

Highlighting nodes based on search

Persisting the graph to disk



It is designed as an educational and exploratory resource for anyone interested in graph‑based data modeling.



✨ Features

Synthetic Data Generation  

Create mock personal and job datasets for experimentation.



Knowledge Graph Construction  

Build a graph with people, jobs, job titles, and departments using networkx.



2D Visualization  

Static graph rendering using matplotlib.



Interactive 3D Visualization  

Explore the graph in 3D using plotly.



Search \& Highlight  

Find nodes and visually emphasize them and their neighbors.



Graph Persistence  

Save and load graphs using .graphml.



🔧 Installation

Install required dependencies:



bash

pip install pandas networkx matplotlib plotly

Or simply run the notebook — missing packages will be installed automatically.



▶️ Usage



Open the notebook in Jupyter or VS Code.

Run all cells sequentially from top to bottom.

Interact with the 3D graph to explore relationships.

Use the search function to highlight specific nodes.

Save the graph to disk when needed.



📘 Notebook Sections

1\. Generate Synthetic Personal Data

Creates a DataFrame with fields such as:



person\_id

name

age

gender



2\. Generate Synthetic Job Data

Builds a job dataset linked to individuals:



job\_id

person\_id

job\_title

department

start\_date



3\. Build the Knowledge Graph

Constructs a networkx graph with:



Person nodes

Job nodes

Job title nodes

Department nodes



Edges represent relationships like:



holds\_job

has\_title

in\_department



4\. Visualize the Knowledge Graph (2D)

Uses matplotlib to render a static 2D graph with color‑coded node types.



5\. Install Plotly for 3D Visualization

Ensures plotly is available for interactive rendering.



6\. Visualize the Knowledge Graph (Interactive 3D)

Creates a fully interactive 3D graph using plotly.graph\_objects.



7\. Add Search and Highlight Functionality

Allows users to:



Search for a node

Highlight it in red

Highlight its immediate neighbors



8\. Save the Graph to Disk

Exports the graph as:



Code

knowledge\_graph.graphml

9\. Load the Graph from Disk

Demonstrates how to reload the saved graph and verify its structure.



📁 Project Structure

Code

├── knowledge\_graph.ipynb

├── knowledge\_graph.graphml   # generated after saving

└── README.md



📄 License
This project is open‑source under the MIT License.

