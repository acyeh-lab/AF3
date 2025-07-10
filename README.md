## Using AF3 on the Computing Cluster

This is a quick tutorial on how to set up default AF3 on the FHCC computing cluster.  Thanks to Phil Bradley for guidance!

- In log-in computing node, create an "input" and "output" directory
- In the "input" directory, upload the "test1.json", which contains 3 protein chains as a default (this can be TCR/MHCII/peptide, for example)
  - You can put multiple jobs into a single JSON file by adding a comma after the last "}" and putting another block like this one (ie several blocks like this separated by commas and between the first "[" and the last "]".
  - Or just put multiple JSON files in the inputs folder. This "server" JSON format is described here: https://github.com/google-deepmind/alphafold/tree/main/server There is a newer format that you can also use, see here: https://github.com/google-deepmind/alphafold3/blob/main/docs/input.md
- Next, upload and the file "af3run.sh" in this repository.
  - Edit the following line in "af3run.sh":
```
export OUTPUT_DIR="YOUR OUTPUT FOLDER DIRECTORY HERE"
export INPUT_DIR="YOUR INPUT FOLDER DIRECTORY HERE"
```
- Now, you're ready to submit the job as follows in the directory of "af3run.sh" shell script:
```
sbatch af3run.sh
```
- Check the output slurm file for error messages; otherwise the final output should be accessible in the "OUTPUT_DIR" that was specified above.
