![header](imgs/1ndd_conservation_cropped.png)
# SSDraw

## Installation

SSDraw requires the Biopython module to be installed.

```bash
pip install biopython
```

SSDraw also requires DSSP to be installed:

```bash
sudo apt-get install dssp
```

Alternatively, you can install DSSP either through conda (conda install -c salilab dssp), or you can follow the instructions on their github page to make a local installation: 
https://github.com/cmbi/dssp.

## Instructions
SSDraw requires 4 arguments:
1. --fasta: the file name sequence or alignment file in fasta format.
2. --name: the id of the sequence in the fasta file corresponding to your protein of interest.
3. --pdb: the file name of the pdb file of your protein
4. --output: the output file name to use


Example 1:
```
python3 ../SSDraw.py --fasta 1ndd.fasta --name 1ndd --pdb 1ndd.pdb --output 1ndd_out
```
![Example 1](imgs/1ndd_out.png)

### Coloring options:
SSDraw uses a gradient to color each position in the alignment by a certain score. The user can choose which scoring system to use, and they can also choose which colormap.

### Scoring: 
-conservation_score: score each position in the alignment by conservation score.
-bfactor: score each residue in the pdb by bfactor
-scoring_file: score each residue by a custom scoring file prepared by the user
-mview: color each residue by the mview coloring system

Example 2: Score by conservation
```
python3 ../SSDraw.py --fasta aligned.fasta --name 1ndd --pdb 1ndd.pdb --output 1ndd_conservation -conservation_score
```
![Example 2](imgs/1ndd_conservation.png)
Example 3: Score by bfactor
```
python3 ../SSDraw.py --fasta 1ndd.fasta --name 1ndd --pdb 1ndd.pdb --output 1ndd_bfactor -bfactor
```
![Example 3](imgs/1ndd_bfactor.png)
### Choosing a colormap:
The default colormap for SSDraw is inferno. The user can select one of the matplotlib library color maps or simply list a set of colors they'd like to use with the --color_map option. Alternatively, the user can select a single color with the --color option and SSDraw will use that color on the whole image.

Example 4: Custom scoring file with custom color map
```
python3 ../SSDraw.py --fasta 2kdl.fasta --name 2kdl --pdb 2kdl.pdb --output 2kdl_out --scoring_file 2kdl_scoring.txt --color_map black cyan  
```
![Example 4](imgs/2kdl_out.png)
### DSSP files:
Normally, SSDraw will generate a DSSP annotation from the PDB file, but if you have a DSSP file you would like to use, you can upload it and input the file name in Options.

### --start and --end:
If you want SSDraw to draw only a portion of your alignment, you can specify the start and/or end points using the --start and --end options respectively. The argument for these options correspond to the index of the alignment position, not to the residue position numbers.

Example 5: Choose subregion of alignment to run SSDraw on
```
python3 ../SSDraw.py --fasta aligned.fasta --name 1ndd --pdb 1ndd.pdb --output 1ndd_conservation_cropped -conservation_score --start 75 --end 132
```
![Example 5](imgs/1ndd_conservation_cropped.png)