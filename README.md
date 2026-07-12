# Code for Solving the Relative Thue Inequality $|F_t(X,Y)| \leq 1$

This repository contains the **SageMath** computational scripts used to verify and establish bounds and constants for the proofs in an upcoming article based on my PhD thesis. The initial (rough but functional) versions of these scripts, used for my thesis, are viewable by anyone with a CoCalc.ai account, and be found here: https://cocalc.com/share/public_paths/f987f45c16aa187276215637a54169592a29b56c .

The overarching goal of the work is to classify all non-trivial solutions to the relative Thue inequality:
$$|F_t(X,Y)| \leq 1 \quad \text{where} \quad F_t(X,Y) = X^4 - tX^3Y - 6X^2Y^2 + tXY^3 + Y^4$$
for non-real quadratic integers $t \in \mathcal{O}_{\mathbb{Q}(t)}$. 

The code classifies Galois groups, bounds the indices of unit groups, and applies Baker's Method (using theorems of Laurent and Mignotte) alongside Legendre's continued fraction criterion to provide the computational component to our result finding all non-trivial solutions to the relative Thue inequality $|F_t(X,Y)| \leq 1$. Due to previous work on this equation (see Citations below), we can assume an upper bound on $|t|$ of $100$. This is not necessary for the Galois results in Chapter 3, Section 1.

## Prerequisites
* [SageMath](https://www.sagemath.org/) (Testing was conducted on SageMath 10.7)
* A standard Python/Sage execution environment (Jupyter Notebook, VS Code, or terminal).

## File Structure

The scripts are organized to match the flow of the mathematical proofs in the thesis.

### Chapter 2: Establishing Lower Bounds
* **`Chapter_2_small_solutions_search.ipynb`** Executes an exhaustive search using norm divisors to find all solutions with $\min\{|x|, |y|\} \leq 40$. This establishes the baseline lower bound required for the later continued fraction reductions. Uses norm divisor properties and symmetries of the equation to optimize the search space over imaginary quadratic integers.

### Chapter 3: Field Arithmetic and Unit Groups
* **`Chapter_3_Galois_classification.ipynb`**
  Performs the computations used in the proofs of results classifying Galois group $\mathcal{G}_t = \text{Gal}(K_tK_{\overline{t}}/\mathbb{Q})$ and checks the cases where $\mathcal{G}_t \simeq D_4$ or $C_4 \times C_2$.
* **`Chapter_3_unit_group_bounds.ipynb`**
  Bounds the index $I$ of $\langle \zeta, \alpha, \alpha', u_{M_t} \rangle$, a maximal subgroup of the unit group. This bound uses Rouché's Theorem to establish lower bounds on polynomial roots circumventing the lack of an explicit relative discriminant.

### Chapter 4: Baker's Method and Reduction
* **`Chapter_4_general_(independent)_cases.ipynb`** *(General Cases)*
  Applies Laurent's Theorem to establish a very large upper bound on $|y|$, and executes continued fraction reduction via Legendre's Criterion to reduce the bound below 40.
* **`Chapter_4_Dihedral_(dependent)_cases.ipynb`** *(Dihedral Edge Cases)*
  Applies Mignotte's Theorem for the specific $D_4$ cases where the roots are multiplicatively dependent, again establishing an upper bound and reducing it using Continued Fraction methods.

## How to Run the Code

These scripts are optimized but some are computationally intensive. By default, the heavy exhaustive search functions in these cases are disabled for quick testing. To run the full computations, change the `RUN_EXHAUSTIVE_SEARCH = False` flag to `True` at the top of the relevant script.

## Citations

If you use this code in your research, please cite my PhD thesis (until the article is available on arXiv, I will edit this file to add the link to that when it is available). You can use the following BibTeX entry:

```bibtex
@phdthesis{B.Earp-Lynch2026thesis,
  author       = {Benjamin Earp-Lynch},
  title        = {A Family of Relative Thue Equations},
  school       = {Carleton University},
  year         = {2026},
  type         = {PhD thesis}
}
```
The assumed bound on $|t|$ is due to the following work.

Benjamin Earp-Lynch, Bernadette Faye, Eva Goedhart, Daniel Wiseniewski, and Ingrid Vukusic. On a simple quartic family of Thue equations over imaginary quadratic number fields. Acta Arith. 208 (2023), no. 4, 355-389. https://doi.org/10.4064/aa230329-19-6.