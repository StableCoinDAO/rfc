# An RFC for Decentralized Stable Coin

* Discussion: [A decentralized stable coin without death spiral](https://github.com/StableCoinDAO/rfc/issues/1)
* [设计文档·中文](./rfc_zh.md)
* [Design Document · English](./rfc_en.md)

**核心特性**
1. 它是存在于区块链网络，由公开固化的算法控制的数字货币，不由任何人、组织、法人发行控制，不存在控制实体信用破产问题。
2. 它没有交易税，只有执行算法的 Gas 消耗。
3. 它没有铸币税，它的发行总价值与所有抵押品的总价值是 1:1。
4. 由于社会总资产是增值的，它的发行总量也会跟随增加。但它不是凭空增加发行，而是跟随抵押品升值及兑换来增发。
5. 它会支持多种抵押品，如 USDT、USDC、BTC 等，从而降低由某种抵押品贬值带来的系统稳定性风险。
6. 它没有绝对的锚定物，稳定性价值锚定会趋向于占大比例的抵押品。比如初期可能 USDT、USDC 比较多，相当于锚定美元。
7. 它只解决最基础的需求——提供稳定价值兑换，高级金融特性（如抵押收益、贷款等）由其它服务提供。
8. 任何用户在任何时间都能使用它——只需要私钥和网络，这是加密数字货币的基本能力。
