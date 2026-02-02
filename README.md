# README

## Project Overview

This system provides a multi-faceted approach to tourist recommendations by analyzing 300 POIs across four European cities: Paris, Rome, Madrid, and Kaunas. The project integrates big data tools to handle computationally intensive tasks like feature extraction and similarity measurements.

## Key Objectives

* Efficiently process and store diverse POI data using a relational PostgreSQL database.


* Implement robust similarity algorithms, including structural analysis (Jaccard Index) and image-based analysis (VGG16 and Dominant Color).


* Calculate POI importance scores using the PageRank algorithm.


* Deliver a responsive, user-friendly interface through a Django web application.



## Technical Architecture

### 1. Data Processing (MPI)

The project uses MPI (via `mpi4py`) to parallelize heavy workloads, significantly reducing processing time compared to sequential execution.

* **VGG16 Features:** Extracts 4096-dimensional vectors representing high-level image content.


* **Dominant Colors:** Uses K-Means clustering () to find representative color palettes.


* **Structural Similarity:** Employs the Jaccard Index to measure similarity based on shared categories within a city.



### 2. Recommendation Engine

The engine identifies the 'k' most similar items using several metrics:

* 
**Image Similarity:** Pairwise Cosine Similarity between VGG16 vectors and normalized color vectors.


* 
**PageRank Score:** Builds a graph using structural similarity as weighted edges to determine the "importance" of each POI.



### 3. Web Application (Django)

* **Models:** Defines the schema for Cities, Places, Categories, and pre-computed Similarities.


* **Views:** Handles user requests for city listings and detailed POI views.


* **Templates:** Responsive UI built with Bootstrap and Django Template Language.



## Database Structure

The PostgreSQL database consists of 17 tables, including:

* `p160b013_place`: Main POI data and PageRank scores.


* `p160b013_imagefeature`: High-level visual fingerprints.


* `p160b013_similarplace`: Pre-computed similarity results for fast UI response.


