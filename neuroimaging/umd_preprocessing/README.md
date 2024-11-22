# fMRI Preprocessing at UMD

- [setup.sh](https://github.com/hspopal/tutorials/blob/main/neuroimaging/umd_preprocessing/code/setup.sh)
- [heuristi.py]()
- [preprocessing-bswift.sh]()
- [heudiconv.sh]()
- [fmriprep-bswift2.sh]()
- [data_transfer.sh]()

## Background Information
These series of scripts were written to get a new MRI project started, download data, and preprocessing it using fmriprep. These steps are done on a lab server, such as neuron in the DSCN lab. The fmriprep preprocessing takes place on the BSWIFT2 high performance cluster (HPC). The scripts can be modified for your needs, for different datasets and servers. All of the scripts references in this documentation are available in the `code` directory. These scripts will have to be placed in specific locations for them to work together. All of those details are noted below.

These scripts are meant to make some tedius work in processing your data more streamlined. Users of these scripts should understand most of the underlying code. Users should absolutely have basic knowledge of the command line and langauges such as Bash. Users should be able to easily navigate through directories and remote servers. If you are not comfortable with these skills, see these tutorials and tread carefully. 


## Setup
For a new project, a new project directory will have to be created in BIDS format. For this pipeline, that includes the main project directory. The main project directory referenced here is `/data/neuron/TRW/reprocessed`. This dataset utilizes a previously collected dataset, in which I converted everything to BIDS format and ran fmriprep. Which is why there is a `reprocessed` directory. Subdirectories should also be created for the following:
- `sourcedata`
    - Location for the raw dicom files will be located
- `Nifti`
    - Location for NIFTI files
- `code`
    - Location for scripts and other code
- `derivatives`
    - Location for "derivatives" from this project, such as the preprocessing output and any analyses 

Once these files have been created, place the `preprocessing-bswift2.sh`, `heuristic.py`, and `heudiconv.sh` scripts into the code directory. If you will not being using a HPC (e.g. BSWIFT), then place the `fmriprep-bswift2.sh` script in the code directory as well. **Note:** this documentation assumes that you will be using a HPC for fmriprep preprocessing. If you are not, you will have to change the relevant paths and skip certain steps. 

The `setup.sh` script is meant to help users run the relevant commands for this pipeline. The beginning of the script has users set a quick variable for the project or BIDS directory and create a list of subject IDs that will be used in for loops to complete the pipeline steps. 


## Preprocessing
The main script for this pipeline is the `preprocessing-bswift2.sh` file. Certain variables and paths need to be edited in this file for your specific setup. These can be found between lines 79 and 89. 

### Downloading dicoms
The next step would be to download the dicoms for your participants. For a single participant you can run the code:
```
sh code/preprocessing_TRW-bswift2.sh -s 001 -d
```
This will download the dicoms from subject 001 (with the appropriate prefix you noted in the above script) from the MNC servers and place them in the `sourcedata` directory.


### Converting dicoms to NIFTIs


### Running fmriprep


### Transfer data


