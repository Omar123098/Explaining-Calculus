# But what is dy/dx?

**Calculus for machine learning, built from one idea: nudge the input a tiny bit, see how much the output moves, and divide.**

This repo has the interactive notebook from the YouTube video *But what is dy/dx?*. It starts with the slope of a straight line and ends with backpropagation in a small neural network, and every step comes with a plot you can play with.

▶️ **Watch the video:** [[VIDEO LINK]](https://www.youtube.com/watch?v=C_-AxTT9lzQ&t=9s)

---

## What's inside

`but_what_is_dydx.ipynb` follows the video, one section per idea:

| # | Topic | What you can do |
|---|---|---|
| 1 | Slope of a straight line | Drag two points and watch Δf / Δx stay the same |
| 2 | f(x) = x² and limits | Shrink Δx and watch the slope settle on 2x |
| 3 | Velocity | A car on a road: average speed becomes the speedometer as Δt → 0 |
| 4 | f(x) = 1/x | Same method, new function: the slope is −1/x² |
| 5 | Chain rule (one variable) | Wind power → turbine output: (Δg/Δu)·(Δu/Δt) |
| 6 | Functions of two variables | A rotatable 3D surface of f(x, y) = x²y³ |
| 7 | Partial derivatives | Freeze one variable, slice the surface, nudge the other |
| 8 | Total derivative | The tangent plane and df = fₓ dx + f_y dy |
| 9 | Linear regression + gradient descent | Fit a line to 25 points step by step, change the learning rate, watch it overshoot |
| 10 | Multivariable chain rule | Walk a circle on the surface: dz/dt = fₓ·dx/dt + f_y·dy/dt |
| 11 | Backpropagation | Train a 2-neuron network to learn "comfortable temperature", and check every gradient against the nudge method |

Every derivative in the notebook is checked twice: once with the formula and once numerically, by taking a tiny step and dividing.

---

## Run it

You need **Python 3.9+**.

**1. Install the packages**

```bash
pip install numpy matplotlib PyQt6 notebook
```

**Ubuntu / Debian only:** Qt also needs one system library. Without it, the kernel crashes when the first plot window opens.

```bash
sudo apt install libxcb-cursor0
```

**2. Open the notebook**

- **VS Code:** open `but_what_is_dydx.ipynb` with the Jupyter extension installed and pick your Python kernel.
- **Browser:** run `jupyter notebook` in this folder and open the file.

**3. Run the Setup cell first.** It should print:

```
Ready. Plots open in windows using: qtagg
```

Then run the sections in order.

---

## How the plots work

Every plot opens in **its own window**, with its sliders and buttons at the bottom of that window. No browser or WebGL is needed.

- **Sliders:** drag them, or click anywhere on a slider to jump to that value.
- **▶ shrink Δx:** slides Δx from 1 down to 0.000001 over a few seconds.
- **▶ play / next step:** steps through gradient descent or network training.
- **3D plots:** drag with the left mouse button to rotate, right-drag to zoom, or press **spin**.

Two options at the top of the Setup cell:

| Option | Default | What it does |
|---|---|---|
| `CLOSE_OTHERS` | `True` | Opening a new plot closes the previous window, so one plot is on screen at a time |
| `MAXIMIZE` | `True` | Opens windows maximized (handy for screen recording) |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| "The kernel crashed" or "Could not load the Qt platform plugin xcb" | `sudo apt install libxcb-cursor0`, restart the kernel, run Setup again |
| Setup prints `tkagg` instead of `qtagg` | PyQt6 is installed in a different Python environment. Run `%pip install PyQt6` inside the notebook, then restart the kernel |
| `NameError` (for example `F`, `wind` or `history`) | Run the cells above it. Later sections reuse functions from earlier ones |
| Windows pile up on screen | Keep `CLOSE_OTHERS = True`, or run the last cell (`plt.close("all")`) |

---

## Go deeper

- [3Blue1Brown, Essence of Calculus](https://www.youtube.com/watch?v=WUvTyaaNkzM&list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr): the geometric intuition behind every idea here
- [3Blue1Brown, Neural Networks](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi): what a network is and how backpropagation works, visually
- [Andrej Karpathy, Neural Networks: Zero to Hero](https://www.youtube.com/watch?v=VMj-3S1tku0&list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ): build backpropagation from scratch in Python (micrograd)

---

Made by **Omar Elgedawy**. Found a mistake or have an idea? Open an issue.
