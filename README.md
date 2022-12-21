# Inference Drift Analysis on Squeezenet Neural Network using IBM Analog Hardware Accelerator Kit.

This is the final project for High Performance Machine Learning class at Columbia University by Pierre Tessier and Serrana Aguirregaray.

Professors: Kaoutar El Maghraoui and Parijat Dube.

## Motivation

One of the biggest challenges in current Neural Networks is the energy consumption. Conventional computers perform calculations by transferring data between memory and processor, which takes time and energy. By leveraging the physical properties of the in-memory computing devices that Analog AI offers, computation happens at the same place where the data is stored, which in turn reduces energy consumption drastically.This allows us to have the speed and energy-efficiency required to move AI forward.

## Project Outline

This project explores the inference drift of a hardware aware trained Squeezenet over the Visual Wake Words Dataset. This was done by pre-training the model digitally and then retraining it for a single epoch using IBM Analog AI. Later, a parameter sweep over rpu configurations (Analog AI's way of defining various settings of the RPU tile or the Analog hardware), was used to evaluate the model's drift.

## Installation

To run the experiments one first need to install CUDA 11.7, by following the steps explained [here](https://docs.nvidia.com/cuda/archive/11.7.1/). Then, Intel MKL is also required and should installed following the [official instructions](https://www.intel.com/content/www/us/en/developer/articles/guide/installation-guide-for-oneapi-toolkits.html). Finally, in the root directory of the [IBM's analog toolkit](https://github.com/IBM/aihwkit), run the following commands

```
ENVNAME=aihwkit
conda deactivate
conda create -n $ENVNAME python=3.8
conda activate $ENVNAME

conda install pytorch torchvision torchaudio cuda=11.7 -c pytorch -c nvidia

pip install pylint==2.9.6
pip install mypy==0.971

conda install -y cmake pybind11 mkl-include
conda install -y scikit-build
conda install -y -c anaconda protobuf
conda install -y requests pytest pylint=2.9.6  pycodestyle parameterized scipy matplotlib
conda install -y pycodestyle twine jinja2 entrypoints
conda install -y pandas seaborn
pip install wget cibuildwheel mypy==0.971 parameterized pymongo pytz PyYAML
pip install prettytable
pip install wandb pyvww torchinfo

# to compile: 

python setup.py build_ext -DCMAKE_BUILD_TYPE=Debug -DCMAKE_EXPORT_COMPILE_COMMANDS=TRUE --inplace -DRPU_BLAS=MKL -j16 -DUSE_CUDA=ON -DRPU_CUDA_ARCHITECTURES="60;70" 2>&1 | tee output_$(date +"%F-%T")
``` 
> Surprisingly we have not been able to use pre-installed GCP images of CUDA and MKL, and had to reinstall everything manually everytime.

## Results

## References

- IBM Analog Hardware Acceleration Kit: https://github.com/IBM/aihwkit
- Analog AI: https://researcher.watson.ibm.com/researcher/view_group.php?id=7716 
- Squeezenet: https://arxiv.org/abs/1602.07360
- Visual Wake Words: https://arxiv.org/abs/1906.05721
- RPU configurations: https://aihwkit.readthedocs.io/en/latest/using_simulator.html#rpu-configurations
