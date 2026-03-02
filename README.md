# Beanstalk — Flash Loan Governance Attack PoC (2022)

> **Educational Purpose Only** — This PoC is created for security research and education
> purposes only. It runs against a fork, not mainnet.

**Category:** Flash Loan Attacks (Governance Takeover)
**Loss:** ~$182M
**Chain:** Ethereum
**Date:** April 17, 2022

## Overview
Beanstalk Farms, a credit-based stablecoin protocol, was exploited for ~$182M through a governance attack powered by flash loans. The attacker flash-borrowed massive amounts of tokens, used them to gain majority voting power in Beanstalk's governance, then passed and immediately executed a malicious proposal that drained the protocol's treasury.

## How It Works
1. **VulnerableGovernance** allows instant voting with flash-borrowed tokens (no time lock, no snapshot)
2. **BeanstalkAttacker** flash loans tokens, votes with overwhelming majority, executes proposal
3. **FixedGovernance** demonstrates snapshot-based voting that prevents flash loan manipulation

## Quick Start
```bash
git clone https://github.com/NomosLabs-Security/poc-beanstalk-2022
cd poc-beanstalk-2022
forge install foundry-rs/forge-std --no-git
forge test -vvvv
```

## Details

- **Exploit Date:** 2022-04-17
- **Fork Block:** N/A (simplified simulation)
- **Expected Output:** Governance takeover via flash-borrowed voting power, draining treasury
- **Full Analysis:** [NomosLabs Security Intelligence Archive](https://nomoslabs.io/archive/beanstalk-2022)

## Key Takeaway
On-chain governance must use snapshot-based voting (voting power recorded at a past block) to prevent flash loan attacks. Allowing same-block or same-transaction voting makes any governance system exploitable. Time locks between proposal and execution are also critical.

## License

MIT — For educational use only.
