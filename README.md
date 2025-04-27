# numerical-computing-project-4--image-deblurring-and-conjugate-gradient-solver-solved
**TO GET THIS SOLUTION VISIT:** [Numerical Computing Project 4 -Image Deblurring and Conjugate Gradient Solver Solved](https://www.ankitcodinghub.com/product/numerical-computing-project-4-image-deblurring-and-conjugate-gradient-solver-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;122085&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;2&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (2 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;Numerical Computing  Project 4 -Image Deblurring and Conjugate Gradient Solver Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (2 votes)    </div>
    </div>
1. Simple Image Deblurring – Problem Definition

Suppose we have a blurred image B which we want to refine (or deblur) and we know the transformation that lead to this blurred image. Then how can we efficiently reconstruct the original image? Let X ∈ Rn×n be the original square, grayscale image matrix, where each matrix entry corresponds to one pixel value. Hence X corresponds to an image with n pixels per side. We can convert the original image matrix X into a column vector x ∈ Rn2, where the entries of X get stacked into a vector, either row- or column-wise. This process is referred to as vectorization . If we now define as b the vectorized form of the blurred image B, we can write the following system of equations:

Ax = b, (1)

Here, A ∈ Rn2×n2 indicates the transformation matrix coming from the the repeated application of what is referred to as the ”image kernel” which in our case produces a blurring effect. An excellent visual explanation of the kernel operation can be found at [4]. Our objective will be to solve the linear system in Eq.[1] for the original vectorized image x, where the transformation matrix A and the blurred image B (and hence b) are known. By solving the system, we can recover the original image, getting rid of the blurring effect applied on top of it.

1.1. Visualization and Vectorization

The image in consideration is black and white and the corresponding image matrix can be visualized with the command imshow (see Matlab documentation). We can vectorize the blurred image matrix with the command B(:). The vectorization ordering can be arbitrary, by column, row or whatever fits best with the data access pattern; however, it must correspond with A. In our case we require row by row vectorize (Matlab default is by column). This can be achieved using the command B=B’; b=B(:);.

1.2. Transformation Matrix

A blurred image pixel is the weighted average of the surrounding pixels. These weights are defined by the kernel matrix K ∈ Rd×d. The much bigger transformation matrix A is constructed from the kernel matrix, such that the non-zero elements of each row of A correspond to the values of K. The detailed construction of the transformation matrix is omitted for brevity, see [4]. The following attributes should be noted:

Borders: The transformation matrix ignores the elements outside of borders of the matrix, (max(i,j) &gt; n).

Banded Matrix: A is a d2-banded matrix, where . This means that A is sparse, and thus one should use sparse data structures. Recall that A is of dimension n2 × n2, defining a dense matrix of that size will not fit on your system. For example, if n = 250 we would need 31 GB (i.e., 8n2 · n2 Bytes) of memory.

For this assignment you will use the provided transformation matrix A.mat. It is generated from the normalized blur image kernel

, (2)

and operates on a “row-vectorized” image matrix.

2. Conjugate Gradient

The CG algorithm starts from an initial guess x0 and applies a series of matrix-vector and vector-vector operations until the desired tolerance is reached:

Algorithm 1 *

Conjugate Gradient Algorithm

1: r ← b − Ax0

2: d ← r

3: ρold ← hr,ri

4: for i =0,1,… do

5: s ← Adi

6: α ← ρold/hd,si

7: x ← x + αd

8: r ← r − αs

9: ρnew ← hr,ri

10: β ← ρnew/ρold

11: d ← r + βd

12: ρold ← ρnew

13: end for

2.1. Symmetry and Positivity

In our case A is symmetric and of full rank but not positive-definite. We can bypass this issue by solving the augmented system Eq. [3]. The pre-multiplication with AT , results in the positive-definite augmented transformation matrix A˜.

AT Ax = AT b (3)

Ax˜ =˜b.

2.2. Condition Number

An important attribute of a linear system Ax = b is its condition number κ(A). This is the relation of the sensitivity of the solution x, to changes in b. If small changes in b results in large changes in x, the system is called ill-conditioned and the condition number of the system is large. The convergence rate of CG is hindered when the system has a high condition number. Notice that the number of iterations needed to find the exact solution is not related to κ(A), but rather equal to the number of unique eigenvalues. The condition number of a square matrix A is

(4)

with σ indicating the singular values of A. For a real symmetric matrix, the singular values are equal to the absolute value of the eigenvalues: σ = |λ|.

In our case, matrix A is symmetric and real, and this implies that the condition number is given by the ratio of the magnitudes of the maximum and minimum eigenvalues. We can check an estimate of the condition number of A by using the Matlab command condest (or cond for a dense matrix). Notice that this command will take a long time on large matrices. Furthermore, the transformation matrix is ill-conditioned and – to make matters worse – we will be solving the augmented system in Eq.[3] with condition number κ(A)2 = κ(A˜). These factors will unfortunately deteriorate the convergence rate of our deblurring program, but this problem can be partially mitigated through preconditioning, as explained in the next section.

2.3. Preconditioning

A symmetric positive-definite preconditioner P is selected such that P−1A˜ ≈ I, that is P−1 approximates A˜−1. We can decompose the preconditioner such that P = LLT , where L is the Cholesky factor (see [2]). Our intention is to solve the preconditioned augmented system

P−1Ax˜ = P−1˜b (5)

. (6)

¯˜) &lt; κ(A˜) and to decrease the range of the eigenval-

