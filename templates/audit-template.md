# Deflationary ShitMoon Token Audit - 2021/02/02

## Requested by Name

```c
   Disclaimer:
   <TODO: Add disclaimer>
```

| Destruction Level | Contract  | Lines                 |
| ----------------- | --------- | --------------------- |
| High              | ERC20.sol | 1,23 -> 40 ; 21 -> 23 |

| Contracts | Explorer Link | Github     |
| --------- | ------------- | ---------- |
| ERC20     | etherscan.com | github.com |

## Protocol Description

Does transfers bla bla bla bla template, beep boop , pickle rick

## IERC20.sol

[OpenZeppeling Standard ERC20 Interface](https://raw.githubusercontent.com/OpenZeppelin/openzeppelin-contracts/master/contracts/interfaces/IERC20.sol)

## ERC20.sol

| Function Name | Type | Modifiers | Return type | Vulnerable |
| ------------- | ---- | --------- | ----------- | ---------- |
| balanceOf     | view | none      | uint256     | False      |