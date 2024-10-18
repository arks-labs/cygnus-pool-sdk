# Cygnus Pool SDK

## stBTC Pool
### Contract Address
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-stBTC   | 0x80E3c92119DAC35b4E56346C3149D88c5D54C472 |
| RestakingVault | 0x0Ce45dd53affbb011884EF1866E0738f58AB7969 |

### Deposit
deposit stBTC to the pool and get the same amount of Cygnus-stBTC back.
### Contract
RestakingVault: `0x0Ce45dd53affbb011884EF1866E0738f58AB7969`
### ABI
```javascript
  {
    inputs: [
      {
        internalType: 'uint256',
        name: 'amount',
        type: 'uint256',
      },
    ],
    name: 'deposit',
    outputs: [],
    stateMutability: 'nonpayable',
    type: 'function',
  },
```

`amount` is your deposit amount with stBTC's decimals.


### Withdraw