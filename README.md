# K-means Clustering in RISC-V Assembly

## Project Overview

This project implements the **k-means clustering algorithm** in RISC-V assembly language as part of the Introduction to Computer Architecture course (IAC 2023/2024) at Instituto Superior Técnico, Universidade de Lisboa.

The program groups a set of 2D points into `k` clusters based on their proximity, visualizing the clustering process in real-time on a 32x32 LED matrix.

## Team Information

- **Group**: 39
- **Campus**: Alameda
- **Academic Year**: 2023/2024

## Description

The k-means algorithm is widely used across multiple domains including:
- Computer vision
- Machine learning
- Cybersecurity intrusion detection
- Astronomy

This implementation focuses on creating an efficient, low-level version of the algorithm that demonstrates understanding of computer architecture principles.

### Algorithm Reference
A detailed explanation of k-means clustering can be found at: [StatQuest K-means Clustering](https://statquest.org/statquest-k-means-clustering/)

## Features

### Visualization
- Real-time display of points and centroids on a 32x32 LED matrix
- Color-coded visualization with k distinct colors for each cluster
- Dynamic updates as iterations progress and clusters are refined
- Black color used for all centroids

### Algorithm Execution
- Single execution of the k-means algorithm
- Iterative refinement of clusters and centroids
- Configurable maximum iterations (L parameter)
- Updates displayed after each iteration

## Inputs

The program accepts the following main inputs (defined in `.data` section):

- **`n_points`**: The number of points
- **`points`**: A vector of points in 2D space, where each point consists of coordinates {x, y}
- **`k`**: The number of clusters to identify
- **`L`**: The maximum number of iterations for the algorithm
- **`centroids`**: Initial centroid positions

### Sample Inputs Provided

The code includes several predefined test inputs:

**Input A - Diagonal Line**
```assembly
n_points:    .word 9
points:      .word 0,0, 1,1, 2,2, 3,3, 4,4, 5,5, 6,6, 7,7, 8,8
```

**Input B - Cross**
```assembly
n_points:    .word 5
points:      .word 4,2, 5,1, 5,2, 5,3, 6,2
```

**Input C - Multiple Clusters**
```assembly
n_points:    .word 23
points:      .word 0,0, 0,1, 0,2, 1,0, 1,1, 1,2, 1,3, 2,0, 2,1, 5,3, ...
```

**Input D - Complex Distribution**
```assembly
n_points:    .word 30
points:      .word 16,1, 17,2, 18,6, 20,3, 21,1, 17,4, ...
```

## Program State

The program maintains the following state variables:

- **`clusters[n]`**: A vector indicating which cluster (0 to k-1) each point belongs to
- **`centroids[k]`**: A vector storing the coordinates of the k cluster centroids
- **`centroidsAnteriores`**: Previous centroids for convergence detection
- **`presence`**: Auxiliary data structure for cluster calculations
- **`colors`**: RGB color definitions for each cluster

## Implementation Details

### Key Procedures

1. **`printPoint`** - Paints a point (x,y) on the LED matrix with a specified color
2. **`cleanScreen`** - Clears all points from the screen
3. **`printClusters`** - Paints all clusters on the LED matrix with corresponding colors
4. **`printCentroids`** - Paints centroids in black on the LED matrix
5. **`calculateCentroids`** - Calculates k centroids based on current point distribution
6. **`manhattanDistance`** - Calculates Manhattan distance between two points
7. **`nearestCluster`** - Finds the nearest cluster for a given point
8. **`updateClusters`** - Updates cluster assignments for all points
9. **`initializeCentroids`** - Initializes centroid positions
10. **`mainSingleCluster`** - Main function for Part 1 (k=1)
11. **`mainKMeans`** - Main function executing the complete k-means algorithm

### Distance Metric

The implementation uses **Manhattan distance** to calculate proximity between points and centroids:

```
distance = |x1 - x0| + |y1 - y0|
```

### Color Scheme

- **Cluster 0**: Red (`0xff0000`)
- **Cluster 1**: Green (`0x00ff00`)
- **Cluster 2**: Blue (`0x0000ff`)
- **Centroids**: Black (`0x000000`)
- **Background**: White (`0xffffff`)

## Technical Specifications

### Memory Organization
- LED Matrix address base: `0xf0000000`
- LED Matrix dimensions: 32 x 32 pixels
- Each pixel: 4 bytes (32-bit color)
- Coordinate system: Origin at bottom-left

### Assembly Conventions
- Follows RISC-V calling conventions
- Uses stack for preserving registers
- Modular procedure-based design

## Development Stages

### Part 1 - Single Cluster (Preliminary Delivery)
- Display initial set of points on screen
- Calculate and display the centroid for all points combined
- Essentially k-means with k=1

### Part 2 - Full K-means (Final Delivery)
- Complete k-means clustering for arbitrary k values
- All required procedures implemented
- Real-time visualization of clustering process
- Convergence detection and iteration control

## Running the Program

The main execution flow:

```assembly
# For Part 1 (single cluster)
jal mainSingleCluster

# For Part 2 (k-means)
jal mainKMeans

# Program termination
li a7, 10
ecall
```

## Educational Objectives

This project emphasizes understanding of:
- Low-level programming in RISC-V assembly
- Computer architecture principles
- Algorithm efficiency at the instruction level
- Memory management and data structures in assembly
- Real-time visualization and I/O operations
- Iterative algorithm implementation
- Spatial data processing

## Credits

Algorithm visualization reference: [DataCamp](https://www.datacamp.com)

---

**Course**: Introdução à Arquitetura de Computadores  
**Institution**: Instituto Superior Técnico, Universidade de Lisboa  
**Academic Year**: 2023/2024
