# Dynamic Maze Pathfinding Engine
# 動態迷宮路徑搜尋引擎 (BFS 演算法實作)

## 📖 Overview / 專案簡介
This project implements a **Breadth-First Search (BFS)** algorithm in C++ to find the shortest path in a dynamically generated maze.  
本專案使用 C++ 實作 **廣度優先搜尋 (BFS)** 演算法，用於尋找動態迷宮中的最短路徑。

Unlike standard solutions that rely on `std::queue` or `std::vector`, this project features a **custom-built Queue data structure** (Linked-List based) and manages memory manually using **dynamic 2D arrays**. The goal is to demonstrate a deep understanding of **fundamental data structures** and **memory management** in C++.  
不同於一般依賴 `std::queue` 或 `std::vector` 的解決方案，本專案實作了**自定義的 Queue 資料結構** (基於鏈結串列)，並使用**動態二維陣列**管理記憶體。核心目標在於展示對 **C++ 基礎資料結構**與**記憶體管理**的深度掌握。

## 🚀 Key Features / 核心功能特性
* **Custom Queue Implementation (Linked-List Based)**:  
  Instead of using `std::queue`, I implemented a full-featured Queue class using a linked list structure (`Qnode`) to handle BFS operations.  
  **自製佇列 (Queue)**: 不依賴 `std::queue`，而是使用鏈結串列 (`Qnode`) 實作完整的 Queue 類別來處理 BFS 運算，展現對資料結構底層的理解。

* **Dynamic Memory Management**:  
  The maze map is stored in a dynamically allocated 2D array (`Record** map`), and all memory is rigorously freed using destructors and delete loops to prevent memory leaks.  
  **動態記憶體管理**: 迷宮地圖使用動態分配的二維陣列 (`Record** map`) 儲存，並透過解構子與迴圈嚴謹地釋放所有記憶體，防止 Memory Leak。

* **Shortest Path Backtracking**:  
  After BFS reaches the target, the program "backtracks" from the goal to the start by following the decreasing step count (gradient descent) to reconstruct the optimal path.  
  **最短路徑回溯**: 當 BFS 抵達終點後，程式會從終點開始，沿著步數遞減的方向「回溯」至起點，藉此重建出最佳路徑。

## ⚙️ Data Structures / 資料結構說明
* **`class Queue`**:  
  Manages `Qnode* front` and `Qnode* back` pointers. Implements `push`, `pop`, and a **memory-safe destructor** to clean up nodes.  
  管理前端與後端指標，實作 `push`, `pop` 以及**記憶體安全**的解構子 (Destructor)。

* **`struct Qnode`**:  
  A linked-list node structure used by the Queue, containing a `Maze` object (coordinate info) and a pointer to the next node.  
  佇列使用的鏈結串列節點結構，包含 `Maze` 物件 (座標資訊) 與指向下一個節點的指標。

* **`struct Record`**:  
  Represents a single cell in the maze grid, storing the **step count** (`num`) and **visited status** (`pass`).  
  代表迷宮格子的結構，儲存**步數** (`num`) 與**路徑標記** (`pass`)。

## 🛠️ Getting Started / 使用指南

### Prerequisites / 環境需求
* **C++ Compiler**: GCC (g++) or any standard C++ IDE.
* **OS**: Windows / Linux / macOS.

### Compilation & Execution / 編譯與執行
```bash
# Compile
g++ HW3_Maze.cpp -o maze

# Run
./maze
```

## 📥 Input Format / 輸入格式說明
The program uses a **row-by-row sparse input** method to configure the map:  
本程式採用**逐列輸入 (Row-by-Row)** 的方式來設定地圖，僅需輸入有特殊物件的位置：

1.  **First Line**: Input `Rows` and `Columns` (Map Size).  
    **第一行**: 輸入 `列數` 與 `行數` (地圖大小)。
2.  **For Each Row** (Loop from 1 to N):  
    Input the `Column Index` followed by a `Type Character`. End the input for the current row with `0`.  
    **每一列**: 輸入 `行索引` 接著輸入 `類型代號`。該列輸入結束時請輸入 `0`。

    **Type Characters (類型代號)**:
    * `s`: Start Point (起點)
    * `t`: Target / Goal (終點)
    * `x`: Obstacle / Wall (障礙物)

### Example Input / 輸入範例
*Map Size: 5x5*
*Row 1: Start point at col 1 (`1 s`), End row (`0`)*
*Row 2: Obstacle at col 3 (`3 x`), End row (`0`)*
*...and so on.*

```text
5 5
1 s 0
3 x 0
2 x 4 x 0
0
5 t 0
```

## 👨‍💻 Author / 作者
**Kai-Wei Lo (羅楷崴)**
* **M.S. in Applied Mathematics**, National Yang Ming Chiao Tung University (NYCU)  
  國立陽明交通大學 應用數學系碩士
* **Focus Areas**: Algorithm Design, C++ Implementation, Numerical Analysis, Graph Theory  
  **專攻領域**: 演算法設計、C++ 實作、數值分析、圖論
