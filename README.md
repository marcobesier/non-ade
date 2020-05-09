# NonADE
A [MAGMA](http://magma.maths.usyd.edu.au/magma/) function that returns the
non-simple (also called "non-ADE") singularities of the associated double cover
of a square root in two variables.

Note: This README is work in progress and not final yet.

## What is NonADE?

`NonADE` is a [MAGMA](http://magma.maths.usyd.edu.au/magma/) function that
returns the non-simple singularities of the associated double cover of a square
root in two variables.
For all examples we tested so far, `NonADE` performs the singularity
classification in less than a second. Therefore, the *free*
[MAGMA Online Calculator](http://magma.maths.usyd.edu.au/calc/) should suffice
for the vast majority of cases.

## Why NonADE?

[MAGMA](http://magma.maths.usyd.edu.au/magma/) has a built-in function to check
whether all singularities of an affine or projective _surface_ are of ADE
type, but lacks a similar function for hypersurfaces in weighted projective
space. The `NonADE`function fills this gap.

## How it works?

The `NonADE` makes use of the fact that

1. the singularities of a double cover of the projective plane are in one-to-one
   correspondence with the singularities of its branch curve.

2. if _p_ is a singularity of the double cover and _q_ is the corresponding
   singularity of the branch locus, then _p_ and _q_ have the same singularity
   type. For example, if _q_ is a simple curve singularity of type A1, then
   _p_ is a simple surface singularity of type A1 and vice versa.


### NOTE TO MYSELF: Continue editing here.
## Usage

To use `ClassSing`, simply copy the content of classsing.txt into an open MAGMA session. Once the function is defined, you can use it as follows:

1. Fix the basefield to be the field of rational numbers.

    `QQ:=Rationals();`

2. If some of the singular-point coordinates of the given curve contain irrational numbers, adjoin these irrationalities to the basefield. For example, if a:=sqrt(5) is such an irrationality, you can adjoin it to the basefield via

    `F<a>:=ext<QQ|[Polynomial([-5,0,1])]>;`

3. Define the basering. Notice that the variables have to have the names x, y, and z.

    `K<x,y,z>:=PolynomialRing(F,3);`

4. Enter the defining polynomial of the projective curve. Example:

    `f:=(-y*(4*z*(z+y)-x*y))*(y^2*(x-4*z)+z*x*(z-2*y));`

5. Call the ClassSing function.

    `ClassSing(K,f);`

## License

`ClassSing`is released under the [GNU General Public License 3](http://www.gnu.org/licenses/gpl-3.0.html).

## Authors

Marco Besier, Dino Festi
