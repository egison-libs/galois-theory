# Galois Theory in Egison

## Usage

```
% egison -l lib/math/algebra/symmetric-group.egi
> s3
[[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
> cyclicSubgroups s3
[[[1, 2, 3]], [[1, 3, 2], [1, 2, 3]], [[2, 1, 3], [1, 2, 3]], [[2, 3, 1], [3, 1, 2], [1, 2, 3]], [[3, 2, 1], [1, 2, 3]]]
> isNormalSubgroup [[1, 2, 3]] s3
True
> isNormalSubgroup [[1, 3, 2], [1, 2, 3]] s3
False
> isNormalSubgroup [[2, 3, 1], [3, 1, 2], [1, 2, 3]] s3
True
> commutatorSubgroup s3
[[1, 2, 3], [2, 3, 1], [3, 1, 2]]
> commutatorSubgroup (commutatorSubgroup s3)
[[1, 2, 3]]
```

## Function List

### `G.id`

```
> G.id 3
[1, 2, 3]
> G.id 4
[1, 2, 3, 4]
```

### `G.*`

```
> G.* [1, 2, 3] [2, 3, 1]
[2, 3, 1]
> G.* [2, 3, 1] [3, 1, 2]
[1, 2, 3]
> G.* [3, 1, 2] [2, 3, 1]
[1, 2, 3]
```

### `G.reverse`

```
> G.reverse [2, 1, 3, 4]
[2, 1, 3, 4]
> G.reverse [4, 1, 2, 3]
[2, 3, 4, 1]
```

### `G.toCycles`

```
> G.toCycles [3, 1, 2, 4]
[[1, 3, 2]]
> G.toCycles [2, 1, 4, 3]
[[1, 2], [3, 4]]
```

### `symmetricGroup`

```
> symmetricGroup 3
[[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]]
> symmetricGroup 4
[[1, 2, 3, 4], [1, 2, 4, 3], [1, 3, 2, 4], [2, 1, 3, 4], [1, 3, 4, 2], [1, 4, 2, 3], [2, 1, 4, 3], [2, 3, 1, 4], [3, 1, 2, 4], [1, 4, 3, 2], [2, 3, 4, 1], [2, 4, 1, 3], [3, 1, 4, 2], [3, 2, 1, 4], [4, 1, 2, 3], [2, 4, 3, 1], [3, 2, 4, 1], [3, 4, 1, 2], [4, 1, 3, 2], [4, 2, 1, 3], [3, 4, 2, 1], [4, 2, 3, 1], [4, 3, 1, 2], [4, 3, 2, 1]]
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
[[1, 2, 3, 4], [4, 3, 2, 1], [2, 1, 4, 3], [3, 4, 1, 2]]
```

### `isNormalSubgroup`

```
> isNormalSubgroup a3 s3
True
> isNormalSubgroup [[2, 1, 3], [1, 2, 3]] s3
False
> isNormalSubgroup a4 v4
True
```

### `genCyclicGroup`

```
> genCyclicGroup [2, 1, 3]
[[2, 1, 3], [1, 2, 3]]
> genCyclicGroup [2, 3, 1]
[[2, 3, 1], [3, 1, 2], [1, 2, 3]]
```

### `cyclicSubgroups`

```
> cyclicSubgroups s3
[[[1, 2, 3]],
 [[1, 3, 2], [1, 2, 3]],
 [[2, 1, 3], [1, 2, 3]],
 [[2, 3, 1], [3, 1, 2], [1, 2, 3]],
 [[3, 2, 1], [1, 2, 3]]]
```

### `generators`

```
> map G.toCycles (generators s4)
[[],
 [[3, 4]],
 [[2, 3]],
 [[1, 2]],
 [[2, 3, 4]],
 [[1, 2], [3, 4]],
 [[1, 2, 3]],
 [[2, 4]],
 [[1, 2, 3, 4]],
 [[1, 2, 4, 3]],
 [[1, 3]],
 [[1, 2, 4]],
 [[1, 3, 4]],
 [[1, 3], [2, 4]],
 [[1, 3, 2, 4]],
 [[1, 4]],
 [[1, 4], [2, 3]]]
```

### `genGroup`

```
> genGroup [[1, 3, 4, 2], [2, 1, 4, 3]]
[[3, 1, 2, 4], [1, 3, 4, 2], [4, 1, 3, 2], [1, 4, 2, 3], [2, 1, 4, 3], [1, 2, 3, 4], [2, 3, 1, 4], [3, 2, 4, 1], [4, 3, 2, 1], [3, 4, 1, 2], [2, 4, 3, 1], [4, 2, 1, 3]]
```

### `G.product`

```
> G.product v4 [[2, 3, 1, 4], [1, 4, 2, 3], [4, 1, 3, 2], [3, 2, 4, 1]]
[[2, 3, 1, 4], [1, 4, 2, 3], [3, 2, 4, 1], [4, 1, 3, 2]]
```

### `G.**`

```
> G.** v4  [[1, 3, 4, 2], [1, 4, 2, 3], [1, 2, 3, 4]]
[[1, 3, 4, 2], [1, 4, 2, 3], [4, 2, 1, 3], [1, 2, 3, 4], [4, 1, 3, 2], [2, 4, 3, 1], [4, 3, 2, 1], [2, 3, 1, 4], [3, 1, 2, 4], [2, 1, 4, 3], [3, 2, 4, 1], [3, 4, 1, 2]]
-- error
```

### `G.//`

```

> G.// a4 v4
[[1, 3, 4, 2], [1, 4, 2, 3], [1, 2, 3, 4]]
```

### `commutator`

```
> commutator [3, 1, 2, 4] [2, 3, 1, 4]
[1, 2, 3, 4]
> commutator [3, 1, 2, 4] [4, 1, 2, 3]
[1, 4, 2, 3]
```

### `commutatorSubgroup`

```
> commutatorSubgroup s3
[[1, 2, 3], [2, 3, 1], [3, 1, 2]]
```

### `isAbelianGroup`

```
> isAbelianGroup (genCyclicGroup [4, 1, 2, 3])
True
> isAbelianGroup s4
False
```

### `isPerfectGroup`

```
> isPerfectGroup a4
False
> isPerfectGroup a5
True
```

## LICENSE

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
