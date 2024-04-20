# Molecules search
Ideas and solutions to the problem of searching for molecules with maximum lgK, created at the final of the National Technological Olympiad in the field of AI.

## Some words about task
It is required to generate 100 molecules with the maximum possible lgK. A set of 250 molecules with a known lgK value is presented for training.

We also faced a number of restrictions on molecules:

1. Each molecule should include only the elements from the list: C, H, O, N, P, S
2. Each molecule must include at least three different elements from the list above
3. Each molecule should contain a total of no more than 12 atoms of the following elements: O, N, P, S
4. The molecular weight of each molecule is <= 500 
5. The index of synthetic accessibility of each molecule is < 5 
6. The Tanimoto metric of molecules in a set < 0.5

## Our solutions

All solutions generally consist of the following steps: 
1. Using one of the methods below, a set of molecules is generated
2. The set is evaluated for passing through all the conditions of the task
3. lgK is considered for the set

The CatBoost model has been used in all our solutions to estimate the lgK value. You can find out exactly how the model trained in  ```CatBoost.ipynb```

The results of the work of various methods of generating molecules are presented below:

| Method name  | Best Result (mean LgK) | 
|--------------|:----------------------:|
| PPO          |          15,5          | 
| CombiChem    |        **25,3**        |
| Permutations |          15,8          |

The table shows the results obtained from the testing system of the competition organizers.

## File Navigation:
```CatBoost.ipynb``` - training a catboost model to predict lgK by SMILES string

```MRL.ipynb``` - a PPO-based solution from the mrl library

```CombiChem.ipynb``` - a solution based on a genetic algorithm

```Permutations.ipynb``` - a solution based on permutations of groups within molecules

```Isomers.ipynb``` - a file for obtaining isomers of the molecule with the largest lgK.

## Conclusion

We understand that the solutions presented are not ideal and can be significantly improved. In this repository, we have shown how our team solved this problem directly at the Olympiad itself.