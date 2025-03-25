# SmartTrace: Intelligent Boundary Detection Tool

A Java-based interactive tool for selecting and extracting regions from images with multiple selection methods.

## Technical Overview

This application implements different selection algorithms to create precise selections in images:

- **Point-to-Point Selection**: Simple straight-line connection between selected points
- **Intelligent Scissors**: Edge-aware selection that finds optimal paths along image boundaries
  - `CrossGradMono`: Grayscale gradient analysis for edge detection
  - `ColorWeight`: Enhanced color-based edge detection for similarly bright but differently colored regions

## Core Components

### Selection Models
- Abstract `SelectionModel` defining selection state management and interactions
- `PointToPointSelectionModel` for straight-line selections
- `ScissorsSelectionModel` for edge-following selections

### Graph-Based Path Finding
- Image pixels represented as graph vertices with weighted edges
- Dijkstra's algorithm implementation for optimal path detection
- Custom `HeapMinQueue` priority queue implementation using binary heap + hash table
- Asynchronous path computation with progress reporting

### UI Components
- `ImagePanel`: Main component for displaying images and handling selection overlay
- `SelectionComponent`: Interactive overlay for selection interactions
- `SelectorApp`: Main application class managing UI components and user interactions

## Key Implementation Details

```
|-- graph/
|   |-- Edge.java                    # Interface for directed edges in a graph
|   |-- Graph.java                   # Interface for directed graph structure
|   |-- HeapMinQueue.java            # Efficient priority queue implementation
|   |-- MinQueue.java                # Priority queue interface
|   |-- PathfindingSnapshot.java     # Captures state of pathfinding progress
|   |-- RefMinQueue.java             # Reference priority queue implementation
|   |-- ShortestPaths.java           # Dijkstra's algorithm implementation
|   |-- Vertex.java                  # Interface for graph vertices
|   |-- Weigher.java                 # Interface for edge weight functions
|-- scissors/
|   |-- ImageGraph.java              # Graph representation of image pixels
|   |-- ImagePathsSnapshot.java      # Visualization of pathfinding progress
|   |-- PolyLineBuffer.java          # Utility for building polylines
|   |-- ScissorsSelectionModel.java  # Intelligent selection implementation
|   |-- ScissorsWeights.java         # Edge weight functions for image features
|-- selector/
|   |-- ImagePanel.java              # Component for displaying the image
|   |-- PointToPointSelectionModel.java # Simple line segment selection
|   |-- PolyLine.java                # Immutable path of line segments
|   |-- SelectionComponent.java      # Overlay for selection interaction
|   |-- SelectionModel.java          # Abstract selection model
|   |-- SelectorApp.java             # Main application class
```

## Technical Features

- Concurrent processing using SwingWorker for non-blocking UI
- Property change propagation for model-view communication
- Binary heap + hash table data structure for O(log n) priority queue operations
- Visual feedback during pathfinding with frontier/settled pixel visualization
- Interactive control point manipulation for selection refinement
- Image processing using Java's BufferedImage and Raster APIs

## Requirements

- Java 17 or higher
- Swing-compatible environment

## Implementation Notes

- The intelligent scissors implementation is based on graph algorithms with image gradient analysis
- Edge weights are calculated using perpendicular gradient analysis at pixel boundaries
- Binary heap with hash table indexing enables efficient priority updates for Dijkstra's algorithm
- Background thread processing with progress reporting for responsive UI
- Custom polygon extraction with alpha channel for saving selections
