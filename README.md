# Facility-Location-Optimization-Chicago-Coffee-Shops
This project demonstrates the application of Prescriptive Analytics and Mathematical Optimization to solve a real-world Facility Location Problem.

The objective is to determine the optimal locations to open 5 new coffee shops to serve customers from 30 public libraries in Chicago. By utilizing IBM CPLEX (DOcplex), the model calculates the most efficient distribution of coffee shops to minimize the total walking distance for all customers.

🛠️ Tech Stack & Tools
Language: Python

Optimization Engine: IBM CPLEX (docplex) - Community Edition

Data Processing: requests, json

Geospatial Calculation: geopy (Great-circle distance)

Visualization: folium

🧠 The Mathematical Model (MILP)
The core of this project is a Mixed-Integer Linear Programming (MILP) model. The problem was formulated with the following logic:

1. Decision Variables
coffeeshop_vars: Binary variables (0 or 1) representing whether a candidate location is selected to open a coffee shop.

link_vars: A binary matrix (30x30) representing whether a specific library is assigned to a specific coffee shop.

2. Business Constraints
Sanity Check: Forbid any routes with unrealistic or missing distance data.

Logical Assignment: A library can only be linked to a coffee shop that is actually open.

Single Source: Each library must be served by exactly one coffee shop.

Budget Limit: Exactly 5 coffee shops must be opened.

3. Objective Function
Minimize the total aggregated distance from all 30 libraries to their assigned coffee shops.

📊 Results & Business Value
The CPLEX engine successfully evaluated thousands of possible route combinations and identified the 5 absolute best locations to open the shops.

Optimal Total Distance: 65.62 miles (Accumulated across all 30 routes).

Average Walking Distance: ~2.18 miles per library.

Visualization: The output includes an interactive Folium map mapping the exact coordinates of the 5 chosen coffee shops (red markers) and the routing edges connecting them to their assigned libraries.

<img width="601" height="350" alt="image" src="https://github.com/user-attachments/assets/5831643e-f06d-4fdd-bd46-6cda69ccd37b" />

<img width="602" height="347" alt="image" src="https://github.com/user-attachments/assets/5e0e625f-5d6b-4ca2-ba3d-6385d146f4af" />


(Note: The dataset was sliced to 30 libraries to comply with the 1,000 variables/constraints limit of the IBM CPLEX Community Edition environment).

!!! How to Run Locally !!!
**Clone the repository:**
   ```bash
  git clone https://github.com/Rafanellli/Facility-Location-Optimization-Chicago-Coffee-Shops.git
   cd Facility-Location-Optimization-Chicago-Coffee-Shops
   ```

Set up a virtual environment:
   ```bash
   python -m venv venv_ibm
   venv_ibm\Scripts\activate
   ```


Install the required dependencies:
   ```bash
   python -m pip install --upgrade pip
   pip install jupyter docplex==2.25.236 cplex requests geopy folium
   ```


Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```


Open Coffeeshop_to_library_decision_optimization.ipynb and run all cells.


## 📝 Credits & Acknowledgments
This project was developed based on the Decision Optimization module provided by IBM's Data Science Professional Certificate on Coursera. Special thanks to the IBM team for the foundational framework.
Author: Seraf Adonai Rafanelli Patay
