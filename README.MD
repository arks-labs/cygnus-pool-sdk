# Cygnus Pool SDK

## ubtc Pool
### Contract Address
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-uBTC    | 0xf410A0d866831fbA8056abbc05a53B90757f58B1 |
| RestakingVault | 0x7551aEa51588AaCe99B89c3FaC3CFc4108DB8094 |
| uBTC           | 0x796e4D53067FF374B89b2Ac101ce0c1f72ccaAc2 |

## unibtc Pool
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-uniBTC  | 0xA558f245c93f5f7eC99E239d7Aab247985D429fD |
| RestakingVault | 0xBc323bA4bbf2559417C3Ca47A75e2Ea341Cf8320 |
| uniBTC         | 0x93919784C523f39CACaa98Ee0a9d96c3F32b593e |


## stBTC Pool
### Contract Address
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-stBTC   | 0x80E3c92119DAC35b4E56346C3149D88c5D54C472 |
| RestakingVault | 0x0Ce45dd53affbb011884EF1866E0738f58AB7969 |
| stBTC          | 0xf6718b2701d4a6498ef77d7c152b2137ab28b8a3 |


### Interact with RestakingVault
RestakingVault:`0x0Ce45dd53affbb011884EF1866E0738f58AB7969` is the contract that manages the stBTC pool. You can interact with the pool by calling the following functions.
### Deposit
deposit stBTC to the pool and get the same amount of Cygnus-stBTC back.

**ABI:**

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
  }
```

- `amount`: the amount of stBTC to be deposited, integer with stBTC's decimals.


### Request withdrawal
Make an order to withdraw Cygnus-stBTC from the pool to get stBTC. 
*(To withdraw stBTC from the pool, you need to make an request first. And you shall be able to claim it after 2~7 days.)*

**ABI:**
```javascript
{
  inputs: [
    {
      internalType: 'uint256',
      name: 'amount',
      type: 'uint256',
    },
  ],
  name: 'requestWithdraw',
  outputs: [],
  stateMutability: 'nonpayable',
  type: 'function',
}
```

- `amount`: the amount of Cygnus-stBTC to be withdrawn, integer with stBTC's decimals.

#### Get withdrawal orders
You can check your withdrawal orders by calling the `getOrdersByOwner` function.

**ABI:**

```javascript
{
  inputs: [
    {
      internalType: 'address',
      name: 'owner', // your wallet address
      type: 'address',
    },
  ],
  name: 'getOrdersByOwner',
  outputs: [
    {
      components: [
        {
          internalType: 'uint256',
          name: 'index', // the unique index of this order
          type: 'uint256',
        },
        {
          internalType: 'uint256',
          name: 'amount', // the amount of stBTC to be withdrawn in this order
          type: 'uint256',
        },
        {
          internalType: 'address',
          name: 'owner', // user wallet address of this order
          type: 'address',
        },
        {
          internalType: 'bool',
          name: 'used', // whether this order has been claimed or not
          type: 'bool',
        },
      ],
      internalType: 'struct CygnusRestakingVault.WithdrawOrder[]',
      name: '',
      type: 'tuple[]',
    },
  ],
  stateMutability: 'view',
  type: 'function',
}
```

### Claim
Claim stBTC from the pool after your withdrawal order has been processed. Orders with index less than or equal to the max claimable index ( `maxWithdrawIndex`) can be claimed.

**ABI:**

```javascript
{
  inputs: [
    {
      internalType: 'uint256[]',
      name: 'indexs',
      type: 'uint256[]',
    },
  ],
  name: 'claim',
  outputs: [],
  stateMutability: 'nonpayable',
  type: 'function',
}
```

- `indexs`: array of the indexes of your withdrawal orders, you can claim multiple orders at once.

#### Check current max claimable index
You can check the current max claimable index by calling the `maxWithdrawIndex` function. Orders with index less than or equal to this value can be claimed.

**ABI:**

```javascript
{
  inputs: [],
  name: 'maxWithdrawIndex',
  outputs: [
    {
      internalType: 'uint256',
      name: '',
      type: 'uint256',
    },
  ],
  stateMutability: 'view',
  type: 'function',
}
```