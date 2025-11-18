# Mills constant
1,665,460 Digits of the mills constant.
The computation is under the assumption that the Riemann hypothesis is true.
Please reference original repository here, https://github.com/ZabeMath/mills-constant

# Jupyter Notebook

A Jupyter notebook is included in the `notebooks` directory which can reproduce both the original 555,153 digits of the Mills constant and the provided 1,665,460 digits. In the directory, there are also 2 text files, `A_14.txt` and `A_13.txt`, that are the direct outputs of the notebook and represent the Mills constants computed with the 13th Mills PRP and 14th Mills PRP. They can be considered duplicates.

# Mills Primes Table

A table in the `notebooks` directory names `mills-primes.csv` is provided. The table is in Comma Seperated Value (CSV) format with columns _n_ and _prime_ that represent the _nth prime_ in the Mills prime sequence when 3 is the exponent utilized. To open the table in Python, we can use this code,

```
import pandas as pd
df = pd.read_csv('mills-primes.csv')

# Retrieve n = 15 prime
n = 15
prime = df[df["n"] == n]["prime"].iloc[0]
prime = int(prime) # convert it to an integer
```

# Numerical Computation

This repository utilizes `mpmath` for numerical computation such that arbitrary precision is achieved. This covers very large numbers, in the case of generating Mills' primes, and very small numbers, in the case of the floating point numbers in Mills' constant. Significant performance improvements are found by utilizing `gmpy2` and more details can be found [here](https://mpmath.readthedocs.io/en/1.3.0/setup.html#using-gmpy-optional).

An edge case of catastrophic cancellation occurs while computing the Mills' constant. When finding the _nth root_ of the prime, there is a consecutive number of 0's for floating point values when dealing with arbitrarily large precision. The internal representation is in binary for `mpmath` and when we perform a base 10 (decimal) representation, it decreases the ones place by 1 with trailing 9's in the tenths, hundredths, and so on. During the verification, this is adjusted based on `mpmath` [documentation](https://mpmath.readthedocs.io/en/1.3.0/technical.html#decimal-issues).

# References
_In no particular order,_

- https://github.com/ZabeMath/mills-constant
- https://github.com/s-batalov/Mills_Primes
- https://cs.uwaterloo.ca/journals/JIS/VOL8/Caldwell/caldwell78.pdf
- https://oeis.org/A108739
- https://mpmath.readthedocs.io/en/1.3.0/index.html
- https://mpmath.readthedocs.io/en/1.3.0/functions/powers.html#root
- https://cs.uwaterloo.ca/journals/JIS/VOL8/Caldwell/caldwell78.pdf
- https://www.youtube.com/watch?v=6ltrPVPEwfo
- https://en.wikipedia.org/wiki/Mills'_constant
- https://mpmath.readthedocs.io/en/1.3.0/setup.html#using-gmpy-optional

_No generative AI was utilized to create this work._
