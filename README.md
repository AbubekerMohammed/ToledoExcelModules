# TSP with AI and Parallelism

This project demonstrates solving the Traveling Salesman Problem (TSP) using Simulated Annealing and Parallelism. The project supports multiple methods including Simulated Annealing with Parallelism, Simulated Annealing without Parallelism, and Brute Force. The solution also visualizes the results using folium maps and outputs statistics such as the best path, total distance, and time taken.

## Features:
- **Simulated Annealing with Parallelism:** Optimizes TSP by parallelizing the annealing process across multiple cities.
- **Simulated Annealing without Parallelism:** Sequentially runs Simulated Annealing for each city.
- **Brute Force:** Calculates the best path by exploring all possible permutations (only for small datasets due to high computational cost).
- **Visual Output:** Generates maps displaying the calculated best route using folium.

## How to Run

1. **Running on Colab:**  
   You can easily run this project on Google Colab by simply clicking the link below:
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AbubekerMohammed/ToledoExcelModules/blob/main/TSP_with_AI_parallelism.ipynb)

2. **Requirements:**  
   If running locally, ensure you have the following packages installed:
   ```bash
   pip install numpy requests folium matplotlib imageio multiprocessing
   ```

3. **Running Locally:**
   Clone the repository:
   ```bash
   git clone https://github.com/AbubekerMohammed/ToledoExcelModules.git
   cd ToledoExcelModules
   ```

4. **Usage:**
   After setting up, you can execute the notebook or Python file. Choose your preferred method when prompted:
   - **1:** Simulated Annealing with Parallelism
   - **2:** Simulated Annealing (Loop through all cities)
   - **3:** Brute Force
   - **4:** Run all methods

## Output
- The results include the best path, total steps taken, the total distance covered, and the time taken.
- The map showing the best route will be saved as `tsp_solution_map.html`.

---

Feel free to add or modify any section as needed!
