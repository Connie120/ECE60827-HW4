# ECE 60827 Hardware Simulation Part 4 

## Professor T. N. Vijaykumar <br> TA: Ni Kang

## Due on Sunday, May 04 2025 at 11:59 PM ET

# Introduction to Timeloop

[Timeloop](https://github.com/NVlabs/timeloop) is an open-source, highly customizable performance modeling framework for deep neural network (DNN) accelerators. Developed by NVIDIA Research, it enables researchers and engineers to simulate and evaluate the behavior of different accelerator architectures and dataflows in detail.

Timeloop works by simulating how a DNN computation is mapped onto a hardware accelerator — including the movement of data across memory hierarchies, the scheduling of operations, and the use of hardware resources such as processing elements and buffers. It is particularly useful for exploring the design space of DNN accelerators and optimizing their performance and energy efficiency.

# About This Lab

In this lab, you will go through **six structured exercises** designed to help you **understand and explore the fundamentals of simulation using Timeloop**. These exercises cover various aspects of workload mapping, hardware configuration, memory hierarchy design, and performance analysis. By the end of the lab, you will gain hands-on experience with:

- Writing workload and architecture configuration files
- Understanding how dataflows impact performance
- Interpreting Timeloop’s output reports
- Exploring design trade-offs

This practical experience is intended to deepen your understanding of accelerator simulation and help you think critically about efficient DNN hardware design.

## Lab Environment Setup

This lab uses [Timeloop](https://github.com/NVlabs/timeloop) and [Accelergy](https://github.com/Accelergy-Project/accelergy) for performance and energy simulation of DNN accelerators. These tools are packaged inside a container to ensure consistent environments across machines.

### Why Apptainer?

While Docker is commonly used to run containers and provides a stable environment, Docker requires root (`sudo`) privileges, which are not available on shared servers. To overcome this, we use Apptainer (formerly Singularity), which is designed for running containers in multi-user environments like HPC clusters without needing `sudo`.

We will run this lab on the **Scholar server** (gpu.scholar.rcac.purdue.edu).


This is the same server used for previous CUDA programming assignments.

### Step 1: Build the Container Image

First, build the Apptainer container using the provided Docker image:

```bash
apptainer build timeloop.sif docker://timeloopaccelergy/accelergy-timeloop-infrastructure:latest
```

This will create a local file called timeloop.sif, which is the container image you will use.


### Step 2: Start the Apptainer Interactive Shell

Use the following command to launch an interactive shell session inside the container:

```bash
apptainer shell \
  --bind ./workspace/:/home/workspace/ \
  --env LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH \
  --bind $(pwd)/timeloop_tmp/cacti_tmp:/usr/local/share/accelergy/estimation_plug_ins/accelergy-cacti-plug-in/cacti_inputs_outputs \
  --bind $(pwd)/timeloop_tmp/neurosim_tmp:/usr/local/share/accelergy/estimation_plug_ins/accelergy-neurosim-plugin \
  timeloop.sif
```

Here’s what each `--bind` flag does:

- `./workspace/` → `/home/workspace/`:  
  Mounts your local `workspace/` folder (containing lab exercises) into the container so you can edit and run files inside the container environment.

- `$(pwd)/timeloop_tmp/cacti_tmp` → `/usr/local/share/accelergy/estimation_plug_ins/accelergy-cacti-plug-in/cacti_inputs_outputs`:  
  Provides a writable location for the CACTI plugin, which generates intermediate files during energy estimation.

- `$(pwd)/timeloop_tmp/neurosim_tmp` → `/usr/local/share/accelergy/estimation_plug_ins/accelergy-neurosim-plugin`:  
  Provides a writable location for the NeuroSim plugin, required for analog/mixed-signal energy estimation.

These bindings are necessary because Apptainer containers are **read-only by default**. Mounting writable host directories allows the simulation tools to generate and store intermediate data and logs.


Once inside the container shell, navigate to the mounted workspace to begin working:

```bash
cd /home/workspace/
```

This is where all the lab exercises are located. You can edit files, run Timeloop simulations, and explore results from this directory inside the container.


## Lab Exercises

In this lab, you will walk through **six hands-on exercises** designed to help you understand and explore accelerator simulation using Timeloop. Each exercise is located in its own directory within the `workspace/` folder and includes a clear objective and specific task.

Please read the instructions provided in each exercise folder or its `README.md`, and complete the required steps. Some exercises may ask you to modify architecture files, experiment with mappings, or analyze simulation outputs such as performance or energy breakdowns.


## What to Submit

You are required to submit a **maximum 3-page report** (PDF format) that includes the following:

- Answers to specific questions posed in each exercise, including plots or tables summarizing the resultsi (where applicable).
- Analysis and discussion of trends or trade-offs observed

Keep your report concise and focused. Use visualizations and bullet points where appropriate.

