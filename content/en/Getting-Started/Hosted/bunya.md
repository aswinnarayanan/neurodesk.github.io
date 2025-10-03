---
title: "Bunya"
linkTitle: "Bunya"
weight: 2
aliases: 
- /docs/getting-started/hosted/bunya
description: >
  Use Neurodesk on Bunya (only for researchers with access to Bunya!)
---


<!-- markdown-link-check-disable -->
Neurodesk is installed at the University of Queensland's supercomputer "Bunya". To access neurodesk tools you need to be in an interactive job (so either start a virtual desktop via Open On-Demand: https://bunya-ondemand.rcc.uq.edu.au/pun/sys/dashboard) or run:
```bash
salloc --nodes=1 --ntasks-per-node=1 --cpus-per-task=1 --mem=5G --job-name=TinyInteractive --time=01:00:00 --partition=debug --account=REPLACE_THIS_WITH_YOUR_AccountString srun --export=PATH,TERM,HOME,LANG --pty /bin/bash -l
```
<!-- markdown-link-check-enable -->

Then load the neurodesk modules:
```bash
module use /sw/local/rocky8/noarch/neuro/software/neurocommand/local/containers/modules/
export APPTAINER_BINDPATH=/scratch,/QRISdata
```

Now you can list all modules (Neurodesk modules are the first ones in the list):
```bash
ml av
```

Or you can module load any tool you need:
```bash
ml qsmxt/6.4.1
```

If you want to use GUI applications (fsleyes, afni, suma, matlab, ...) you need to overwrite the temporary directory to be /tmp (otherwise you get an error that it cannot connect to the DISPLAY):
```bash
export TMPDIR=/tmp 
```

For matlab you also need to create a network license file in your ~/Downloads/network.lic:
```bash
cat <<EOF > ~/Downloads/network.lic
SERVER uq-matlab.research.dc.uq.edu.au ANY 27000
USE_SERVER
EOF
```

NOTE: If you are using AFNI on Bunya then the default detach behavior will cause SIGBUS errors and a crash. To fix this run AFNI with:
```bash
afni -no_detach
```

NOTE: MRIQC has its $HOME variable hardcoded to be /home/mriqc. This leads to problems on Bunya. A workaround is to run this before mriqc:
```bash
export neurodesk_singularity_opts="--home $HOME:/home"
```

If you are missing an application, please contact mail.neurodesk@gmail.com and ask for the neurodesk installation to be updated on Bunya :)

### Using this inside a jupyter notebook
You need to install this in addtion:
```bash
pip install jupyterlmod
```

Then start a notebook and run these commands:
```python
import module
await module.load('niimath')
```
