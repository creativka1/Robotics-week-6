# Lab 6 — Differential Drive Robot Localization

Assigned trajectory: **24**.

This lab compares recorded simulator and physical-robot odometry using TRIK Studio. The notebook retains the supplied motor-model example, followed by the trajectory comparison, difference-over-time plot, and calculated results. Its code has no comments or Markdown cells, as requested, and all plot outputs are saved.

## Files

| File | Contents |
|---|---|
| `trajectory_real.qrs` | Physical-robot program with native diagram blocks |
| `trajectory_sim.qrs` | Corresponding simulator program with native diagram blocks |
| `odometry_data_real.txt` | Recorded physical-run odometry |
| `odometry_data_sim.txt` | Recorded native-diagram simulator odometry |
| `Lab6_analysis_24.ipynb` | Executed notebook with plots and results |
| `requirements.txt` | Python dependencies |

Both log files are headerless CSV with columns `x,y,time`: position in metres and time in milliseconds. Positions are encoder-based estimates. The raw logs are unchanged.

## Run the notebook

Keep the two `.txt` files beside the notebook. Install the requirements and open the notebook in Jupyter, or upload it to Google Colab. In Colab, run all cells and select both `.txt` files when prompted.

```bash
pip install -r requirements.txt
```

## Run the robot program

Open the appropriate `.qrs` in TRIK Studio and select the robot-behavior diagram tab. The projects contain editable native blocks rather than an embedded script. Select the physical robot or 2D model as appropriate, then generate/upload or run normally.

Start at the lower-right of 2, facing left. The programs request 30 cm stroke units, nominal digit height 60 cm, and a top connecting travel segment between the digits. Physical settings are radius 0.042 m and wheelbase 0.194 m; simulator settings are radius 0.028 m and wheelbase 0.154 m. Left motor/encoder: M4/E4; right: M3/E3.

Wait for `24 OK 19/19`. Retrieve and preserve each new run's log before running again. The program also writes an optional encoder diagnostic file; only the two odometry logs needed for the comparison are included here.

## Recorded comparison

| Quantity | Simulator | Physical robot |
|---|---:|---:|
| Samples | 5,688 | 2,422 |
| Recorded interval | 113.720 s | 128.760 s |
| Final x | 0.613390 m | 0.595448 m |
| Final y | 0.009612 m | 0.006276 m |

The completed-run odometry endpoint separation is **0.018250 m (1.825 cm)**. Time-aligned differences also include the different execution speeds and settling durations; the notebook compares only the common recorded interval. This is an odometry comparison, not an independent measurement of the actual floor trajectory. The tape-measurement item is omitted following the instructor clarification supplied for this task.
