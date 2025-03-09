# Pool Information Guide

## Query Pool APY
> Query the Annual Percentage Yield (APY) of liquidity pools

```go
func QueryPoolApy(
    nemoConfig *models.NemoConfig, // Nemo configuration
) (*models.ApyModel, error)
```

### Parameters
| Parameter | Type | Description |
|:----------|:-----|:------------|
| nemoConfig | *models.NemoConfig | Nemo protocol configuration |

### Returns
| Type | Description |
|:-----|:------------|
| *models.ApyModel | APY information |
| error | Error message if any |

### ApyModel Structure
```go
type ApyModel struct {
    PoolApy string `json:"poolApy"` // Total pool yield rate
    PtApy   string `json:"ptApy"`   // Principal Token APY
    YtApy   string `json:"ytApy"`   // Yield Token APY
}
```

> **Important Note**: All APY values are multiplied by 100. For example, if the returned value is "1000", the actual APY is 10%.

### Example
```go
// Initialize configuration
config := &models.NemoConfig{...}

// Query APY
apyInfo, err := nemoService.QueryPoolApy(config)
if err != nil {
    log.Fatal(err)
}

// Convert and display actual APY
poolApy, _ := strconv.ParseFloat(apyInfo.PoolApy, 64)
ptApy, _ := strconv.ParseFloat(apyInfo.PtApy, 64)
ytApy, _ := strconv.ParseFloat(apyInfo.YtApy, 64)

fmt.Printf("Pool APY: %.2f%%\n", poolApy/100)  // Actual percentage
fmt.Printf("PT APY: %.2f%%\n", ptApy/100)      // Actual percentage
fmt.Printf("YT APY: %.2f%%\n", ytApy/100)      // Actual percentage
```

### Usage Tips

1. **APY Calculation Notes**
    - Returned APY values are multiplied by 100
    - Divide by 100 to get actual percentage
    - Example: returned value "1000" → actual APY 10%

2. **Query Recommendations**
    - Recommended to query hourly for latest APY
    - Compare historical data to observe yield trends

### Notes
- APY data is real-time and may fluctuate with market conditions
- Convert values to readable percentage format for display
- Use correct proportions when calculating yields