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

#### §20.10 — `$fatal` The finish_number may be used in an implementation-specific manner.

```SV
$fatal [ ( finish_number [, list_of_arguments ] ) ] ;
finish_number ::= 0 | 1 | 2
```

#### §12.5.3 — `unique`-case, `unique0`-case, and `priority`-case

> In **unique**-case and unique0-case, the case_expression shall be evaluated exactly once... Unique-case and unique0-case are violated if more than one case_item is found to match the case_expression. 

> If the case is qualified as **priority** or unique, the simulator shall issue a violation report if no case_item matches.

```SV
bit [2:0] a;

unique case(a) // values 3,5,6,7 cause a violation report
	0,1: $display("0 or 1");
	2  : $display("2");
	4  : $display("4");
endcase

priority casez(a) // values 4,5,6,7 cause a violation report
	3'b00?: $display("0 or 1");
	3'b0??: $display("2 or 3");
endcase

unique0 case(a) // values 3,5,6,7 do not cause a violation report
	0,1: $display("0 or 1");
	2  : $display("2");
	4  : $display("4");
endcase
```

---

# Coding Styles
* code: [lowRISC](https://github.com/lowRISC/style-guides/blob/master/VerilogCodingStyle.md) (github)
* verification: [lowRISC](https://github.com/lowRISC/style-guides/blob/master/DVCodingStyle.md) (github)

# Personal reminders

```SV
begin: block_a
	...
end: block_a
```