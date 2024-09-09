# Rustody_image

This Apptainer image is based on my ImageSmith and contains my Rust programs.
Therefore the logics is different from my 'normal' Bioinformatics tools.

These normal images are accessed via a Jupyter notebook. This image does not provide a Jupyter notebook, just command line tools.


When installed as a module on COSMOS this tool is called Rustody/<Version> and loading this will put a Rustody program into your path.
This 'program' loads the apptainer image an runs every command you issue after 'Rustody' as command in the image:

```sh
ml Rustody/1.0

Rustody echo "I am alive!"
```

This will run the ``echo "I am alive!"`` in the apptainer image.

# Create the image

This repository is the definition of the Rustody module on COSMOS.
And at the same time an example of how to build a apptainer image that provides command line tools.

## Install

```sh
git clone 
cd Rustody_image
make restart
make build
```

Afterwads you have both the sandbox as well as the image in your ``Rustody_image`` folder.
The two script `shell.sh` and `run.sh` let you interact with the sandbox and image respectively.

The script bin/Rustody does also work in this setting:

```sh
bash bin/Rustody echo "I am alive!"
```

## Usage

Currently these Rust tools are installed in the image:

	1. https://github.com/stela2502/Rustody
	2. https://github.com/stela2502/multi_subset_bam
	3. https://github.com/stela2502/bam_aligner

To call e.g. the ``multi_split_bam`` from this image folder you can do this:

```sh
bash bin/Rustody multi_split_bam -b <bam file> -v barcodes_louvain0.txt,barcodes_louvain1 -o <outfiles_prefix>
```

With ``barcodes_louvain0.txt`` containing the sequence barcode for each cell in the louvin cluser 0 for this bam file - one per line.


