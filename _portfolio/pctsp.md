---
title: "Prize-collecting Travelling Salesperson Problem"
excerpt: "Implementation in Python and C++ of algorithms for the Prize-collecting TSP."
collection: portfolio
---

This project develops heuristics and a branch-and-cut algorithm for the Prize-collecting TSP on sparse graphs with non-metric cost function.
The motivation of this problem is to plan a route in a city that minimises the air pollution exposure of a runner.
The route must be sufficiently long and start/end at the same location.

For details, you can [read the paper](https://ceur-ws.org/Vol-3813/9.pdf),
[see the open-source code](https://github.com/PatrickOHara/pctsp) and [install the software](https://github.com/PatrickOHara/pctsp/blob/master/docs/installation.md).
The [TSPLIB dataset](http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/) is publicly available.
Please reach out directly for access to the air quality dataset.

# Usage

We recommend using our software via the command line interface (CLI).
This allows the user to run individual algorithms on single instances, run large number of instances in one go,
or to 'batch' instances with many different parameters with support for creating slurm scripts.

For example, to run Suurballe's heuristic on the st70 instance from the TSPLIB dataset:

```bash
pctsp tsplib suurballes_heuristic --graph-name st70
```

Equally, one can run the full branch & cut algorithm on the King's Cross (kx) instance of the londonaq dataset:

```bash
pctsp londonaq solve_pctsp --graph-name laqkxA
```

Note one can use the `--help` option at any point to get support for the commands.

## Docker

For ease of use, why not use our pre-built docker image with the TSPLIB dataset included to run some algorithms?
First you will need to pull the latest docker image:

```bash
docker pull patrickohara/pctsp:latest
```

For example, to run Suurballe's heuristic on the TSPLIB st70 instance:

```bash
docker run patrickohara/pctsp:latest pctsp tsplib suurballes_heuristic --graph-name st70
```

## Batching & Slurm

To make pushing hundreds or thousands of instances to Slurm managed clusters easier,
we have commands for creating batches of instances and writing a slurm file to a filepath of your choosing.

The first step is to setup the experiment.
The following command will read the dataset files from the root directory specified
then create a json file with all the experiment settings.

```bash
pctsp setup londonaq cost_cover --londonaq-root ~/datasets/londonaq
```

Next, we will create a slurm file for the experiment with a given batch size.
The batch size is the number of instances that will be ran on one slurm task.
In the example below, the batch size is 3:

```bash
pctsp slurm cost_cover 3 --londonaq-root ~/datasets/londonaq/
```

The logger will output the location of the slurm file created (it will be called `cost_cover.slurm`).
To submit the jobs to slurm, simply run:

```bash
sbatch cost_cover.slurm
```
