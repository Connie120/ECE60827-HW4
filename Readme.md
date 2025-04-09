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
- Interpreting Timeloop’s output reports and visualizations
- Exploring trade-offs in compute and memory usage

This practical experience is intended to deepen your understanding of accelerator simulation and help you think critically about efficient DNN hardware design.