This operation is done to both decrease the condition number κ(A ues. The underlying caveat here is that the preconditioner should be computationally inexpensive to find.

To meet the desired properties of the preconditioner, a common approach is to use incomplete Cholesky (IC) factorization (see [1]). With IC, we only compute the Cholesky factorization of the non-zero elements of A˜. This cheap factorization of A˜ gives us the preconditioner P = FT F, where F is the sparse IC factors. This routine can fail since the existence of F is not guaranteed (note that F is forced to be sparse). To amend this issue, a heuristic approach is used to apply a diagonal shift of P, enforcing positive-definiteness and making F computable. The detailed explanation of this routine is outside the scope of this assignment. We can use the Matlab ichol command for the IC factorization (please refer to the Matlab documentation for more information).

The Assignment

Read this document and Section 7.4 of the textbook [1] in order to answer the following questions.

1 . General Questions [10 points]

1. What is the size of the matrix A?

2. How many diagonal bands does A have?

3. What is the length of the vectorized blurred image b?

2. Properties of A [10 points]

1. If A is not symmetric, how would this affect A˜?

2. Explain why solving Ax = b for x is equivalent to minimizing over x, assuming that A is symmetric positive-definite.

3. Conjugate Gradient [30 points]

1. Write a function for the conjugate gradient solver [x,rvec]=myCG(A,b,x0,maxitr,tol), where x and rvec are, respectively, the solution value and a vector containing the residual at every iteration.

2. In order to validate your implementation, solve the system defined by Atest.mat and btest.mat. Plot the convergence (residual vs iteration).

3. Plot the eigenvalues of Atest.mat and comment on the condition number and convergence rate.

4. Does the residual decrease monotonically? Why or why not?

4. Deblurring problem [35 points]

1. Solve the deblurring problem for the blurred image matrix B.mat and transformation matrix A.mat using your routine myCG and Matlab’s preconditioned conjugate gradient pcg. As a preconditioner, use ichol to get the incomplete Cholesky factors and set routine type to nofill with α = 0.01 for the diagonal shift (see Matlab documentation). Solve the system with both solvers using max iter = 200 tol = 10−6. Plot the convergence (residual vs iteration) of each solver and display the original and final deblurred image. Comment on the results that you observe.

Hint : Check the Matlab description of the pcg() routine to make sure that you compute the residual norm in the same manner to be able to properly compare them.

2. When would pcg be worth the added computational cost? What about if you are deblurring lots of images with the same blur operator?

Quality of the code and of the report [15 points]

The highest possible score of each project is 85 points and up to 15 additional points can be awarded based on the quality of your report and code (maximum possible grade: 100 points). Your report should be a coherent document, structured according to the template provided on iCorsi. If there are theoretical questions, provide a complete and detailed answer. All figures must have a caption and must be of sufficient quality (include them either as .eps or .pdf).

If you made a particular choice in your implementation that might be out of the ordinary, clearly explain it in the report. The code you submit must be self-contained and executable, and must include the set-up for all the results that you obtained and listed in your report. It has to be readable and, if particularly complicated, well-commented.

Additional notes and submission details

In-class assistance

If you experience difficulties in solving the problems above, please join us in class either on Tuesdays 15:30-17:00 or on Wednesdays 13:30-15:00 in room C1.03.

References

[1] Linear Systems: Iterative Methods, Chapter 7, SIAM Book A First Course on Numerical Methods, C. Greif, U. Ascher.

[2] The Cholesky decomposition, Chapter 5, Section 5.5, SIAM Book A First Course on Numerical Methods, C. Greif, U. Ascher.

[3] An Introduction to the Conjugate Gradient Method Without the Agonizing Pain, http://www.cs.cmu.

edu/˜./quake-papers/painless-conjugate-gradient.pdf

[4] Image Kernels, http://setosa.io/ev/image-kernels/
