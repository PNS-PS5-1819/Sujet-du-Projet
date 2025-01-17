# Metrics associated to the dataset


## Execution time

These execution time are just _one shot_ execution of the _APB_ and _StudentFirst Algorithm, on a Mac Book Pro (3,1 GHz Intel Core i7, 16GB or RAM). **This is not a benchmark**.


| Dataset Size | APB (Exec time, s) | StudentFirst (Exec Time, s) |
|:------------:|:---------------:| :-----------------------:|
| 10  | 0.082 | 0.083 |
| 100  | 0.089 | 0.095 |
| 1,000  | 0.130 | 0.140 |
| 10,000  | 0.374 | 0.347 |
| 100,000 | 3.661 | 2.647 |
| 1,000,000  | 73.826 | 44.245 |


## Distance to stability

| Dataset Size | APB | StudentFirst  |
|:------------:|:---------------:| :-----------------------:|
| 10  | 0 | 2 |
| 100  | 0 | 24 |
| 1,000  | 0 | 296 |
| 10,000  | 0 | 3,411 |
| 100,000 | 0 | 34,147 |
| 1,000,000  | 0 | 34,1850 |


## Satisfaction (Student)

| Dataset Size | APB | StudentFirst  |
|:------------:|:---------------:| :-----------------------:|
| 10  | 1.30 | 1.30 |
| 100  | 1.79 | 1.62 |
| 1,000  | 2.57 | 2.08 |
| 10,000  | 4.12 | 3.52 |
| 100,000 | 4.68 | 3.84  |
| 1,000,000 | 4.79 | 3.94  |

## Satisfaction (Schools)

| Dataset Size | APB | StudentFirst  |
|:------------:|:---------------:| :-----------------------:|
| 10  | 2.30 | 2.22 |
| 100  | 22.57 | 24.12 |
| 1,000  | 168.85 | 184.92 |
| 10,000  | 1,171.65 | 1,274.01 |
| 100,000 | 8,054.45 | 9,154.07 |
| 1,000,000  | 84,012.71 | 92,713.02 |

## Instability (#couples)

| Dataset Size | APB | StudentFirst  |
|:------------:|:---------------:| :-----------------------:|
| 10  | 0 | 0 |
| 100  | 0 | 15 |
| 1,000  | 0 | 316 |
| 10,000  | 0 | 8,400 |
| 100,000 | 0 | 76,793 |
| 1,000,000  | 0 | 757,626 |

## Instability (#Students)

| Dataset Size | APB | StudentFirst  |
|:------------:|:---------------:| :-----------------------:|
| 10  | 0 | 0 |
| 100  | 0 | 4 |
| 1,000  | 0 | 126 |
| 10,000  | 0 | 2,196 |
| 100,000 | 0 | 13,323 |
| 1,000,000  | 0 | 119,964 |


## Excluded students (X)

| Dataset Size | APB | StudentFirst  |
|:------------:|:---------------:| :-----------------------:|
| 10  | 0 | 1 |
| 100  | 1 | 1 |
| 1,000  | 23 | 32 |
| 10,000  | 436 | 494 |
| 100,000 | 8,284 | 8,797 |
| 1,000,000  | 41,115 | 67,545 |

## Raw data

### _Admission PostBac_


#### Sample size: 10

##### Satisfaction

```
0  1  2  X
8  1  1  0
1.30
2.30
```

##### Stability

```
0
0
```

#### Sample size: 100

##### Satisfaction

```
0   1   2   3   4   5   6   X
70  12   6   2   3   6   0   1
1.79
22.57
```

##### Stability

```
0
0
```

#### Sample size: 1,000

##### Satisfaction

```
0    1    2    3    4    5    6    7    8    9    X
587  134   61   36   17   38   53   21   21    9   23
2.57
168.85
```

##### Stability

```
0
0
```

#### Sample size: 10,000

##### Satisfaction

```
0     1     2     3     4     5     6     7     8     9    10    11    12    13     X
5081   958   368   330   384   364   206   276   316   319   429   229   250    54   436
4.12
1171.65
```

##### Stability

```
0
0
```

#### Sample size: 100,000

##### Satisfaction

```
0      1      2      3      4      5      6      7      8      9     10     11     12     13     14     15     16      X
54453   9148   5043   3273   2279   2308   1059    838   1219    519    529   1072   3542   2251   1717   1349   1117   8284
4.68
8054.45
```

##### Stability

```
0
0
```

#### Sample size: 1,000,000

##### Satisfaction

```
0       1       2       3       4       5       6       7       8       9      10      11      12      13      14      15      16      17      18      19      20      21      22      23       X
556515  107238   57173   37639   26350   19422   11009    6364   13130    7184   13009    4346    3601    3161    3043    8872    5737    6184   22080   18725    9586    5936    3257    9324   41115
4.79
84012.71
```

##### Stability

```
0
0
```

### Plan B (Student First)

#### Sample size: 10

##### Distance to `APB`

```
2
```

##### Satisfaction

```
0  1  2  X
9  0  0  1
1.30
2.22
```

##### Stability

```
0
0
```

#### Sample size: 100

##### Distance to `APB`

```
24
```

##### Satisfaction

```
0   1   2   3   4   5   6   X
78  12   0   0   3   5   1   1
1.62
24.12
```

##### Stability

```
15
4
```

#### Sample size: 1,000

##### Distance to `APB`

```
296
```

##### Satisfaction

```
0    1    2    3    4    5    6    7    8    9    X
718  105   27   29   17   35   10    3   23    1   32
2.08
184.92
```

##### Stability

```
316
126
```

#### Sample size: 10,000

##### Distance to `APB`

```
3411
```

##### Satisfaction

```
0     1     2     3     4     5     6     7     8     9    10    11    12    13     X
6606   541    95    58   329   406    44   180   278   369    76   159   323    42   494
3.52
1274.01
```

##### Stability

```
8400
2196
```

#### Sample size: 100,000

##### Distance to `APB`

```
34147
```

##### Satisfaction

```
0      1      2      3      4      5      6      7      8      9     10     11     12     13     14     15     16      X
70086   6729   1923    242   1488   2013    225     65   1430    133    231    215   1356   1595   1753   1408    311   8797
3.84
9154.07
```

##### Stability

```
76793
13323
```

#### Sample size: 1,000,000

##### Distance to `APB`

```
341850
```

##### Satisfaction

```
0       1       2       3       4       5       6       7       8       9      10      11      12      13      14      15      16      17      18      19      20      21      22      23       X
725796   60651   31721   26385   15796    6244    3291     811    1588    1315   12250    1598     470     392     576    6764    4212    1416    4370   10773    7731    4358    2311    1636   67545
3.94
92713.02
```

##### Stability

```
757626
119964
```

