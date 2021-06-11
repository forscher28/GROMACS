# GROMACS
This contains all the input and output files used in  tutorial 1 i.e. Lysozyme in Water

# Step One: Preparation of Topology
1. Download the protein structure from https://www.rcsb.org/ <br/>
2. One the protein is downloaded you can use VMD or PyMOL to view the structure<br/>
3. Remove all the water molecues from the protein structure and verify the presence of all the atoms the PDB file should contain only protein atoms, and is ready to be input into the first GROMACS module, pdb2gmx.<br/>
4. The topology (topol.top) file contains all the information necessary to define the molecule within a simulation. This information includes nonbonded parameters (atom types and charges) as well as bonded parameters (bonds, angles, and dihedrals). We will take a more detailed look at the topology once it has been generated.<br/>
5. gmx pdb2gmx -f 1AKI.pdb -o 1AKI_processed.gro -water spce
6. Select the OPLS Force filed which is the most applicable to this simulation<br/>
7. Now by the running(5), we have generated 3 files: 1AKI_processed.gro, topol.top, and posre.itp.
8. 1AKI_processed.gro is a GROMACS-formatted structure file that contains all the atoms defined within the force field (i.e., H atoms have been added to the amino acids in the protein). The topol.top file is the system topology . The posre.itp file contains information used to restrain the positions of heavy atoms 
9. You can view all the files from vi filename.extension.

# Step Two: Solvation
1. Firstly in this step we start defing a box with dimension with editconf module and fill it with the solvent using solvation module.<br/>
2. gmx editconf -f 1AKI_processed.gro -o 1AKI_newbox.gro -c -d 1.0 -bt cubic (Defining the box)<br/>
3. gmx solvate -cp 1AKI_newbox.gro -cs spc216.gro -o 1AKI_solv.gro -p topol.top (Solvating the box)<br/>
4. Again you can view the created file using vi filename,extension.<br/>
5. 



