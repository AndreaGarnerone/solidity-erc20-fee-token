# TokenMagico ERC20

An ERC20 token written in Solidity that extends the OpenZeppelin implementation by adding a transaction fee, a dedicated treasury, and the ability to pause all transfers.

The project began as a practical exercise and demonstration to explore common patterns in smart contract development on Ethereum.

---

## Key Features

- **ERC20** standard based on OpenZeppelin
- Configurable transaction fee (0–100%)
- Treasury that automatically collects fees
- Fee exemption for selected addresses
- Ability to **pause** and **resume** all transfers
- Full control via **Ownable**
- Events for all relevant administrative operations

---

## Fee Logic

During a transfer:

- If `taxFee == 0`, the transfer proceeds normally
- If the sender or recipient is exempt, **no fee is applied**
- Otherwise:
  - a percentage of the amount is sent to the treasury
  - the remainder goes to the recipient

The fee is expressed as a whole number percentage (`0–100`).

---

## Special Roles

- **Owner**
  - Can modify the fee
  - Can change the treasury
  - Can set exemptions
  - Can pause the contract

- **Treasury**
  - Automatically receives fees
  - Is exempt from the fee


Translated with DeepL.com (free version)
