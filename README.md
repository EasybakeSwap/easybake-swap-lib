# EasyBake Swap Library
Solidity libraries that are shared across EasyBake swap contracts. These libraries are focused on safety and gas efficiency.

## Install

Run `yarn` to install dependencies.

## Test

Run `yarn test` to execute the test suite.

## Usage

Install this in another project via `yarn add easybake-swap-lib` 

Then import the contracts via:

```solidity
import "@easybakeswap/easybake-swap-lib/contracts/access/Ownable.sol"; 
```

## Test Results v1.0.0
```
  AddressStringUtil
    #toAsciiString
      ✓ zero address (96ms)
      ✓ own address (105ms)
      ✓ random address (91ms)
      ✓ reverts if len % 2 != 0
      ✓ reverts if len >= 40
      ✓ reverts if len == 0
      ✓ produces len characters (121ms)

  Babylonian
    #sqrt
      ✓ works for 0-99 (1287ms)
      ✓ product of numbers close to max uint112 (78ms)
      ✓ max uint256
      ✓ gas cost
      ✓ gas cost of large number
      ✓ gas cost of max uint

  BitMath
    #mostSignificantBit
      ✓ 0
      ✓ 1
      ✓ 2
      ✓ all powers of 2 (2166ms)
      ✓ type(uint256).max
      ✓ gas cost of smaller number
      ✓ gas cost of max uint128
      ✓ gas cost of max uint256
    #leastSignificantBit
      ✓ 0
      ✓ 1
      ✓ 2
      ✓ all powers of 2 (1931ms)
      ✓ type(uint256).max
      ✓ gas cost of smaller number
      ✓ gas cost of max uint128
      ✓ gas cost of max uint256

  FixedPoint
    #encode
      ✓ shifts left by 112
      ✓ will not take >uint112(-1)
    #encode144
      ✓ shifts left by 112
      ✓ will not take >type(uint144).max
    #decode
      ✓ shifts right by 112
      ✓ will not take >uint224(-1)
    #decode144
      ✓ shifts right by 112
      ✓ will not take >type(uint256).max
    #mul
      ✓ works for 0
      ✓ correct multiplication
      ✓ overflow
      ✓ max of q112x112
      ✓ max without overflow, largest fixed point
      ✓ max without overflow, smallest fixed point
    #muli
      ✓ works for 0
      ✓ works for 3*2
      ✓ works for 3*-2
      ✓ max without overflow, largest int (42ms)
      ✓ max without overflow, largest fixed point (51ms)
    #muluq
      ✓ works for 0
      ✓ multiplies 3*2
      ✓ multiplies 4/3*4/3
      ✓ overflow upper
      ✓ gas for short circuit where one multiplicand is 0
      ✓ gas
    #divuq
      ✓ works for 0 numerator
      ✓ throws for 0 denominator
      ✓ equality 30/30
      ✓ divides 30/10
      ✓ divides 35/8
      ✓ divides 1/3
      ✓ divides 1e15/3e15 (long division, repeating)
      ✓ boundary of full precision
      ✓ precision
      ✓ gas cost of dividend = divisor short circuit
      ✓ divuq overflow with smaller numbers
      ✓ divuq overflow with large numbers
      ✓ gas cost of full precision small dividend short circuit
      ✓ gas cost of long division with less than 112 iterations
      ✓ gas cost of long division with all iterations
    #fraction
      ✓ correct computation less than 1
      ✓ correct computation greater than 1
      ✓ fails with 0 denominator
      ✓ can be called with numerator exceeding uint112 max
      ✓ can be called with denominator exceeding uint112 max
      ✓ can be called with numerator exceeding uint144 max
      ✓ can be called with numerator and denominator exceeding uint112 max
      ✓ short circuits for 0
      ✓ can overflow if result of division does not fit
      ✓ gas cost of 0
      ✓ gas cost of smaller numbers
      ✓ gas cost of number greater than Q112 numbers
      ✓ gas cost of number greater than Q112 numbers
    #reciprocal
      ✓ fails for 0
      ✓ fails for 1
      ✓ works for 0.25
      ✓ works for 5
    #sqrt
      ✓ works with 0
      ✓ works with numbers less than 1
      ✓ gas cost of less than 1
      ✓ works for 25
      ✓ gas cost of 25
      ✓ works for max uint144
      ✓ gas cost of max uint144
      ✓ works for 2**144
      ✓ gas cost of 2**144
      ✓ works for encoded max uint112
      ✓ gas cost of encoded max uint112
      ✓ works for max uint224
      ✓ gas cost of max uint224

  FullMath
    #mulDiv
      ✓ accurate without phantom overflow
      ✓ accurate with phantom overflow
      ✓ accurate with phantom overflow and repeating decimal

  PairNamer
    #pairName
      ✓ concatenation (95ms)
    #pairSymbol
      ✓ concatenation (88ms)

  SafeERC20Namer
    #tokenName
      ✓ works with compliant (46ms)
      ✓ works with noncompliant (48ms)
      ✓ works with empty bytes32 (53ms)
      ✓ works with noncompliant full bytes32 (54ms)
      ✓ works with optional (43ms)
      ✓ works with non-code address
      ✓ works with really long strings (66ms)
      ✓ falls back to address with empty strings (52ms)
    #tokenSymbol
      ✓ works with compliant (48ms)
      ✓ works with noncompliant (49ms)
      ✓ works with empty bytes32 (45ms)
      ✓ works with noncompliant full bytes32 (52ms)
      ✓ works with optional (38ms)
      ✓ works with non-code address
      ✓ works with really long strings (65ms)
      ✓ falls back to address with empty strings (47ms)

  SafeMathTest
    #sqrt
      ✓ works for 0-99 (998ms)
      ✓ max uint256

  TransferHelper
    #safeApprove
      ✓ succeeds with compliant with no revert and true return (83ms)
      ✓ fails with compliant with no revert and false return (53ms)
      ✓ fails with compliant with revert (62ms)
      ✓ succeeds with noncompliant (no return) with no revert (127ms)
      ✓ fails with noncompliant (no return) with revert (56ms)
    #safeTransfer
      ✓ succeeds with compliant with no revert and true return (81ms)
      ✓ fails with compliant with no revert and false return (56ms)
      ✓ fails with compliant with revert (53ms)
      ✓ succeeds with noncompliant (no return) with no revert (84ms)
      ✓ fails with noncompliant (no return) with revert (59ms)
    #safeTransferFrom
      ✓ succeeds with compliant with no revert and true return (81ms)
      ✓ fails with compliant with no revert and false return (55ms)
      ✓ fails with compliant with revert (56ms)
      ✓ succeeds with noncompliant (no return) with no revert (89ms)
      ✓ fails with noncompliant (no return) with revert (54ms)
    #safeTransferETH
      ✓ succeeds call not reverted (128ms)
      ✓ fails if call reverts (54ms)


  139 passing (11s)

✨  Done in 21.25s.
```