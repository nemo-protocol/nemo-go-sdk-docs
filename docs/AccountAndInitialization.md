# Account and Initialization Guide

## 1. SDK Installation
> Install Nemo Protocol SDK
```bash
go get github.com/nemo-protocol/nemo-go-sdk
```

## 2. Account Creation
> Create accessible account with private key for on-chain transaction signing
```go
sender := account2.NewAccountPrivateKey("your_private_key")
```

## 3. Service Initialization
> Initialize Sui service root node
```go
nemoService := service.InitSuiService()
```

## 4. Pool Configuration
> Get supported liquidity pool configurations
```go
pools := models.InitConfig()
```

### Supported Pool Types

The following table lists all currently supported pool types and their corresponding coinTypes:

| Token Name | Coin Type |
|:-----------|:----------|
| sSUI | `0xaafc4f740de0dd0dde642a31148fb94517087052f19afb0f7bed1dc41a50c77b::scallop_sui::SCALLOP_SUI` |
| sDEEP | `0xeb7a05a3224837c5e5503575aed0be73c091d1ce5e43aa3c3e716e0ae614608f::scallop_deep::SCALLOP_DEEP` |
| sUSDC | `0x854950aa624b1df59fe64e630b2ba7c550642e9342267a33061d59fb31582da5::scallop_usdc::SCALLOP_USDC` |
| sSCA | `0x5ca17430c1d046fae9edeaa8fd76c7b4193a00d764a0ecfa9418d733ad27bc1e::scallop_sca::SCALLOP_SCA` |
| ssbUSDT | `0xb1d7df34829d1513b73ba17cb7ad90c88d1e104bb65ab8f62f13e0cc103783d3::scallop_sb_usdt::SCALLOP_SB_USDT` |
| ssbETH | `0xb14f82d8506d139eacef109688d1b71e7236bcce9b2c0ad526abcd6aa5be7de0::scallop_sb_eth::SCALLOP_SB_ETH` |
| stSUI | `0xd1b72982e40348d069bb1ff701e634c117bb5f741f44dff91e472d3b01461e55::stsui::STSUI` |

> **Note**: Complete pool type configurations can be found in the SDK source code file `service/sui/common/constant/coinEnum.go`(https://github.com/nemo-protocol/nemo-go-sdk/blob/main/service/sui/common/constant/coinEnum.go).

### Example Usage

```go
// Initialize account
sender := account2.NewAccountPrivateKey("your_private_key")

// Initialize service
nemoService := service.InitSuiService()

// Get pool configurations
pools := models.InitConfig()

// Select specific pool
for _, pool := range pools {
    if pool.CoinType == "0xaafc...::SCALLOP_SUI" {
        // Perform operations with this pool
        break
    }
}
```

### Best Practices

1. **Account Security**
    - Securely store private keys
    - Use environment variables for sensitive data
    - Never hardcode private keys in source code

2. **Service Configuration**
    - Handle service initialization errors
    - Monitor connection status
    - Implement proper error handling

3. **Pool Selection**
    - Verify pool compatibility
    - Check pool liquidity
    - Monitor pool status before operations

[Liquidity Operations](/docs/LiquidityOperations.md)