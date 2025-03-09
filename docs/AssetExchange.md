# Nemo Protocol SDK Documentation

## AssetExchange Module

### 1. SwapByPy
> Exchange `pt` or `yt` assets for `coin`

```go
func SwapByPy(
    amountIn float64,      // Input amount
    slippage float64,      // Slippage
    amountInType string,   // Input asset type
    amountOutType string,  // Output asset type
    sender *account.Account,// Sender account
    nemoConfig *models.NemoConfig, // Nemo configuration
) (bool, error)
```

#### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| amountIn | float64 | Input asset amount |
| slippage | float64 | Transaction slippage percentage |
| amountInType | string | Input asset type |
| amountOutType | string | Output asset type (constant.PYTYPE or constant.YTTYPE) |
| sender | *account.Account | User account information |
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |

#### Returns
| Type | Description |
|:-----|:------------|
| bool | Whether transaction succeeded |
| error | Error message if any |

#### Example
```go
success, err := nemoService.SwapByPy(
    100.0,              // Input 100 tokens
    0.01,              // 1% slippage
    constant.PYTYPE,    // Input PT type
    "0x2::sui::SUI",   // Output SUI
    sender,            // User account
    config,            // Nemo configuration
)
```

---

### 2. SwapToPy
> Exchange `coin` for `pt` or `yt` assets

```go
func SwapToPy(
    amountIn float64,      // Input amount
    slippage float64,      // Slippage
    amountInType string,   // Input asset type
    amountOutType string,  // Output asset type
    sender *account.Account,// Sender account
    nemoConfig *models.NemoConfig, // Nemo configuration
) (bool, error)
```

#### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| amountIn | float64 | Input asset amount |
| slippage | float64 | Transaction slippage percentage |
| amountInType | string | Input asset type (e.g., "0x2::sui::SUI") |
| amountOutType | string | Output asset type (constant.PYTYPE or constant.YTTYPE) |
| sender | *account.Account | User account information |
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |

#### Returns
| Type | Description |
|:-----|:------------|
| bool | Whether transaction succeeded |
| error | Error message if any |

#### Example
```go
success, err := nemoService.SwapToPy(
    100.0,              // Input 100 SUI
    0.01,              // 1% slippage
    "0x2::sui::SUI",   // Input SUI
    constant.PYTYPE,    // Output PT type
    sender,            // User account
    config,            // Nemo configuration
)
```

#### Notes
- Ensure account has sufficient gas fees
- Recommended to trade during high liquidity periods
- Use query interface to get estimated transaction results

[Reward Claims](/docs/RewardClaims.md)