# Sort

Method    | Best  | Worst       | Stable | Memory
----------|-------|-------------|--------|---------
bubble    | N     | N^2         | T      | 1
selection | N^2   | N^2         | F      | 1
insertion | N     | N^2         | T      | 1
shell     | NlogN | Nlog2N      | F      | 1
merge     | NlogN | NlogN       | T      | N
quick     | NlogN | NlogN ~ N^2 | F      | logN ~ N

## Bubble

이웃한 두 값을 비교하여 정렬.

## Selection

최대/최소 값을 골라내어 정렬.
