# How to make Singularity images for Turku-neural-parser-pipeline

Docker images for [Turku-neural-parser-pipeline](http://turkunlp.org/Turku-neural-parser-pipeline/) are very helpfully provided by the Turku NLP group.  This repository contains recipies for converting these into Singularity images suitable for CSC's Puhti HPC cluster.

Building the images requires root access, so it has to be done on a computer where you have root or sudo access, such as your own computer or a virtual server in Pouta.  To build the CPU version, simply run:

    sudo singularity build tnpp-cpu.sif tnpp-cpu.def

For the GPU version, run:

    sudo singularity build tnpp-gpu.sif tnpp-gpu.def

For convenience pre-build images can also be found in Allas: [tnpp-cpu.sif](https://a3s.fi/mldata/tnpp-cpu.sif), [tnpp-gpu.sif](https://a3s.fi/mldata/tnpp-gpu.sif), and in the `/appl/soft/ai/singularity/images/` directory on Puhti.

Finally, you can run it like this for the CPU version:

    echo "Minulla on koira." | singularity run --pwd=/app tnpp-cpu.sif stream fi_tdt parse_plaintext > parsed.conllu

or for the GPU version:

    echo "Minulla on koira." | singularity run --nv --pwd=/app tnpp-gpu.sif stream fi_tdt parse_plaintext > parsed.conllu

In Puhti use the full path to the sif file, e.g. `/appl/soft/ai/singularity/images/tnpp-cpu.sif`.
