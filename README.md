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
space. The `NonADE` function fills this gap.

## How it Works

The `NonADE` makes use of the fact that

1. the singularities of a double cover of the projective plane are in one-to-one
   correspondence with the singularities of its branch curve.

2. if _p_ is a singularity of the double cover and _q_ is the corresponding
   singularity of the branch locus, then _p_ and _q_ have the same singularity
   type. For example, if _q_ is a simple curve singularity of type _A1_, then
   _p_ is a simple surface singularity of type _A1_ and vice versa.

`NonADE` works as follows: First, the user provides the defining polynomial
_F(x,y,z)_ of the projective curve _B_ that defines the branch locus
\{ _B_ = 0 \} of the double cover.
Given that (by 1.) all singularities of the double cover are in one-to-one
correspondence with the singularities of _B_ and given that (by 2.) simple
singularities of _B_ do not change their type under the double cover
involution, it suffices to study the singularities of _B_ in order to study the
singularities of the double cover.

Unfortunately, [MAGMA](http://magma.maths.usyd.edu.au/magma/) does not have a
function to check whether or not a given projective curve has only simple
singularities. There is, however, a function that performs this task for affine
and projective surfaces, called
`IsSimpleSurfaceSingularity`.
While this function can not be applied to hypersurfaces in weighted projective
space, we _can_ use it on affine surfaces. Notice that

1. to study the singularities of _B_, we can study the singularities of each
   of its three affine charts.

2. each affine chart of _B_ corresponds to a double cover of the affine plane
   branched above the respective affine chart of _B_. Each of these double
   covers can be viewed as a hypersurface in the affine 3-space.

3. We can use `IsSimpleSurfaceSingularity` to study the singularities of each
   of these three affine surfaces.

4. By the above comments, each simple singularity of one of these three surfaces
   corresponds to a simple curve singularity of an affine chart of _B_. The
   singularities of the affine charts of _B_, make up all singularities of _B_.
   The singularities of _B_, make up all singularities of the double cover.

In other words, we can simply study the singularities of each of the three
affine surfaces mentioned above using `IsSimpleSurfaceSingularity`, and
formulate our result in terms of singularities of the original double cover
associated to our square root.

## Usage

For a detailed discussion of how to use `NonADE`, have a look at the Usage.pdf
file, which is contained in this repository.

## License

`NonADE`is released under the
[GNU General Public License 3](http://www.gnu.org/licenses/gpl-3.0.html).

## Authors

Marco Besier, Dino Festi
