# Cygnus Pool SDK

## stBTC Pool
### Deposit
deposit stBTC to the pool and get the same amount of Cygnus-stBTC back.
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