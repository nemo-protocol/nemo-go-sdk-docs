# Principal Token Operations Guide

## 1. MintPy
> Mint PT/YT pair by depositing underlying assets

```go
func MintPy(
    amountIn float64,      // Input amount
    sender *account.Account,// Sender account
    nemoConfig *models.NemoConfig, // Nemo configuration
) (bool, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| amountIn | float64 | Input asset amount |
| sender | *account.Account | User account information |
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

// Mint PT/YT pair
success, err := nemoService.MintPy(
    1000.0,             // Deposit 1000 tokens
    sender,            // User account
    config,            // Nemo configuration
)

if err != nil {
    log.Fatal(err)
}
```

---

## 2. RedeemPy
> Redeem underlying assets by burning PT/YT pair

```go
func RedeemPy(
    amountIn float64,      // Input amount of PT/YT pair
    sender *account.Account,// Sender account
    nemoConfig *models.NemoConfig, // Nemo configuration
) (bool, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| amountIn | float64 | Amount of PT/YT pair to redeem |
| sender | *account.Account | User account information |
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

// Redeem underlying assets
success, err := nemoService.RedeemPy(
    500.0,              // Redeem 500 PT/YT pairs
    sender,            // User account
    config,            // Nemo configuration
)

if err != nil {
    log.Fatal(err)
}
```

### Notes
- MintPy creates both PT and YT tokens in equal amounts
- RedeemPy requires both PT and YT tokens in equal amounts
- Ensure sufficient balance before operations
- Consider gas fees for transactions

### Best Practices
1. **Before Minting**
    - Check available balance
    - Verify market conditions
    - Understand minting ratio

2. **Before Redeeming**
    - Ensure equal PT/YT balance
    - Check redemption value
    - Consider timing for better returns

[Asset Exchange](/docs/AssetExchange.md)