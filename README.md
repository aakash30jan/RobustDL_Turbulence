# Robust deep learning for emulating turbulent viscosities 
_Under consideration for publication in the Physics of Fluids, the code will be released upon publication of the manuscript_
###
### Abstract:
From the simplest models to complex deep neural networks, modeling turbulence with machine learning techniques still offers multiple challenges. In this context, the present contribution proposes a robust strategy using patch-based training to learn turbulent viscosity from flow velocities, and demonstrates its efficient use on the Spallart-Allmaras turbulence model. Training datasets are generated for flow past two-dimensional obstacles at high Reynolds numbers and used to train an auto-encoder type convolutional neural network with local patch inputs. Compared to a standard training technique, patch-based learning not only yields increased accuracy but also reduces the computational cost required for training.
### Manuscript: https://arxiv.org/abs/2107.11235


### Requirements:
1. scipy==1.3.1
2. vtk==8.1.2
3. tqdm==4.37.0
4. numpy==1.17.3
5. tensorflow==2.0.0
6. matplotlib==3.2.1
7. tqdm==4.37.0

### Usage:
#### Download
```bash
git clone https://github.com/aakash30jan/RobustDL_Turbulence
```
If git is not installed, you can get the source zip with
```bash
wget -O RobustDLTurbulence.zip https://github.com/aakash30jan/RobustDL_Turbulence/archive/refs/heads/main.zip 
unzip RobustDLTurbulence.zip
```

#### Install Requirements
```bash
cd transport
pip install -r requirements.txt
cd train
pip install -r requirements.txt
```
Make sure you install TF2.0 with GPU support.  

#### Pre-process the training data
Make sure the training data is stored at `case_dir`  
```bash
cd transport
python3 preprocess.py
```
The current `preprocess.py` looks for `.vtu` files in `case_sample/resultats/2d/bulles*.vtu` . Modify the `case_dir`, `resultats_dir`, `fileListVTU` to accomodate your training dataset containing `.vtu` files of interest. 

#### Train the model
```console
cd train
make train
```
You may clean the previous training data, if any, by 
```console
cd train
make clean
```
The file train.py is self-explanatory: We first load the system and user-defined libraries, set the training parameters, load the pre-processed dataset, make a patched-data, load the model architectures, define training and validation steps to suit TF2.0, and then perform the training. Make sure cuda-capabale devices and drivers are visible to Tensorflow, you may need to `module load cudaxxx` depending on the machine configuration. 

### Issues:
Problems? Please raise an issue at [https://github.com/aakash30jan/RobustDL_Turbulence/issues](https://github.com/aakash30jan/RobustDL_Turbulence/issues).

[![Issues](https://img.shields.io/github/issues/RobustDL_Turbulence/issues)](#pydispo)  [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](#pydispo)

### Citation:
Please use https://doi.org/xxx/xxx for citing this code or article. You may also download this .bib file or copy the following bibtex entry. 
```
@article{patil2021robust,
  title={Robust deep learning for emulating turbulent viscosities},
  author={Patil, Aakash and Viquerat, Jonathan and Haber, George El and Hachem, Elie},
  journal={arXiv preprint arXiv:2107.11235},
  year={2021}
}
```
