
# BetwithStacks: Decentralized Sports Betting Platform

**BetwithStacks** is a fully decentralized, peer-to-peer sports betting platform built on the **Stacks blockchain** using **Clarity smart contracts**. It allows users to create, join, and resolve betting events without intermediaries—ensuring fairness, transparency, and control.

---

## 🎯 Key Features

* **Decentralized Betting**
  Create and participate in sports wagers with no central authority or bookmaker.

* **Multiple Betting Types**

  * **Winner-take-all**: Winners split the full prize pool proportionally.
  * **Proportional**: Payouts are distributed according to stake size.
  * **Fixed-odds**: Classic bookmaker odds with pre-set payouts.

* **Transparent & Fair**
  All betting logic is verifiable and executed on-chain.

* **Autonomous Resolution**
  Events can be resolved through a trusted resolver with pre-defined rules.

* **User Protection**
  Includes cancellation, refund, and access control mechanisms to prevent abuse.

---

## 🔧 Smart Contract Architecture

BetwithStacks is powered by a single Clarity smart contract with the following components:

### 📦 Data Structures

* `wagers`: Stores details for all betting events.
* `bettor-positions`: Tracks user bets across wagers.
* `supported-wager-types`: Lists available betting mechanisms.

### ⚙️ Key Functions

#### For Wager Creators

* `create-wager`: Start a new betting event with customizable parameters.
* `close-wager`: Close betting once the end block is reached.
* `cancel-wager`: Cancel a wager and issue refunds (only before the end block).

#### For Bettors

* `place-bet`: Place a bet on a specific outcome with a defined amount.
* `claim-winnings`: Withdraw your earnings after the wager is resolved.

#### For Administrators

* `resolve-wager`: Resolve the wager by declaring winning outcomes.

#### Read-Only Functions

* `get-wager`: Fetch metadata and status of a given wager.
* `get-bettor-position`: Check individual betting positions.
* `get-current-block-height`: Returns the current blockchain height.

---

## 🧪 Getting Started

### Prerequisites

* [Clarinet](https://docs.stacks.co/docs/clarity/clarinet) – Local development and testing
* [Stacks Wallet](https://wallet.hiro.so) – For contract deployment and interaction

---

### 📥 Installation

Clone the repository:

```bash
git clone https://github.com/fhayvy/betstacks.git
cd betstacks
```

Initialize the Clarinet project:

```bash
clarinet integrate
```

Run tests:

```bash
clarinet test
```

---

## 🚀 Deployment

Deploy to Testnet:

```bash
clarinet deploy --testnet
```

Deploy to Mainnet:

```bash
clarinet deploy --mainnet
```

---

## 🧾 Usage Examples

### ✅ Creating a Betting Event

```clarity
(contract-call? .betwithstacks create-wager 
  "World Cup 2026 Winner" 
  (list "Brazil" "France" "Germany" "Argentina" "Spain") 
  u100000 
  "fixed-odds" 
  (some (list u200 u350 u400 u250 u500)))
```

### 💸 Placing a Bet

```clarity
(contract-call? .betwithstacks place-bet u0 u1 u1000)
```

### 🎉 Claiming Winnings

```clarity
(contract-call? .betwithstacks claim-winnings u0)
```

---

## 🔐 Security Considerations

* Role-based function access to prevent unauthorized actions
* Immutable event outcomes once resolved
* Smart contract escrows hold funds until resolution
* Explicit error codes for clear debugging and safer interaction

---

## 🤝 Contributing

1. Fork the repository
2. Create a new branch:

   ```bash
   git checkout -b feature/amazing-feature
   ```
3. Commit your changes:

   ```bash
   git commit -m 'Add some amazing feature'
   ```
4. Push to the branch:

   ```bash
   git push origin feature/amazing-feature
   ```
5. Open a Pull Request 🚀

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

* The [Stacks](https://www.stacks.co) community
* Clarity language developers
* Open-source contributors supporting decentralized finance and betting innovation

---

