# Asset Information Guide

## Query Asset Details
> Query the balance details of YT, PT, and LP tokens for a specific address

```go
func QueryAsset(
    nemoConfig *models.NemoConfig, // Nemo configuration
    address string,                // Wallet address
) (*models.AssetModel, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |
| address | string | Wallet address to query |

### Returns
| Type | Description |
|:-----|:------------|
| *models.AssetModel | Asset balance information |
| error | Error message if any |

### AssetModel Structure
```go
type AssetModel struct {
    YtBalance float64 `json:"ytBalance"` // Yield Token balance
    PtBalance float64 `json:"ptBalance"` // Principal Token balance
    LpBalance float64 `json:"lpBalance"` // Liquidity Provider Token balance
}
```

### Example
```go
// Initialize service
s := service.InitSuiService()

// Query asset details
address := "0x00"
assetInfo, err := s.QueryAsset(&list[3], address)
if err != nil {
    log.Fatal(err)
}

// Display asset information
fmt.Printf("YT Balance: %.6f\n", assetInfo.YtBalance)
fmt.Printf("PT Balance: %.6f\n", assetInfo.PtBalance)
fmt.Printf("LP Balance: %.6f\n", assetInfo.LpBalance)
```

### Usage Tips

1. **Balance Checking**
    - Regular balance checks recommended
    - Monitor changes after transactions
    - Verify balances before operations

2. **Query Recommendations**
    - Cache results when appropriate
    - Implement rate limiting for multiple queries
    - Handle network errors gracefully

### Notes
- Balance data is real-time from the blockchain
- Values are returned in their native precision
- Consider implementing caching for frequent queries
- Handle potential network delays and errors
