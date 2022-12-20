# Inference Drift Analysis on Squeezenet Neural Network using IBM Analog Hardware Accelerator Kit.

This is the final project for High Performance Machine Learning class at Columbia University by Pierre Tessier and Serrana Aguirregaray.

Professors: Kaoutar El Maghraoui and Parijat Dube.

## Motivation

One of the biggest challenges in current Neural Networks is the energy consumption. Conventional computers perform calculations by transferring data between memory and processor, which takes time and energy. By leveraging the physical properties of the in-memory computing devices that Analog AI offers, computation happens at the same place where the data is stored, which in turn reduces energy consumption drastically.This allows us to have the speed and energy-efficiency required to move AI forward.

## Project Outline

This project explores the inference drift of a hardware aware trained Squeezenet over the Visual Wake Words Dataset. This was done by pre-training the model digitally and then retraining it for a single epoch using IBM Analog AI. Later, a parameter sweep over rpu configurations (Analog AI's way of defining various settings of the RPU tile or the Analog hardware), was used to evaluate the model's drift.

## Results
