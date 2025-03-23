# Stellar Token (STLR)

## Overview

Stellar Token (STLR) is a robust, feature-rich fungible token implementation built for the Stacks blockchain. This contract provides advanced token functionality with enhanced security features, governance capabilities, and comprehensive administrative controls.

## Features

- **Complete SIP-010 Compliance**: Fully implements the Stacks Improvement Proposal 10 standard for fungible tokens
- **Governance Mechanisms**: Built-in voting power tracking for decentralized decision-making
- **Token Security**:
  - Time-limited allowances for safer approvals
  - Token locking to prevent transfers for specific time periods
  - Address restriction system to prevent malicious activity
- **Supply Management**:
  - Maximum supply cap of 1 trillion tokens
  - Precision of 6 decimal places
  - Controlled minting with role-based permissions
- **Administrative Controls**:
  - Pausable functionality for emergency situations
  - Configurable ownership transfer
  - Initialization safety

## Technical Specifications

- **Token Name**: Stellar Token
- **Token Symbol**: STLR
- **Decimals**: 6
- **Maximum Supply**: 1,000,000,000,000,000 (1 trillion tokens)
- **Error Handling**: Comprehensive error reporting with unique error codes

## Contract Functions

### Read-Only Functions

- `get-name`: Returns the token name
- `get-symbol`: Returns the token symbol
- `get-decimals`: Returns the number of decimal places
- `get-total-supply`: Returns the current total supply
- `get-balance`: Returns the balance of a given account
- `get-allowance`: Returns the current allowance for a spender with expiry check
- `is-locked`: Checks if an address has locked tokens

### Administrative Functions

- `initialize`: Sets up the token parameters (name, symbol, decimals)
- `set-contract-owner`: Transfers ownership to a new principal
- `pause`: Temporarily stops all token transfers
- `unpause`: Restores token transfer functionality

### Token Operations

- `mint`: Creates new tokens to a specified recipient
- `transfer`: Moves tokens between accounts with governance tracking
- `approve`: Grants spending permission with automatic expiry

### Event Tracking

The contract emits events for all major state changes:
- Transfer events
- Mint events
- Burn events

## Security Considerations

- Overflow protection via safe arithmetic operations
- Robust validation for all inputs
- Protection against common attack vectors
- Time-bound approvals to limit exposure

## Usage Examples

### Initializing the Token

```clarity
(contract-call? .stellar-token initialize "Stellar Token" "STLR" u6)
```

### Minting Tokens

```clarity
(contract-call? .stellar-token mint u1000000 'SPNWZ5V2XQCM0YQCPGW7ZT8P0X17FBHNCJT7FWQA)
```

### Transferring Tokens

```clarity
(contract-call? .stellar-token transfer u500000 'SP9XD1NXQC1NVCVPKP3ZXYASQE52KQ5G02K1HZ5S)
```

### Approving a Spender

```clarity
;; Approve 100 tokens to spender, valid for 144 blocks (approx. 1 day)
(contract-call? .stellar-token approve u100000 'SP8CW12A65ATDWK33MFBV2KZM8JCPNBTH7BTGH25 (+ block-height u144))
```

## Development Roadmap

- [ ] Multi-sig administrative controls
- [ ] Custom token vesting schedules
- [ ] Enhanced governance voting mechanisms
- [ ] Automatic token distribution capabilities
- [ ] Cross-chain bridge support

## License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## Disclaimer

This token contract is provided as-is. Users and implementers should perform their own security audits before deployment to production environments.