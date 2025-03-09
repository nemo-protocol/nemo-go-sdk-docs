# Liquidity Operations Guide

## 1. Add Liquidity
> Add liquidity using `scoin` assets or underlying assets

```go
func AddLiquidity(
    amountIn float64,      // Input amount
    slippage float64,      // Slippage
    sender *account.Account,// Sender account
    amountInType string,   // Input asset type
    nemoConfig *models.NemoConfig, // Nemo configuration
) (bool, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| amountIn | float64 | Input asset amount |
| slippage | float64 | Transaction slippage percentage |
| sender | *account.Account | User account information |
| amountInType | string | Input asset type |
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |

### Returns
| Type | Description |
|:-----|:------------|
| bool | Whether operation succeeded |
| error | Error message if any |

### Example
```go
// Initialize account and configuration
sender := account.NewAccount(...)
config := &models.NemoConfig{...}

// Add liquidity
success, err := nemoService.AddLiquidity(
    1000.0,             // Add 1000 tokens
    0.01,              // 1% slippage
    sender,            // User account
    "0x2::sui::SUI",   // SUI token
    config,            // Nemo configuration
)

if err != nil {
    log.Fatal(err)
}
```

---

## 2. Redeem Liquidity
> Withdraw `scoin` assets or underlying assets from liquidity pool

```go
func RedeemLiquidity(
    amountOut float64,     // Withdrawal amount
    slippage float64,      // Slippage
    sender *account.Account,// Sender account
    amountOutType string,  // Withdrawal asset type
    nemoConfig *models.NemoConfig, // Nemo configuration
) (bool, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| amountOut | float64 | Desired withdrawal amount |
| slippage | float64 | Transaction slippage percentage |
| sender | *account.Account | User account information |
| amountOutType | string | Withdrawal asset type |
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |

### Returns
| Type | Description |
|:-----|:------------|
| bool | Whether operation succeeded |
| error | Error message if any |

### Example
```go
// Initialize account and configuration
sender := account.NewAccount(...)
config := &models.NemoConfig{...}

// Redeem liquidity
success, err := nemoService.RedeemLiquidity(
    500.0,              // Withdraw 500 tokens
    0.01,              // 1% slippage
    sender,            // User account
    "0x2::sui::SUI",   // Withdraw SUI tokens
    config,            // Nemo configuration
)

if err != nil {
    log.Fatal(err)
}
```

[Asset Exchange](/docs/AssetExchange.md)