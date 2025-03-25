# SmartTrace: Intelligent Boundary Detection Tool

## 🧠 Overview

SmartTrace is a Java-based desktop application designed to intelligently detect object boundaries in images. Powered by Dijkstra’s algorithm and built with Swing, it allows users to select boundaries either manually or with intelligent auto-tracing. The application is optimized for performance using multithreading and `SwingWorker`, ensuring a responsive and smooth user experience.

## 🚀 Features

- 🔍 **Intelligent Auto-Tracing**: Uses Dijkstra’s algorithm to detect optimal paths along object edges.
- ✏️ **Manual Selection Mode**: Users can manually outline boundaries for finer control.
- ⚡ **Multithreaded UI**: Real-time responsiveness using Java's `SwingWorker` for background computation.
- 💾 **Interactive Visualization**: View and modify paths live on the image canvas.
- ⏱️ **Performance Boost**: Reduces boundary selection time by up to 65% compared to manual methods.

## 🛠️ Technologies Used

- Java
- Swing GUI Framework
- Dijkstra’s Algorithm
- Graph Data Structures
- Java Multithreading (`SwingWorker`)

## 📷 How It Works

1. **Load an Image** into the app.
2. **Click to Select Points** on the boundary.
3. **Auto-trace Path** between points using graph-based shortest paths.
4. **Preview & Save** the selected boundary.

## 📂 File Structure

