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
- [ ] this part
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

## Sampling

## Single cell tutorial






​    


