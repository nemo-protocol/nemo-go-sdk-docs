# Reward Claims Guide

## 1. Claim YT Rewards
> Claim `YT` (Yield Token) rewards

```go
func ClaimYtReward(
    nemoConfig *models.NemoConfig, // Nemo configuration
    sender *account.Account,       // Sender account
) (bool, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |
| sender | *account.Account | User account information |

### Returns
| Type | Description |
|:-----|:------------|
| bool | Whether the claim operation succeeded |
| error | Error message if any |

### Example
```go
// Initialize account and configuration
sender := account.NewAccount(...)
config := &models.NemoConfig{...}

// Claim YT rewards
success, err := nemoService.ClaimYtReward(
    config,            // Nemo configuration
    sender,           // User account
)

if err != nil {
    log.Fatal(err)
}

if success {
    fmt.Println("Successfully claimed YT rewards")
}
```

---

## 2. Claim LP Rewards
> Claim Liquidity Provider (LP) rewards

```go
func ClaimLpReward(
    nemoConfig *models.NemoConfig, // Nemo configuration
    sender *account.Account,       // Sender account
) (bool, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |
| sender | *account.Account | User account information |

### Returns
| Type | Description |
|:-----|:------------|
| bool | Whether the claim operation succeeded |
| error | Error message if any |

### Example
```go
// Initialize account and configuration
sender := account.NewAccount(...)
config := &models.NemoConfig{...}

// Claim LP rewards
success, err := nemoService.ClaimLpReward(
    config,            // Nemo configuration
    sender,           // User account
)

if err != nil {
    log.Fatal(err)
}

if success {
    fmt.Println("Successfully claimed LP rewards")
}
```

### Notes
- Ensure account has sufficient gas fees
- Regular claiming is recommended for optimal returns
- Use query interface to check claimable reward amounts
- Monitor gas prices for cost-effective claiming
- Consider network congestion when timing claims
- Keep track of claimed rewards for tax purposes
- Check reward rates and vesting schedules if applicable

### Best Practices
1. **Timing Your Claims**
    - Monitor gas fees for optimal claiming times
    - Consider reward accumulation rates
    - Check network congestion levels

2. **Cost Management**
    - Calculate gas costs against reward values
    - Batch claims when possible
    - Consider reward thresholds

3. **Record Keeping**
    - Track all claim transactions
    - Monitor reward rates over time
    - Keep records for tax purposes

### Common Issues and Solutions
| Issue | Solution |
|:------|:---------|
| Transaction Failed | Check gas fees and network status |
| No Rewards Available | Verify staking period and amounts |
| High Gas Fees | Wait for off-peak hours |
| Claim Stuck Pending | Check transaction status on explorer |

---

## Additional Resources
- [Reward Calculator](#)
- [Gas Price Tracker](#)
- [Network Status](#)

[Pool Information](/docs/PoolInformation.md)