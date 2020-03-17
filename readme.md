# AI Song Contest - KTH/KMH+Doremir
____
## Introduction

The AI Song Contest is an online project organised by Dutch public broadcaster VPRO in collaboration with NPO Innovation and NPO 3FM with the idea of translating the rather complicated matter of AI into the universal language of music to make it more accessible to the general public. This repository represent the work of the team "KTH/KMH+Doremir" for the creation of the *"Come To Ge Ther"* song entry. The song arises from a human-AI collaboration. It was assembled from human-curated content generated by an AI trained on a dataset composed of syllable-note pairs. Thus, the AI learns to jointly generate lyrics and melody. The lyrics are represented in a syllabic way, and so to generate a multiple-syllabic word requires several steps of the process. The picture below shows where material comes from in the mix of the song. Furthermore, the lyrics heard in the introduction are synthesized from computer models of female and male voice (i.e., Google wavenet).

![Info image](/repo_images/visual2.jpg)

## Setup

First, download the dataset. It can be obtained here: https://github.com/yy1lab/Lyrics-Conditioned-Neural-Melody-Generation

Second, set up the different paths for the project inside the file *common.py* and create the missing directories if needed

Third, install the dependencies by running:

```
pip install -r requirements.txt 
```

If you want to use the pre-trained model on a sequence length of 60, it is downloadable here: https://drive.google.com/open?id=1J3C_XbGr64u5RVRT5XwjDZWow7YZBlCx

## Run the project

The file *main.py* provides an interface to run all the functionalities of the project. The list of available commands is accessible by calling:

```
python main.py -h
```

And it will produce as output the following:

```
usage:  [-h] [--eurovision]
        {train,generate_bulk,evaluation_baseline,evaluation_generated} ...

positional arguments: {train, generate_bulk, evaluation_baseline, evaluation_generated}
    train                   train the network
    generate_bulk           generate in bulk MIDI and lyrics from the trained
                            network
    evaluation_baseline     generate evaluation plots and statistics for the
                            dataset
    evaluation_generated    generate evaluation plot and statistics for the bulk
                            generated MIDI files

optional arguments:
  -h, --help                show this help message and exit
  --eurovision              specify whether using the Eurovision dataset or not
```

### Examples

Train the network for 100 epochs and save the weights under the name *run_100_epochs*:

```
python main.py train run_100_epochs 100
```

Load the trained network and generate in bulk 50 sequences:

```
python main.py generate_bulk run_100_epochs 50 ./out_bulk/
```

Generate the baseline evaluation report with the name *baseline_report*:

```
python main.py evaluation_baseline baseline_report
```

Generate an evaluation report based on the bulk generation of 50 sequences from the trained network and save it under the name of *generated_report*:

```
python main.py evaluation_generated run_100_epochs generated_report 50
```
