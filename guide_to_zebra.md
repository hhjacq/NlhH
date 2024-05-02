**Protein Prediction with zebra**

By Henry Jacques !

Some references you may find useful:
•	Alphafold: https://github.com/google-deepmind/alphafold
•	Foldseek: https://github.com/steineggerlab/foldseek
•	3DFI: https://github.com/PombertLab/3DFI

**How to log in to zebra:**

Unless you have the Reed VPN you must be on Reed Wifi. You must use a mac or linux computer (unless you know how to use shell scripting on Windows. I don’t know how to do that).

Access zebra by typing  ssh jacquesh@zebra.reed.edu

Ask a faculty member with relevant knowledge of this project for the password!

How to access hard drive space for Mellies Lab associated projects:

Type  cd /media/jacquesh/MelliesLab

Please make a new directory for your project. Use this if you have no idea how to do that: https://www.geeksforgeeks.org/basic-shell-commands-in-linux/

How to access protein prediction programs:

Type  cd /media/jacquesh/MelliesLab/3DFI

Ensure this is your working directory for further steps. 






**How to run Alphafold:**

Install the FASTA file in the inputs directory

Run:
python3 3D/alphafold/docker/run_docker.py \
  --fasta_paths=inputs/Your_protein.fasta \
  --max_template_date=Todays_date \
  --data_dir=database\
  --output_dir=exp_results

This will take a while to run.


**How to run Foldseek:**

My recommendation is to run with the HTML output file. 

Have your PDB file stored in the inputs directory.

Also have your PDB database stored in the inputs directory. Now, run as one line:

foldseek easy-search inputs/Your_protein.pdb inputs/Your_database Result_name.html tmp --format-mode 3

If you are using the standard entire PDB database as your target, use the following:

foldseek easy-search inputs/Your_protein.pdb database/RCSB_PDB Result_name.html tmp --format-mode 3

**How to run 3DFI:**

Install the FASTA file in the inputs directory

Type:
export CCP4=/opt/xtal/ccp4-8.0/bin/
export PATH=$PATH:$CCP4

Then use this command:
run_3DFI.pl \
  -f inputs/Your_Protein.fasta \
  -o exp_results \
  -p alphafold \
  -c 32 \
  -a GESAMT \
  -i alphafold





If you have questions consult the Githubs or email me at henryhjacques@gmail.com

Good luck!
