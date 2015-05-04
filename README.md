# Galois Theory in Egison

## Usage

```
% egison -l lib/math/symmetric-group.egi
> s3
{{1 2 3} {1 3 2} {2 1 3} {2 3 1} {3 1 2} {3 2 1}}
> (cyclic-subgroups s3)
{{{1 2 3}} {{1 3 2} {1 2 3}} {{2 1 3} {1 2 3}} {{2 3 1} {3 1 2} {1 2 3}} {{3 2 1} {1 2 3}}}
> (normal-subgroup? {{1 2 3}} s3)
#t
> (normal-subgroup? {{1 3 2} {1 2 3}} s3)
#f
> (normal-subgroup? {{2 3 1} {3 1 2} {1 2 3}} s3)
#t
> (commutator-subgroup s3)
{{1 2 3} {2 3 1} {3 1 2}}
> (commutator-subgroup {{1 2 3} {2 3 1} {3 1 2}})
{{1 2 3}}
> (commutator-subgroup s4)
{{1 2 3 4} {1 3 4 2} {1 4 2 3} {2 3 1 4} {3 1 2 4} {4 1 3 2} {2 4 3 1} {4 3 2 1} {3 2 4 1} {4 2 1 3} {3 4 1 2} {2 1 4 3}}
> (commutator-subgroup {{1 2 3 4} {1 3 4 2} {1 4 2 3} {2 3 1 4} {3 1 2 4} {4 1 3 2} {2 4 3 1} {4 3 2 1} {3 2 4 1} {4 2 1 3} {3 4 1 2} {2 1 4 3}})
{{1 2 3 4} {4 3 2 1} {3 4 1 2} {2 1 4 3}}
> (commutator-subgroup {{1 2 3 4} {4 3 2 1} {3 4 1 2} {2 1 4 3}})
{{1 2 3 4}}
```


## LICENSE

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.