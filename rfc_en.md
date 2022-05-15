> English Version

## Basic Design

1. It must be a smart contract that can be implemented in one more public blockchains that supports smart contracts and be logically consistent, and it must be compatible with the standard of smart contract exchange currency of the public blockchain. For example, Ethereum compatible ERC20 standard, thus seamless exchange.
2. We named the stable coin DSC, and users can mint DSC with supported tokens (such as ERC20 version USDT, USDC, BTC, etc.) through this contract (or redeem tokens).
3. The DSC contract is a public infrastructure, its minting, redeeming behavior is not controlled by anyone, exchange ratio is determined by the stability algorithm. DSC is also not controlled by anyone, completely produced by minting, and there is no upper limit.
4. DSC does not need the credit endorsement of other assets. Its initial assets are 0, and DSC is generated after seed users initiate minting.
5. DSC has no absolute anchor. It initially anchors US dollar, but considering that there may be depreciation behavior of US dollar, it may eventually anchor BTC, all determined by the stabilization algorithm.
6. There is no tax when minting or redeeming, only perform smart contract Gas consumption.
7. StableCoin DAO is responsible for adding "supported tokens" and the initial conversion ratio.

## Stabilization Algorithm

1. XUSD <-> DSC was used to describe the stable algorithm of minting and redeeming, and the initial exchange ratio was 1X:1D.
2. **Stable exchange model**: The DSC smart contract will try to maintain the stability of the value of its own assets, when the user uses 1X:1S to mint DSC, the request will be executed.
3. **XUSD devaluation mode**: The DSC smart contract cannot perceive the devaluation of external X token, but will recognize the appreciation of its own assets, that is, the initiator premium request: when the user uses 1.1X:1S to mint DSC, the request will be executed, and the exchange ratio will be updated to the weighted average value of 1.05X:1S of the transaction after execution.
4. The exchange ratio of subsequent minting requests shall be carried out in accordance with the new value, and the destruction shall be carried out in accordance with the same ratio. At this point, the user shall exchange 1S:1.05X for XUSD, and the request will be executed.
5. **XUSD appreciation model**: The DSC smart contract cannot perceive the appreciation of external X token, but will recognize the appreciation of its own assets, namely, the initiator's premium request: the user uses 1.1S:1.05X to redeem XUSD, the request will be executed, and the exchange ratio will be updated to the weighted average 1X:1S of the transaction after execution.
6. **Stabilization algorithm driving force**: Why do users want to exchange at a premium? For example, 1.1XUSD -> 1DSC and 1.1DSC -> 1.05XUSD. **Limit of transaction per hand, for example 1000DSC per hand, but allow users to premium to break the limit** For example, the user expects a transaction of 2000DSC, must premium 1.1 times.
7. **Stabilization algorithm design**: So, if a whale user wants to redeem 1 million XUSD, how should the premium be? It is necessary to design the specific calculation formula of "breaking the limit -> premium -> exchange ratio".

## Attack Scenario Analysis

### Can malicious pull up X token to mint DSC?
1. The attacker needs to prepare enough DSC to pull up X;
2. If the relative lifting cost of lifting X is not enough, the attack power is insufficient, and algorithm design can achieve this goal.
3. The StableCoin DAO, on the other hand, can run a guard robot that hedges an attacker's behavior based on real-world conditions.

### Can malicious redeem X token to destroy DSC?
1. The stability value of DSC is not determined by a single X token, but by all collateral currencies. The appreciation and depreciation of a single X token has little impact on the overall system.
2. DSC does not exist overshoot, attackers can not cheaply raise DSC to launch a run attack;
3. By the guard robot according to the real world situation in time to hedge the attacker's behavior.

## Across the blockchain transfer
