# Computer simulations of mechanical properties of penta-graphene nanotubes

Code from my MSc thesis in Materials Science (Nanotechnology) at Gdańsk University of
Technology (2018–2020).

Penta-graphene is a 2D carbon material made only of pentagons. In the thesis I rolled
penta-graphene sheets into nanotubes (PGNTs), simulated them with molecular dynamics in
LAMMPS, and measured how their radius and length change with temperature and with axial
tension and compression.

## What the code does

The C++ programs cover the whole simulation workflow: they generate the structures,
then batch-process the LAMMPS output.

| File | What it does |
|---|---|
| `Penta-Graphene Nanotube Generation in C++` | Builds a nanotube from the 6-atom penta-graphene unit cell. It tiles a flat sheet, cuts it along the chiral vector (m, n), rotates the cut onto the x-axis, replicates it, and rolls it into a tube. Each stage writes an `.xyz` structure file |
| `Analysis of PGNT's after relaxation in C++` | Reads the final configurations of 20 nanotubes, after relaxation and after 81 deformation steps each, and computes the tube radius |
| `PGNT Radius and Length Analysis in C++` | Parses NPT and NVT trajectory dumps (`.lammpstrj`) at 8 temperatures and up to 26 strain steps. Averages the radius and length frame by frame, then over all frames, and writes one summary table per run |
| `Merging Excel Files in Python` | A small, separate pandas utility: it combines the `Raw Data` sheet of every `.xlsm` file in a folder into one workbook |

## Notes

- The C++ files are **listings copied from the thesis appendix**. They keep the printed line
  numbers and page numbers, so they don't compile as they are.
- They need the LAMMPS output files, which are not in this repository.
- From a data point of view, the analysis is a batch ETL job. It parses more than 1,900
  fixed-layout simulation files, aggregates per frame and per run, and produces tidy summary
  tables for plotting.

## Tools

C++, LAMMPS (molecular dynamics), Python (pandas).
