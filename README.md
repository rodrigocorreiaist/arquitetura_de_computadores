K-means Clustering in RISC-V Assembly
Project Overview
This project implements the k-means clustering algorithm in RISC-V assembly language as part of the Introduction to Computer Architecture course (2023/2024). The program groups a set of 2D points into k clusters based on their proximity, visualizing the clustering process in real-time.

Description
The k-means algorithm is widely used across multiple domains including:

Computer vision
Machine learning
Cybersecurity intrusion detection
Astronomy
This implementation focuses on creating an efficient, low-level version of the algorithm that demonstrates understanding of computer architecture principles.

Algorithm Reference
A detailed explanation of k-means clustering can be found at: StatQuest K-means Clustering

Inputs
The program accepts the following main inputs:

points: A vector of points in 2D space, where each point consists of coordinates {x, y}
n: The number of points (size of the points vector)
k: The number of clusters to identify
l: The maximum number of iterations for the algorithm
Program State
The program maintains the following state variables:

clusters[n]: A vector indicating which cluster (0 to k-1) each point belongs to
centroids[k]: A vector storing the coordinates of the k cluster centroids (each with 2D coordinates)
Additional state variables as needed
Features
Visualization
Real-time display of points and centroids on a 2D matrix display
Color-coded visualization with k distinct colors for each cluster
Dynamic updates as iterations progress and clusters are refined
Algorithm Execution
Single execution of the k-means algorithm (not optimized with multiple runs)
Iterative refinement of clusters and centroids
Updates displayed after each iteration
Project Structure
The solution is organized into modular procedures/functions, each solving a specific sub-problem. This modular approach allows for:

Incremental development and testing
Clear separation of concerns
Easier debugging and maintenance
Development Approach
It is recommended to implement and test each procedure individually before moving to the next, ensuring gradual progress toward the complete solution.

Deliverables
Preliminary Delivery
The preliminary submission should demonstrate:

Display of the initial set of points on screen
Calculation and display of the centroid for all points combined
Essentially, k-means with k=1
Final Delivery
The complete implementation with:

Full k-means clustering for arbitrary k values
All required procedures implemented
Real-time visualization of clustering process
Adherence to the provided code skeleton structure
Implementation Requirements
Code Organization
Must follow the procedure structure defined in the project skeleton
Must respect the memory organization defined in the initial code
Each procedure must be implemented and tested independently
Technical Constraints
Written entirely in RISC-V assembly language
Efficient implementation required for practical applications
Must handle 2D point coordinates and calculations
Solution Architecture
The solution is decomposed into procedures that should be implemented in the suggested order (detailed in the full project specification). The provided code skeleton defines:

Code structure conventions
Memory data organization
Interface requirements between procedures
Team Composition
This project is designed for groups of 3 students, allowing for division of work across the different procedures while maintaining collaborative integration.

Credits
Algorithm visualization reference: DataCamp

Note: This project emphasizes understanding of:

Low-level programming in assembly
Computer architecture principles
Algorithm efficiency at the instruction level
Memory management and data structures in assembly
Real-time visualization and I/O operations
