# Use Cases  

## Background  
Clustering a set of molecules into different groups based on their molecular properties is very useful to establish   
understanding of how features are related to the separation. Good separation of chemical property is fundamental   
to data reprentation and visualization.

Performances of common clustering methods is highly dependent on the input data. Dimensionality reduction (DR) is  
often applied to map the high-dimensional data into clustering-friendly space to allow for easier separation. Compared  
to linear DR methods (e.g. PCA, CCA), deep neural networks has demonstrated its power in nonlinear mapping of high-  
dimensional domain into reduced-dimensional latent spaces. The latent representation of data can then be used as  
input for clustering tasks.

Combining deep neural network (DNN) based DR and K-means clustering would require a two-phase training procedure  
which optimize on both the representation learning and the clustering. 

## Objectives  

Achieve robust and efficient embedding and clustering of high dimensional chemical datasets (e.g, ChEMBL with 1.8M chemicals),  informed by domain knowledge, *_e.g._*, bio-degration or molecular toxicity.

## Components  

### Hign Dimemsional Feature Generation and Selection  
Generate reproducible features using existing packages like [_RDKit_](https://www.rdkit.org/) and [_Mordred_](https://pypi.org/project/mordred/), and select those based on both feature disctribution and domain knowledges

### Baseline Clustering Tasks  
Used original high-dimensional input to do baseline clustering tasks as bench-marking

### Training Embedding Layers
Autoencoder neural network to reduce dimension of the given dataset and evalutate the reconstruction loss

### Embedding-Clustering Co-optimization
Apply K-mean clustering algorithm or other unsupervised/supervised clustering methods to the latent space, co-optimize the loss of both clustering and embedding

### Validation  
Evaluate the clustering result by evaluating the reconstruction loss of autoencoder and the quality of clustering (K-mean) method
     
1. Smaller synthetic dataset with labels <br>
A small synthetic dataset that contains 100+ feature and 1000+ data points is used to estabulish a valid model. The model could be evaluated by the metrics of cluster quality, reconstruction loss and the clustering impurity. 

2. Larger unlabeled dataset <br>
1.8M chemicals on [_ChEMBL_](https://www.ebi.ac.uk/chembl/) are used to evaluate the optmized model architecture built from the small dataset (the parameters for larger dataset will be tuned accordingly) combining the metrics of clustering and reconstruction.




