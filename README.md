# Galois Theory in Egison

## Usage

```
% egison -l lib/math/symmetric-group.egi
> s3
{{1 2 3} {1 3 2} {2 1 3} {2 3 1} {3 1 2} {3 2 1}}
> (cyclic-subgroups s3)
{{{1 2 3}}
 {{1 3 2} {1 2 3}}
 {{2 1 3} {1 2 3}}
 {{2 3 1} {3 1 2} {1 2 3}}
 {{3 2 1} {1 2 3}}}
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
```

## Function List

### `G.id`

```
> (G.id 3)
{1 2 3}
> (G.id 4)
{1 2 3 4}
```

### `G.*`

```
> (G.* {1 2 3} {3 1 2})
{3 1 2}
> (G.* {2 1 3} {3 1 2})
{3 2 1}
> (G.* {3 1 2} {2 1 3})
{1 3 2}
```

### `G.reverse`

```
> (G.reverse {2 1 3 4})
{2 1 3 4}
> (G.reverse {4 1 2 3})
{2 3 4 1}
```

### `G.to-cycles`

```
> (G.to-cycles {3 1 2 4})
{{1 3 2}}
> (G.to-cycles {2 1 4 3})
{{1 2} {3 4}}
```

### `symmetric-group`

```
> (symmetric-group 3)
{{1 2 3} {1 3 2} {2 1 3} {2 3 1} {3 1 2} {3 2 1}}
> (symmetric-group 4)
{{1 2 3 4} {1 2 4 3} {1 3 2 4} {2 1 3 4} {1 3 4 2} {1 4 2 3} {2 1 4 3} {2 3 1 4}
 {3 1 2 4} {1 4 3 2} {2 3 4 1} {2 4 1 3} {3 1 4 2} {3 2 1 4} {4 1 2 3} {2 4 3 1}
 {3 2 4 1} {3 4 1 2} {4 1 3 2} {4 2 1 3} {3 4 2 1} {4 2 3 1} {4 3 1 2} {4 3 2 1}}
```

### `s3`, `s4`, `s5`

`s3` is the symmetric group with 3 symobols.

`s4` is the symmetric group with 4 symobols.

`s5` is the symmetric group with 5 symobols.

### `a3`, `a4`, `a5`

`a3` is the alternating group of `s3`.

`a4` is the alternating group of `s4`.

`a5` is the alternating group of `s5`.

### `v4`

`v4` is Klein four-group.

```
> v4
{{1 2 3 4} {2 1 4 3} {3 4 1 2} {4 3 2 1}}
```

### `normal-subgroup?`

```
> (normal-subgroup? a3 s3)
#t
> (normal-subgroup? {{2 1 3} {1 2 3}} s3)
#f
> (normal-subgroup? a4 v4)
#t
```

### `gen-cyclic-group`

```
> (gen-cyclic-group {2 1 3})
{{2 1 3} {1 2 3}}
> (gen-cyclic-group {2 3 1})
{{2 3 1} {3 1 2} {1 2 3}}
```

### `cyclic-subgroups`

```
> (cyclic-subgroups s3)
{{{1 2 3}}
 {{1 3 2} {1 2 3}}
 {{2 1 3} {1 2 3}}
 {{2 3 1} {3 1 2} {1 2 3}}
 {{3 2 1} {1 2 3}}}
```

### `generators`

```
> (map G.to-cycles (generators s4))
{{}
 {{3 4}}
 {{2 3}}
 {{1 2}}
 {{2 3 4}}
 {{1 2} {3 4}}
 {{1 2 3}}
 {{2 4}}
 {{1 2 3 4}}
 {{1 2 4 3}}
 {{1 3}}
 {{1 2 4}}
 {{1 3 4}}
 {{1 3} {2 4}}
 {{1 3 2 4}}
 {{1 4}}
 {{1 4} {2 3}}
```

### `gen-group`

```
> (gen-group {{1 3 4 2} {2 1 4 3}})
{{1 2 3 4} {1 3 4 2} {1 4 2 3} {2 1 4 3} {3 1 2 4} {4 1 3 2} {2 3 1 4} {2 4 3 1} {3 2 4 1} {3 4 1 2} {4 2 1 3} {4 3 2 1}}
```

### `G.product`

```
(G.product v4 {{2 3 1 4} {1 4 2 3} {4 1 3 2} {3 2 4 1}})
{{1 4 2 3} {2 3 1 4} {3 2 4 1} {4 1 3 2}}
```

### `G.**`

```
> (G.** v4  {{1 3 4 2} {1 4 2 3} {1 2 3 4}})
{{1 2 3 4} {1 3 4 2} {1 4 2 3} {2 1 4 3} {2 3 1 4} {2 4 3 1} {3 1 2 4} {3 2 4 1} {3 4 1 2} {4 1 3 2} {4 2 1 3} {4 3 2 1}}
```

### `G.//`

```
> (G.// a4 v4)
{{1 3 4 2} {1 4 2 3} {1 2 3 4}}
```

### `commutator`

```
> (commutator {3 1 2 4} {2 3 1 4})
{1 2 3 4}
> (commutator {3 1 2 4} {4 1 2 3})
{1 4 2 3}
```

### `commutator-subgroup`

```
> (commutator-subgroup s3)
{{1 2 3} {2 3 1} {3 1 2}}
```

### `abelian-group?`

```
> (abelian-group? (gen-cyclic-group {4 1 2 3}))
#t
> (abelian-group? s4)
#f
```

### `perfect-group?`

```
> (perfect-group? a4)
#f
> (perfect-group? a5)
#t
```

## LICENSE

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
