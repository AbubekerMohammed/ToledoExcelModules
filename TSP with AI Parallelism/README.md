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

## Visualization & Route Planning
To help students understand the complexity of the Traveling Salesman Problem (TSP), they were provided with a city map and asked to calculate the total cost of traveling through different routes. This allowed them to see how the order of cities affects the total cost.
<img src="./City Map(1).png" alt="City Map.png" width="400"/>

## 📊 Route Cost Table
| Route  | Total Cost of Travelling |
|--------|---------------------------|
| ABCDA  | 3 (A→B) + 1 (B→C) + 5 (C→D) + 6 (D→A) = 15 |
| ABDCA  | 3 (A→B) + 4 (B→D) + 5 (D→C) + 2 (C→A) = 14 |
| ACDBA  | 2 (A→C) + 5 (C→D) + 4 (D→B) + 3 (B→A) = 14 |
| ACBDA  | 2 (A→C) + 1 (C→B) + 4 (B→D) + 6 (D→A) = 13 |
| ADCBA  | 6 (A→D) + 5 (D→C) + 1 (C→B) + 3 (B→A) = 15 |
| ADBCA  | 6 (A→D) + 4 (D→B) + 1 (B→C) + 2 (C→A) = 13 |


## ⚙️ Time vs. Number of Cores
| Number of Cores | Time Taken (s) |
|------------------|----------------|
| 1                | Time1          |
| 2                | Time2          |
| 4                | Time3          |
| 16               | Time4          |
| 32               | Time5          |


## ⚡ GPU Thread Performance
| Thread Count | Time Taken (s) |
|--------------|----------------|
| 1            | Time1          |
| 2            | Time2          |
| 12           | Time3          |
| 32           | Time4          |
| 64           | Time5          |
| 128          | Time6          |

---

Feel free to add or modify any section as needed!
