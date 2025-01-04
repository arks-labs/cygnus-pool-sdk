# Cygnus Pool SDK


## Bitlayer Pool
## SolvBTC.m
| Name      | Address                                    |
| --------- | ------------------------------------------ |
| token     | 0x387e2a62b0f7fB75F36F1312EF8d6b60569674cA |
| vault     | 0xD4a90C85cd602aF645015FeE43354120D5eC4102 |
| solvBTC.m | 0xe04d21d999faedf1e72ade6629e20a11a1ed14fa |

## stBTC
| Name  | Address                                    |
| ----- | ------------------------------------------ |
| token | 0x4884521dc53f8D746Fdc6D8E1279c4B1EEE019b2 |
| vault | 0x971B1c1048aDBB63f23ef333215587623F292b57 |
| stBTC | 0xf6718b2701d4a6498ef77d7c152b2137ab28b8a3 |

## uniBTC
| Name   | Address                                    |
| ------ | ------------------------------------------ |
| token  | 0x0055dc86970Ce62E160bc5579A8D44f6EAc3CE17 |
| vault  | 0xf587B7116879a529353Cc71eE959cD69FD5CAE48 |
| uniBTC | 0x93919784c523f39cacaa98ee0a9d96c3f32b593e |

## BL BTC

| Name  | Address                                    |
| ----- | ------------------------------------------ |
| token | 0x62a92d143f4a496399f44555bb75b6ccba2bba3b |
| vault | 0x8d2757EA27AaBf172DA4CCa4e5474c76016e3dC5 |
| BLBTC | 0x4e0dd7c16d2bbf873335cc21c72663b3eae23014 |



### wBTC
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-wBTC    | 0xaA553f2E836CD0Fc9A33E7aC188d8B4fC1083395 |
| RestakingVault | 0x1792865D493FE4DFdD504010D3c0f6da11E8046D |
| wBTC           | 0xff204e2681a6fa0e2c3fade68a1b28fb90e4fc5f |


## Ethereum Pool
### cgETH.hashkey

| Name          | Address                                    |
| ------------- | ------------------------------------------ |
| token         | 0x91a26EF947077dFf7D30cdc251dAE57179B0484c |
| vault         | 0x1F113e7580909E84B08289Fe6eE93f3917eB1314 |
| cgETH.hashkey | 0xEf588D79DF77c34B9821C5c1FB2f3e5019fB9521 |

## BSquared Pool
### ubtc 
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-uBTC    | 0xf410A0d866831fbA8056abbc05a53B90757f58B1 |
| RestakingVault | 0x7551aEa51588AaCe99B89c3FaC3CFc4108DB8094 |
| uBTC           | 0x796e4D53067FF374B89b2Ac101ce0c1f72ccaAc2 |

### unibtc
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-uniBTC  | 0xA558f245c93f5f7eC99E239d7Aab247985D429fD |
| RestakingVault | 0xBc323bA4bbf2559417C3Ca47A75e2Ea341Cf8320 |
| uniBTC         | 0x93919784C523f39CACaa98Ee0a9d96c3F32b593e |


### uoBTC
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-uoBTC   | 0x6fc87e25C5C86E6b9FcFBA5dFf2F56964C36A1Ab |
| RestakingVault | 0xE7ae30C03395D66F30A26C49c91edAe151747911 |
| uoBTC          | 0xBFb4B5F54Ef69692Bb36963fA846e8855D73DBC0 |


###  stBTC
| Name           | Address                                    |
| -------------- | ------------------------------------------ |
| Cygnus-stBTC   | 0x80E3c92119DAC35b4E56346C3149D88c5D54C472 |
| RestakingVault | 0x0Ce45dd53affbb011884EF1866E0738f58AB7969 |
| stBTC          | 0xf6718b2701d4a6498ef77d7c152b2137ab28b8a3 |


#### Interact with RestakingVault
RestakingVault:`0x0Ce45dd53affbb011884EF1866E0738f58AB7969` is the contract that manages the stBTC pool. You can interact with the pool by calling the following functions.
#### Deposit
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


#### Request withdrawal
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

#### Claim
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