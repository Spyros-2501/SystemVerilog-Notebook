# IEEE 1800-2023

## §6.18 User-defined types

```SV
typedef int intP;
```

## §6.19 Enumerations

```SV
// c is automatically assigned the increment-value of 8
enum {a=3, b=7, c} alphabet;

// a=0, b=7, c=8
enum {a, b=7, c} alphabet;

// Correct declaration - bronze and gold are unsized
enum bit [3:0] {bronze='h3, silver, gold='h5} medal2;
```

## §6.21 Scope and lifetime

> Tasks and functions may be declared as **automatic**. Variables ... are initialized on each entry to the call or block

> Specific variables ... can be explicitly declared as **static**.

## §7.4.2 Unpacked arrays

> `[size]` shall mean the same as `[0:size-1]`

```SV
int Array[0:7][0:31];	// array declaration using ranges
int Array  [8]  [32];	// array declaration using sizes
```

## §9.4.2.1 Event OR operator

> Comma-separated sensitivity lists shall be synonymous to `or`-separated sensitivity lists.

```SV
always @(a or b, c, d or e)
```

## §12.5.3 `unique`-case, `unique0`-case, and `priority`-case

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

## §13. Tasks and functions (subroutines)

> Tasks and functions are collectively referred to as *subroutines*.

## §13.3 Tasks

> A call to a task is also referred to as a *task enable*

## §13.4 Functions

> The primary purpose of a function is to return a value that is to be used in an expression.

## §13.5.1 Pass by value

## §13.5.2 Pass by reference

```SV
function automatic int crc (ref byte packet [1000:1]);
	for(int j= 1; j <= 1000; j++) begin
		crc ^= packet[j];
	end
endfunction
```

## §20.8.1 Integer math functions

> The system function `$clog2` shall return the ceiling of the log base 2 of the argument

```SV
$clog2(n)
```

## §20.8.2 Real math functions

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

## §20.10 Severity system tasks

### `$fatal`

> The *finish_number* may be used in an implementation-specific manner.

```SV
$fatal [ ( finish_number [, list_of_arguments ] ) ] ;
finish_number ::= 0 | 1 | 2
```

## §23.3.2 Module instantiation syntax

> One or more module **instances** (identical copies of a module) can be specified in a single module instantiation statement.

```SV
ffnand
	ff1 (.q(),     .qbar(out1), .clear(in1), .preset(in2)), 
	ff2 (.q(),     .qbar(out2), .clear(in2), .preset(in1), .q()); 
	ff3 (.q(out3), .qbar(),     .clear(in1), .preset(in2));
```

----------------------------------------------------------------------

# Coding Styles
* code: [lowRISC](https://github.com/lowRISC/style-guides/blob/master/VerilogCodingStyle.md) (github)
* verification: [lowRISC](https://github.com/lowRISC/style-guides/blob/master/DVCodingStyle.md) (github)

# Personal reminders

```SV
begin: block_a
	...
end: block_a
```