# IEEE 1800-2023

#### §9.4.2.1 — Comma-separated sensitivity lists shall be synonymous to or-separated sensitivity lists.

```SV
always @(a or b, c, d or e)
```

#### §20.8.1 — Integer math functions

> The system function `$clog2` shall return the ceiling of the log base 2 of the argument

```SV
$clog2(n)
```

#### §20.8.2 — Real math functions

```SV
$ln(x)
$log10(x)
$exp(x)
$sqrt(x)
$pow(x,y)
$floor(x)
$ceil(x)
$sin(x)
$cos(x)
$tan(x)
$asin(x)
$acos(x)
$atan(x)
$atan2(y,x)
$hypot(x,y)
$sinh(x)
$cosh(x)
$tanh(x)
$asinh(x)
$acosh(x)
$atanh(x)
```

#### §7.4.2 — [size] shall mean the same as [0:size-1]

```SV
int Array[0:7][0:31];	// array declaration using ranges
int Array  [8]  [32];	// array declaration using sizes
```

# Coding Styles
* code: [lowRISC](https://github.com/lowRISC/style-guides/blob/master/VerilogCodingStyle.md) (github)
* verification: [lowRISC](https://github.com/lowRISC/style-guides/blob/master/DVCodingStyle.md) (github)