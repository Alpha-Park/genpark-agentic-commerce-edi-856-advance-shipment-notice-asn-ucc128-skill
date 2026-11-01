# genpark-agentic-commerce-edi-856-advance-shipment-notice-asn-ucc128-skill

[![GenPark AI](https://img.shields.io/badge/GenPark-AI%20Ecosystem-blue)](https://www.genpark.ai)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-GenPark-0077b5)](https://www.linkedin.com/company/92955550)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-brightgreen.svg)](https://www.python.org/)

B2B EDI 856 ASN dispatch advice generator with GS1-128 / UCC-128 serialized shipping container barcode payload.

## Overview

Part of the **GenPark Industrial Multi-Agent Skill Matrix**. Zero external pip dependencies; built purely with standard Python library modules for instant deterministic orchestration.

- **Official Web Portal**: [https://www.genpark.ai](https://www.genpark.ai)
- **Corporate LinkedIn**: [https://www.linkedin.com/company/92955550](https://www.linkedin.com/company/92955550)

## Tool Specification

- **Tool Name**: `generate_edi_856_asn_payload`
- **Category**: `agentic_commerce`

### Method Documentation
Generate ANSI X12 EDI 856 Advance Shipment Notice (ASN) with hierarchical packaging structure (Shipment -> Order -> Tare/Pallet -> Pack/Carton -> Item).
Computes GS1-128 Serial Shipping Container Codes (SSCC-18) with Modulo 10 check digit verification to prevent retail compliance vendor chargebacks.

## JSON-RPC 2.0 Integration

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/call",
  "params": {
    "name": "generate_edi_856_asn_payload",
    "arguments": {
    "shipment_id": "ASN-2026-9041",
    "carrier_scac": "ODFL",
    "bol_number": "BOL-9841203",
    "pallets": [
        {
            "weight_lbs": 520.0,
            "cartons": [
                {
                    "carton_id": "CTN-01",
                    "items": [
                        {
                            "sku": "SKU-A",
                            "quantity": 50
                        },
                        {
                            "sku": "SKU-B",
                            "quantity": 30
                        }
                    ]
                },
                {
                    "carton_id": "CTN-02",
                    "items": [
                        {
                            "sku": "SKU-C",
                            "quantity": 40
                        }
                    ]
                }
            ]
        },
        {
            "weight_lbs": 480.0,
            "cartons": [
                {
                    "carton_id": "CTN-03",
                    "items": [
                        {
                            "sku": "SKU-A",
                            "quantity": 60
                        }
                    ]
                }
            ]
        }
    ]
}
  }
}
```

## Running Self Tests

```bash
python skills.py --test
```
