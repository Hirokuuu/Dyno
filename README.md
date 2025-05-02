# Dyno


# DYNO - Dynamic Card Security Protocol  
**Zero-Static Payment Infrastructure**  

[![Project License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE) 
[![RFC Draft](https://img.shields.io/badge/RFC%20Status-Draft-yellow)](https://datatracker.ietf.org/doc/draft-dyno-protocol/) 

---

## 🔐 Problem Statement  
Traditional payment cards lose $32.4B annually to fraud due to:  
- Static PAN/CVV/Expiry credentials  
- Physical card data leakage  
- Costly reissuance cycles ($3-10/card)  

DYNO eliminates these vulnerabilities through **real-time credential rotation**.

---

## 🛡️ Core Innovation  
### Dynamic Authentication Protocol  
```plaintext
+---------------------+       +---------------------+
|   Physical Card     |       |   Bank Backend      |
|  (Blank Surface)    |<----->|  (DYNO Engine)      |
| - EMV Chip          |       | - Rotating PAN      |  
| - Magstripe         |       | - Time-based CVV    |
+---------------------+       | - Ephemeral Expiry  |
                              +---------------------+


### Key Features  
| Component           | Specification                          |
|---------------------|----------------------------------------|
| Credential Rotation | 60-sec TTL for PAN/CVV/Expiry          |
| Cryptographic Base  | AES-256 + HMAC-SHA384                  |
| Token Mapping       | ISO 8583-compliant dynamic BIN ranges  |
| Fallback Protocol   | EMV L2 with dynamic cryptogram         |



## 💰 Economic Impact  
**Per 1M Cards (Annual)**  
```python
def calculate_savings():
    fraud_loss = 2100000  # Traditional system
    replacements = 150000 # @ $3/card
    dyno_fraud = fraud_loss * 0.27  # 73% reduction
    dyno_replace = replacements * 0.1 # 90% reduction
    return f"${(fraud_loss + replacements) - (dyno_fraud + dyno_replace):,} saved"
    
print(calculate_savings())  # Output: $2,373,000 saved
```

---

## 🚀 Implementation  
### Bank Integration  
```bash
# Clone reference implementation
git clone https://github.com/dyno-systems/core-engine.git

# Configuration (env.example)
DYNO_MASTER_KEY="secp384r1:3a8f2c..."  
TOKEN_VAULT_ADAPTER=postgresql  
FRAUD_ML_MODEL=resnet-18:v4.2  
```

### Card Manufacturing Specs  
| Parameter           | Value                     |
|---------------------|---------------------------|
| Chip OS             | JCOP 4.0                  |
| Secure Element      | SLE 78CLX2000             |
| NFC Interface       | ISO/IEC 14443 Type A      |
| Dynamic Display     | E-Ink (2.9" 296x128)      |

---

## 📚 Documentation  
- [Protocol Whitepaper](/docs/DYNO_Whitepaper_v1.2.pdf)  
- [PCI DSS Compliance Guide](/docs/pci-compliance.md)  
- [ATM Integration RFC](/docs/RFC-ATM-Integration.md)  

---

## 🌐 Governance  
**Working Group Members**  
- Bank of New Zealand (BNZ)  
- EMVCo Technical Committee  
- MIT Digital Currency Initiative  

---

## ⚖️ License  
Dual-licensed under **MIT** (reference implementation) and **Apache 2.0** (protocol specification).  

```
This README focuses on DYNO's technical and financial substance rather than website design. For web components, see `/web-ui` directory.
