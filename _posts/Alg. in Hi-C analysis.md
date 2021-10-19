# Hi-C analysis

## Compartments

### call compartments

- input: a dense cis matrix
- output: eigvec_table *the contribution (projection coefficient) of each column to the PCA1 vector*
- perquisite: ref to PCA

- [ ] Why need observed_over_expected
	*observed can not discriminate the "biological interaction"*
1. calculate observed_over_expected matrix:
	Since observed matrix is what you get from the valid pairs, the key step is to calculate the expected matrix.
	
	Following the expected interacting frequency in polymer model ([reference](https://academic.oup.com/nargab/article/2/2/lqaa020/5813971) (Equa(1), Equa(4) & Equa(5)). 
	
	To put it simple:     The diagonals of the matrix, corresponding to contacts between loci pairs with a fixed distance, are grouped into exponentially growing bins of distances; the diagonals from each bin are normalized by their average value.
	
	- [ ] hand painted illustration

	`	data[offset + j, j] /= mean_pixel
	return data`
	
2. eigendecomp：
	(if symmetric) `	mat -= 1.0
		_eigvals, _eigvecs = scipy.sparse.linalg.eigsh(mat, _n)
	return _eigvecs`
	
	Solves `A * x[i] = w[i] * x[i]`, the standard eigenvalue problem for w[i] eigenvalues with corresponding eigenvectors x[i].
   
    * since the variance of A projecting onto x[i] is `x[i]^T * A`, to maximize it means to find the maximized w[i] with the corresponding x[i]
    * why the final pca1 values we need is between [-1,1]: the maximal projection direction is the colliner direction, with the projection coefficient `cos(0)=1`

### saddle plot and compartment strength
- input: a dense cis matrix,  eigvec_table
- output: a matrix to be visualized, compartment strength
1. sort the dense matrix by PC1 values
2. aggregate the sorted matrix
3. calculate the compartment strength:
	a: mean (mat_i,j), where i, j \geq percentile(.75)[sorted_index] or \leq percentile(.25)[sorted_index]
	b: mean (mat_i,j), where i, j \geq percentile(.75)[sorted_index] or \leq percentile(.25)[sorted_index]
	c: mean (mat_i,j), where only one of i, j  \geq percentile(.75)[sorted_index] or only one of i, j  \leq percentile(.25)[sorted_index]
	compartment strength  = a+b-c
## TADs

### call TADs

1. insulation score:

![is](./figs/IS.png)

2. delta vector

![delta](./figs/delta.png)

	For each bin (reference point) the average insulation differences are calculated between all points up to 100 kb left of the reference point relative to the reference point. The same is repeated for all points up to 100 kb right of the reference point. The delta value is then defined as the difference between the mean (left difference) and mean (right difference).

3. call boundary

![vis](./figs/vis.png)

	local minima in delta vector with boundary strength bigger than a threshold

## ChIP-seq
![chip](./figs/chip_analyze.png)
### peak calling
[reference](https://hbctraining.github.io/Intro-to-ChIPseq/lessons/05_peak_calling_macs.html)
### signal enrichment

### chromHMM

## Agglomeric clustering

The AgglomerativeClustering object performs a hierarchical clustering using a bottom up approach: each observation starts in its own cluster, and clusters are successively merged together. The linkage criteria determines the metric used for the merge strategy:

Ward minimizes the sum of squared differences within all clusters. It is a variance-minimizing approach and in this sense is similar to the k-means objective function but tackled with an agglomerative hierarchical approach.

If the ground truth labels are not known, evaluation must be performed using the model itself. The Silhouette Coefficient (sklearn.metrics.silhouette_score) is an example of such an evaluation, where a higher Silhouette Coefficient score relates to a model with better defined clusters. The Silhouette Coefficient is defined for each sample and is composed of two scores:

a: The mean distance between a sample and all other points in the same class.

b: The mean distance between a sample and all other points in the next nearest cluster.

The Silhouette Coefficient s for a single sample is then given as:

 
The Silhouette Coefficient for a set of samples is given as the mean of the Silhouette Coefficient for each sample.

The score is bounded between -1 for incorrect clustering and +1 for highly dense clustering. Scores around zero indicate overlapping clusters.

The score is higher when clusters are dense and well separated, which relates to a standard concept of a cluster.

The Silhouette Coefficient is generally higher for convex clusters than other concepts of clusters, such as density based clusters like those obtained through DBSCAN.

## Sampling

## Single cell tutorial






  

