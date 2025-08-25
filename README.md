# Draft Secure Trading Platform

## Project Overview
Draft Secure is a decentralized trading platform leveraging the Stacks blockchain for transparent, secure peer-to-peer asset exchange with comprehensive marketplace systems, automated settlement, and secure verification infrastructure.

### Key Features
- Decentralized energy grid participant registration and management
- Peer-to-peer energy trading marketplace with real-time pricing
- Fungible energy tokens for standardized trading units
- Smart meter integration with verification system
- Secure grid operations and maintenance
- Automated trade settlement and dispute resolution

### Project Description
GridFlow revolutionizes energy distribution by providing a decentralized platform for energy trading and grid management. By leveraging the Stacks blockchain, GridFlow offers a transparent, secure, and efficient system for energy distribution. The platform combines participant registration, energy trading, tokenization, and metering to create a complete ecosystem for decentralized energy markets.

## Contract Architecture

### participant-registry.clar
The core registration and access control system for Draft Secure participants. Enhanced with trading metadata support.

**Data Structures**:
- `platform-participants`: Stores participant information including trading capabilities
- `pending-registrations`: Manages registration requests
- `participant-metadata`: Enhanced trading statistics and reputation data

**Public Functions**:
- `register-participant`: Register new platform participants
- `approve-registration`: Approve pending registrations
- `update-participant-info`: Update participant information
- `remove-participant`: Remove participants from the system
- `update-reputation-score`: Modify participant reputation based on trading history
- `record-transaction`: Log completed trades

### marketplace.clar
The marketplace contract enabling peer-to-peer asset trading.

**Key Features**:
- Asset listing management
- Dynamic pricing mechanisms
- Automated trade settlement
- Escrow system for secure transactions
- Dispute resolution system

**Public Functions**:
- `create-listing`: List asset for sale
- `purchase-asset`: Buy listed asset
- `place-bid`: Bid on auction-style listings
- `finalize-auction`: Complete auction-style sales
- `confirm-delivery`: Verify asset delivery
- `settle-payment`: Process payment after delivery
- `open-dispute`: Initiate dispute resolution

### utility-token.clar
A SIP-010 compliant fungible token representing standardized trading units.

**Features**:
- Fungible unit representation
- Standard token operations (transfer, mint, burn)
- Role-based minting and burning permissions
- Integration with trading system

**Key Functions**:
- `mint`: Create new tokens
- `burn`: Remove tokens from circulation
- `transfer`: Transfer tokens between participants
- `get-balance`: Check token holdings

### meter-management.clar
Asset verification and tracking system.

**Features**:
- Asset registration and management
- Reading verification
- Dispute resolution for submissions
- Production/consumption tracking

**Key Functions**:
- `register-tracker`: Add new tracking devices
- `submit-reading`: Record readings
- `verify-reading`: Validate submitted readings
- `file-dispute`: Contest incorrect readings
- `resolve-dispute`: Settle reading disputes

## Installation & Setup

1. Ensure you have Clarinet installed on your system.
2. Clone the Draft Secure repository: `git clone https://github.com/draft-secure/platform.git`
3. Navigate to the project directory: `cd draft-secure`
4. Install the project dependencies: `npm install`
5. Run the Clarinet development environment: `clarinet dev`

## Usage Guide

### Participant Registration
```clarity
(register-participant 'ABCD1234 PARTICIPANT-TYPE-TRADER "participant-metadata")
```

### Asset Trading
```clarity
;; List asset for sale
(create-listing u1000 u500 PRICING-FIXED u0)

;; Purchase asset
(purchase-asset u1)

;; Place bid (for auction listings)
(place-bid u1 u550)
```

### Utility Token Operations
```clarity
;; Transfer tokens
(transfer u100 tx-sender 'RECIPIENT none)

;; Check balance
(get-balance 'ADDRESS)
```

### Asset Tracking
```clarity
;; Register a tracking device
(register-tracker 0x1234 DEVICE-TYPE-PRIMARY "location")

;; Submit reading
(submit-reading 0x1234 block-height u100 0xSIGNATURE)
```

## Security Considerations

- **Role-Based Access Control**: Strict permissions for critical operations
- **Escrow System**: Secure trade settlement with funds in escrow
- **Verified Meters**: Only registered and verified meters can submit readings
- **Dispute Resolution**: Formal process for handling disputes
- **Multi-Stage Settlement**: Phased completion of trades with verification steps

## Examples

### Complete Trading Cycle
```clarity
;; 1. Create asset listing
(create-listing u1000 u500 PRICING-FIXED u0)

;; 2. Purchase asset
(purchase-asset u1)

;; 3. Confirm delivery
(confirm-delivery u1)

;; 4. Settle payment
(settle-payment u1)
```

### Reading Verification
```clarity
;; 1. Submit reading
(submit-reading 0x1234 block-height u100 0xSIGNATURE)

;; 2. Verify reading
(verify-reading 0x1234 block-height true "Verification notes")
```

### Token Operations
```clarity
;; Mint tokens to participant
(mint u1000 'PARTICIPANT_ADDRESS)

;; Transfer tokens
(transfer u100 tx-sender 'TARGET_ADDRESS none)
```

The Draft Secure platform provides a comprehensive solution for decentralized asset trading, from participant registration to final settlement, with robust security measures and dispute resolution mechanisms.