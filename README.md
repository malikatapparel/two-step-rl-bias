This repository contains the computational modelling for the two-step reinforcement learning task (model-based vs model-free), including the parameter recovery analysis.

## What’s inside
This repo contains code to:
- compute sequential learning values (model-free / model-based)
- estimate the model-based vs model-free balance (`w`)
- run parameter recovery to validate the model

## Model (brief)
The task is a 2-stage decision task:
- Stage 1: state `sA`, action `a1`
- Stage 2: state `sB` or `sC`, action `a2`
- Reward is delivered at Stage 2

Model-free learning uses SARSA(λ).  
Model-based values use the task transition structure (common = 0.7 / rare = 0.3).  
Stage-1 choice values combine both systems with a weight parameter:

- `w = 0` → fully model-free
- `w = 1` → fully model-based

Choices are generated with a softmax policy (including a repetition bias term).

## Parameter estimation
Parameters are estimated with Maximum A Posteriori (MAP) estimation using priors:
- `beta1`, `beta2`: gamma
- `p`: normal
- `alpha1`, `alpha2`, `w`, `lambda`: logit-normal

## Parameter recovery
Simulated behavior from virtual participants is refit using the same MAP procedure.
Recovery is evaluated by correlating true vs recovered parameters.

## Files
- `mle_paramsrecovery.ipynb` — MAP fitting + parameter recovery notebook

## How to run
Open the notebook and run all cells:

```bash
jupyter notebook mle_paramsrecovery.ipynb
