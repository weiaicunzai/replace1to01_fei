# Avoid	More	Than	Two	Expressions	in	List Comprehensions

* listcom support multiple levels of loops and multiple conditions per loop level

```
my_lists = [
    [[1, 2, 3], [4, 5, 6]],
    # ...
]

flat = [x for sublist1 in my_lists
        for	sublist2 in sublist1
        for	x	in	sublist2]
```

```
a	=	[1,	2,	3,	4,	5,	6,	7,	8,	9,	10]
b	=	[x	for	x	in	a	if	x	>	4	if	x	%	2	==	0]
c	=	[x	for	x	in	a	if	x	>	4	and	x	%	2	==	0]
```

* Do not use more than two expressions in listcomp: this could be one loop one condition, two condition, two loops


Yes:
```
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

squared	= [[x**2 for x in row] for row in matrix]

flat = [x for row in matrix	for	x in row]
```

```
a = range(10)
b = [x for x in a if a > 3]
```

No:
```
a = range(10)
b = [x for x in a if a > 3 and x < 5]
```

```
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
filtered = [[x	for	x in row if	x % 3 == 0]
    for	row	in	matrix	if	sum(row) >=	10]
```