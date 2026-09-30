# Fractol

A small interactive fractal renderer written in C using **MiniLibX**. This project explores complex numbers, fractal mathematics, coordinate mapping, graphical rendering, and event handling.

## Features

* Render the **Mandelbrot** set.
* Render customizable **Julia** sets.
* Zoom in and out with the mouse wheel.
* Move around the fractal with the arrow keys.
* Increase or decrease the maximum number of iterations.
* 600×600 graphical window.
* Command-line argument validation and error handling.
* Real-time re-rendering when the view or iteration count changes.

## Requirements

* Linux
* `cc` / GCC-compatible C compiler
* `make`
* X11 development libraries
* MiniLibX for Linux

The project uses MiniLibX with X11 and Xext.

## Installation

Clone the repository:

```bash
git clone https://github.com/xyzgoeswild/fractol.git
cd fractol
```

Build the project:

```bash
make
```

This creates the `fractol` executable.

## Usage

### Mandelbrot

Run the Mandelbrot set:

```bash
./fractol mandelbrot
```

### Julia

Run a Julia set by providing the real and imaginary components:

```bash
./fractol julia <real> <imaginary>
```

Example:

```bash
./fractol julia -0.7 0.27015
```

The program validates the fractal name and Julia coordinates before starting.

## Controls

| Input            | Action                  |
| ---------------- | ----------------------- |
| Mouse wheel up   | Zoom in                 |
| Mouse wheel down | Zoom out                |
| Arrow keys       | Move around the fractal |
| `+`              | Increase iterations     |
| `-`              | Decrease iterations     |
| `ESC`            | Close the window        |

The default maximum iteration count is **50**.

It can be increased up to **1000** or decreased down to **10**.

## How It Works

The renderer maps each screen pixel to a point in the complex plane and repeatedly applies the fractal equation:

```text
z = z² + c
```

### Mandelbrot

For the Mandelbrot set, `c` is taken from the pixel's position in the complex plane.

### Julia

For the Julia set, `c` is fixed using the coordinates supplied through the command line, while the initial `z` comes from the pixel position.

A point is considered to have escaped when the squared magnitude of `z` exceeds the configured escape value.

The number of iterations is then used to determine the pixel's color.

## Project Structure

```text
fractol/
├── includes/
│   └── fractol.h
├── src/
│   ├── main.c
│   ├── display_error.c
│   ├── events.c
│   ├── initialize.c
│   ├── math_utils.c
│   ├── parsing.c
│   ├── render.c
│   └── utils.c
└── Makefile
```

### Main Components

* **main.c** — Parses command-line arguments and starts the selected fractal.
* **parsing.c** — Validates fractal names and Julia parameters.
* **initialize.c** — Initializes MiniLibX, the window, image buffer, and default fractal data.
* **render.c** — Performs the fractal iterations and draws pixels to the image.
* **math_utils.c** — Handles complex-number operations, coordinate mapping, and number parsing.
* **events.c** — Handles keyboard, mouse, and window events.
* **display_error.c** — Handles invalid input and error messages.
* **utils.c** — Contains supporting utility functions.
* **fractol.h** — Contains structures, constants, includes, and function declarations.

## Makefile Commands

### Build

```bash
make
```

Builds the `fractol` executable.

### Clean

```bash
make clean
```

Removes object files.

### Full Clean

```bash
make fclean
```

Removes object files and the `fractol` executable.

### Rebuild

```bash
make re
```

Cleans the project and rebuilds everything.

## Concepts Practiced

This project was developed as part of the **42 curriculum** and focuses on:

* Complex numbers
* Fractal mathematics
* Coordinate transformations
* Iterative algorithms
* Pixel manipulation
* Graphics programming with MiniLibX
* Keyboard and mouse event handling
* Command-line parsing
* Memory management
* C programming

## Author

**XYZ**

42 Network / 1337
