# Python Capstone Proposal — Track A (Research)

## Project title
**Dynamic-Obstacle Multi-Target Path Planning for Autonomous Mobile Robots**

## 1. Benchmark paper
Xiang, D., Lin, H., Ouyang, J., & Huang, D. (2022). “Combined improved A* and greedy algorithm for path planning of multi-objective mobile robot.” *Scientific Reports*, 12, Article 13273. https://doi.org/10.1038/s41598-022-17684-0

**Venue:** *Scientific Reports* was Q1 in the 2022 SCImago Journal Rankings (SJR = 0.973; Multidisciplinary category).

SCImago ranking: https://www.scimagojr.com/journalrank.php?ord=desc&order=tc&type=j&year=2022

**Code/data:** I could not identify a public official code repository or downloadable dataset. The paper states that its data are available from the corresponding author upon reasonable request. I will recreate the published grid scenario in Python.

## 2. Result to reproduce
I will recreate the multi-target warehouse scenario in **Figure 5** and compare my results with **Table 6**. The start is (1,1), the final goal is (47,47), and the four intermediate targets are (13,13), (21,24), (30,27), and (37,40).

The main metrics are average path length and total turning angle. Planning time will be a secondary metric. Table 6 reports **79.015** average path length, **1311.276°** total turning angle, and **1.686** average planning time for the proposed method. The paper's Reference 38 comparison values will be cited as reported; my own baseline will be plain A* with nearest-first target ordering. If I report node count, I will define it as the total number of expanded nodes summed across all path segments.

## 3. Research question
**Compared with the static result reproduced for Table 6, how do 3, 6, and 10 randomly moving obstacles change average path length, total turning angle, and task-completion rate when the robot replans its route to the remaining targets?**

## 4. Data and compute
I will recreate the Figure 5 grid, obstacle layout, start, goal, and target coordinates from the paper using Python, NumPy, and Matplotlib. Each dynamic obstacle will move one cell per step using a random walk through free cells. The robot also moves one cell per step. A collision occurs if the robot and an obstacle occupy the same cell or swap cells during a step. Replanning is triggered when an obstacle blocks the robot's next planned cell. If no safe route is found within 500 steps, that run will count as a failure. Task completion means reaching all four targets and the final goal without collision. I will use 30 fixed random seeds for each obstacle count and compare the improved method with plain A* using nearest-first target ordering under the same obstacle movements. The experiments are intended to run on Google Colab; no physical robot is required.

## 5. Plan and fallback
**By 4 December 2026:** Recreate the Figure 5 scenario; implement the paper's improved A*–greedy method and the plain A* nearest-first baseline; and compare the static results with Table 6.

**By 18 December 2026:** Add 3, 6, and 10 moving obstacles; test both methods using the same 30 random seeds; report path length, turning angle, task-completion rate, and replanning time; and complete the code and 4–6 page IEEE-style report.

**Fallback:** If the multi-target Figure 5 reproduction is not completed, I will reproduce the single-target Map 1 (20 × 20) experiment shown in Figure 3 and Table 3, using start (1,1) and goal (17,17), and compare traditional A* with improved A* on path length and turning angle.

## Implementation note
The paper does not clearly specify all parameter choices, including the α and β weights, and some path-smoothing equations may require interpretation. I will document any assumptions and report deviations rather than claim an exact reproduction if the published details are insufficient. If the full Figure 5 implementation is not working by 27 November, I will switch to the fallback scenario to protect the 4 December checkpoint.

## AI-use disclosure
ChatGPT and Claude helped with brainstorming, reading and understanding the benchmark paper, and editing this proposal. I will write and verify the implementation, run the experiments, and take responsibility for the results and analysis.
