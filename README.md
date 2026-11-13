# Windmill
A simple Computer Graphics and Image Processing (CST 304) macro-project of drawing a windmill.

# 2D Rotating Windmill Animation with Matplotlib and NumPy

This project implements a 2D rotating windmill animation in Python using `matplotlib` and `numpy`. It serves as a visual demonstration of basic linear algebra concepts, specifically **rotation matrices** and **composite 2D transformations**.

## Table of Contents
- [How It Works](#how-it-works)
  - [1. Geometry Representation](#1-geometry-representation)
  - [2. Rotation Matrix](#2-rotation-matrix)
  - [3. Composite Transformation](#3-composite-transformation)
- [Requirements](#requirements)
- [How to Run](#how-to-run)

---

## How It Works

### 1. Geometry Representation
Each blade of the windmill is defined as a simple 2D triangle centered around the origin `(0, 0)`. The vertices are represented as a $2 \times 3$ NumPy matrix:
$$
\text{blade\_coords} = \begin{pmatrix} 0 & 0.8 & -0.8 \\ 0 & 4.0 & 4.0 \end{pmatrix}
$$
where row 1 corresponds to the $X$ coordinates, and row 2 corresponds to the $Y$ coordinates.

### 2. Rotation Matrix
To rotate the blade by an angle $\theta$ (converted to radians), we multiply the coordinate matrix by the standard 2D rotation matrix $R$:
$$
R = \begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}
$$

In the code, this is calculated using NumPy's matrix multiplication operator `@`:
```python
rotated_points = R @ points
```

### 3. Composite Transformation
To animate four independent blades rotating around the tower's hub, the script applies a composite transformation sequence for each frame:
1. **Rotation**: Rotate the base blade by the current angle plus a $90^\circ$ offset relative to the other blades.
2. **Translation**: Translate the rotated coordinates from the origin `(0,0)` to the windmill hub center at `(cx, cy)` (coordinates `(0, 6)`).

Finally, `matplotlib.animation.FuncAnimation` continuously updates the polygons to construct a smooth rendering.

## Requirements
- Python 3
- NumPy
- Matplotlib

## How to Run
Execute the code cell in your Jupyter/Google Colab environment. Matplotlib will render the real-time looping animation directly in your browser.
