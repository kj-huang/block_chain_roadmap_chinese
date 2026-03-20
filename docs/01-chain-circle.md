# 鏈圈世界 — 技術開發路線圖

> 鏈圈是區塊鏈技術的核心 — 這條路線適合想成為區塊鏈開發者的你。
> 從智能合約到 DApp，從 Layer 2 到零知識證明，一步步建立你的技術棧。

## 圖例

| 標記 | 意義 |
|------|------|
| 🟠 | 個人推薦 — 強烈建議優先學習 |
| 🟡 | 建議學習 — 有助於全面理解 |
| ⬜ | 任君挑選 — 依個人興趣深入 |

---

## Level 1：程式語言基礎

在開始寫智能合約之前，你需要至少掌握一種區塊鏈相關的程式語言。

### 🟠 Solidity

- 以太坊智能合約的主要語言，入門首選
- 語法類似 JavaScript / C++
- 生態系最成熟、學習資源最多
- 學習資源：[CryptoZombies](https://cryptozombies.io/)、[Solidity by Example](https://solidity-by-example.org/)

### 🟡 Rust

- Solana、Polkadot、Near、Sui (Move 是 Rust-based) 等生態系的主力語言
- 學習曲線較陡峭，但效能優異
- 如果你對 Solana 或底層協議開發有興趣，Rust 是必備技能
- 學習資源：[The Rust Book](https://doc.rust-lang.org/book/)

### 🟡 JavaScript / TypeScript

- DApp 前端開發必備
- 與區塊鏈互動的工具庫（ethers.js、viem）都是 JS/TS
- 測試框架（Hardhat）也基於 JS/TS
- 如果你已經是前端開發者，這是你最快上手的路徑

### ⬜ Go

- Geth（以太坊官方客戶端）以 Go 撰寫
- Cosmos SDK 也使用 Go
- 適合想參與底層協議開發的人

### ⬜ Move

- 由 Meta (Facebook) 的 Diem 專案誕生
- 用於 Aptos 和 Sui 區塊鏈
- 以資源導向程式設計為特色，天生防止重入攻擊

---

## Level 2：智能合約開發

### 🟠 Solidity 深入

- 資料型別、映射 (mapping)、結構體 (struct)
- 繼承、介面 (interface)、抽象合約
- 事件 (Events) 與日誌 (Logs)
- 錯誤處理：`require`、`revert`、自訂錯誤
- 存取控制：`Ownable`、角色管理
- Gas 優化技巧

### 🟠 開發框架

| 框架 | 說明 | 推薦程度 |
|------|------|----------|
| [Hardhat](https://hardhat.org/) | JavaScript/TypeScript 生態，插件豐富，社群最大 | 🟠 入門首選 |
| [Foundry](https://book.getfoundry.sh/) | Rust 打造，速度極快，用 Solidity 寫測試 | 🟠 進階推薦 |
| [Remix IDE](https://remix.ethereum.org/) | 瀏覽器內 IDE，適合快速原型 | 🟡 學習用 |

### 🟡 OpenZeppelin 合約庫

- 業界標準的安全合約模板
- ERC-20 / ERC-721 / ERC-1155 實作
- 存取控制、可暫停、重入鎖等常用模組
- 文件：[OpenZeppelin Docs](https://docs.openzeppelin.com/contracts/)

### 🟡 合約安全

你寫的合約管理的是真金白銀，安全至關重要。

| 攻擊類型 | 說明 |
|----------|------|
| 重入攻擊 (Reentrancy) | 惡意合約在你的合約完成狀態更新前重複呼叫 |
| 整數溢位 (Overflow) | Solidity 0.8+ 已內建防護，但仍需注意 unchecked 區塊 |
| 存取控制漏洞 | 忘記加上權限檢查，任何人都能呼叫敏感函數 |
| 前端攻擊 (Front-running) | 攻擊者看到你的交易後搶先執行 |
| 閃電貸攻擊 (Flash Loan) | 利用無擔保貸款操縱價格或榨取套利空間 |

- 學習資源：[Ethernaut](https://ethernaut.openzeppelin.com/)（智能合約安全挑戰）

### 🟡 合約升級模式

智能合約部署後不可修改，但可以透過代理模式 (Proxy Pattern) 實現邏輯升級。

| 模式 | 說明 |
|------|------|
| Transparent Proxy | 管理者和使用者走不同路徑，避免函數衝突 |
| UUPS | 升級邏輯放在實作合約中，Gas 更低 |
| Beacon Proxy | 多個代理共享同一個實作，適合批量部署 |
| Diamond (EIP-2535) | 模組化升級，適合超大型合約系統 |

### ⬜ 形式化驗證

- 用數學方法證明合約行為符合規格
- 工具：Certora、K Framework
- 成本高但安全性最高，常見於 DeFi 大型協議

---

## Level 3：DApp 前端開發

### 🟠 區塊鏈互動套件

| 套件 | 說明 |
|------|------|
| [viem](https://viem.sh/) | 輕量、型別安全的以太坊互動庫（新專案推薦） |
| [ethers.js](https://docs.ethers.org/) | 老牌經典，文件豐富，社群龐大 |
| [wagmi](https://wagmi.sh/) | 基於 viem 的 React Hooks 套件 |
| [web3.js](https://web3js.readthedocs.io/) | 最早的以太坊 JS 庫，仍有不少專案使用 |

### 🟠 錢包整合

- MetaMask — 最普及的瀏覽器錢包
- WalletConnect — 連接行動裝置錢包的開放協議
- [RainbowKit](https://www.rainbowkit.com/) / [ConnectKit](https://docs.family.co/connectkit) — 開箱即用的錢包連接 UI 元件

### 🟡 鏈上資料索引

- [The Graph](https://thegraph.com/) — 建立 Subgraph 索引鏈上事件，用 GraphQL 查詢
- [Goldsky](https://goldsky.com/) — The Graph 的替代方案，更快的同步速度
- 直接讀取合約 vs 索引事件：了解何時用哪種方式

### 🟡 去中心化儲存

| 方案 | 說明 |
|------|------|
| [IPFS](https://ipfs.tech/) | 內容定址的分散式檔案系統 |
| [Arweave](https://arweave.org/) | 一次付費、永久儲存 |
| [Filecoin](https://filecoin.io/) | 基於 IPFS 的激勵層，付費存儲 |

### ⬜ 進階前端

- [Ceramic](https://ceramic.network/) — 去中心化資料網路，可變資料流
- [Lens Protocol](https://lens.xyz/) — 去中心化社交圖譜
- ENS (Ethereum Name Service) — 將錢包地址映射到 .eth 網域名稱

---

## Level 4：主流公鏈生態深入

### 🟠 Ethereum

- EVM (以太坊虛擬機) 的運作原理
- EIP (以太坊改進提案) 流程
- 合併後架構：執行層 (Execution Layer) + 共識層 (Consensus Layer)
- 路線圖：The Surge（分片）、The Scourge（MEV）、The Verge（Verkle Trees）等

### 🟡 Layer 2 擴展方案

| 類型 | 代表 | 特色 |
|------|------|------|
| Optimistic Rollup | Optimism、Arbitrum、Base | 樂觀假設交易有效，有挑戰期 |
| ZK Rollup | zkSync、Starknet、Scroll、Linea | 用零知識證明驗證交易，即時確認 |
| 追蹤工具 | [L2Beat](https://l2beat.com/) | L2 生態系數據儀表板 |

- 了解 Rollup 的核心原理：將交易批次壓縮後提交到 L1
- Sequencer 的角色與中心化風險
- 跨 L2 橋接的使用與安全考量

### 🟡 Solana

- 高效能 L1：每秒可處理數千筆交易
- Program（合約）開發：使用 Rust 或 Anchor 框架
- 帳戶模型與 Ethereum 不同（帳戶 vs 合約分離）
- 工具：[Anchor](https://www.anchor-lang.com/)、[Solana Playground](https://beta.solpg.io/)

### ⬜ Cosmos 生態系

- 「區塊鏈的網際網路」— 每條鏈可自訂但透過 IBC 互通
- Cosmos SDK — 用 Go 語言打造自己的區塊鏈
- CometBFT (原 Tendermint) — 共識引擎
- 代表應用鏈：Osmosis (DEX)、dYdX v4、Celestia (模組化 DA)

### ⬜ Polkadot

- 中繼鏈 + 平行鏈架構
- [Substrate](https://substrate.io/) — 打造平行鏈的框架
- 共享安全性：平行鏈繼承中繼鏈的安全保障

### ⬜ Bitcoin 生態系新發展

- Ordinals — 在 Bitcoin 上刻錄 NFT
- BRC-20 — 基於 Ordinals 的代幣標準
- Lightning Network — 鏈下支付通道，實現即時小額交易
- Taproot 升級 — 增強隱私與智能合約能力

---

## Level 5：進階主題

### 🟡 零知識證明 (ZKP)

零知識證明是區塊鏈擴展和隱私的未來。

| 技術 | 說明 |
|------|------|
| zk-SNARKs | 簡潔非互動式知識論證，證明體積小 |
| zk-STARKs | 不需可信設定，抗量子計算 |
| Circom | 撰寫零知識電路的 DSL |
| Halo2 | Zcash 團隊開發的 ZK 證明系統 |

- 應用：ZK Rollup、隱私交易、身份驗證
- 學習資源：[ZK Book](https://www.rareskills.io/zk-book)

### 🟡 帳戶抽象 (Account Abstraction, ERC-4337)

- 讓智能合約帳戶取代 EOA（外部擁有帳戶）
- 實現：社交恢復、Gas 代付、批次交易、多簽
- 大幅改善用戶體驗，降低 Web3 入門門檻
- 工具：[Pimlico](https://pimlico.io/)、[ZeroDev](https://zerodev.app/)

### ⬜ 跨鏈橋原理與安全

- 鎖定-鑄造模型、流動性池模型
- 歷史重大攻擊：Ronin Bridge ($600M)、Wormhole ($320M)
- 安全考量：多簽治理、延時機制、形式化驗證

### ⬜ MEV (最大可提取價值)

- 區塊提議者可以通過排序、插入、審查交易來獲取價值
- Flashbots — 透明化 MEV 的生態系
- MEV-Boost — 驗證者委託專業 Searcher/Builder 建構區塊
- PBS (Proposer-Builder Separation) — 以太坊的長期 MEV 解決方案

### ⬜ 去中心化身份 (DID)

- W3C DID 標準 — 自主身份
- 可驗證憑證 (Verifiable Credentials)
- Soulbound Token (SBT) — 不可轉讓的代幣，代表身份/成就
- 應用：信用系統、學歷認證、DAO 治理身份

---

## Level 6：安全審計與測試

### 🟠 測試策略

| 類型 | 說明 | 工具 |
|------|------|------|
| 單元測試 | 針對個別函數的正確性 | Hardhat、Foundry |
| 整合測試 | 多個合約交互的場景 | Hardhat、Foundry |
| Fuzz Testing | 隨機輸入找出邊界案例 | Foundry (`forge fuzz`)、Echidna |
| Invariant Testing | 驗證系統不變量始終成立 | Foundry (`forge invariant`) |
| Fork Testing | 在主網的分叉上測試 | Foundry (`forge fork`) |

### 🟡 靜態分析工具

| 工具 | 說明 |
|------|------|
| [Slither](https://github.com/crytic/slither) | Trail of Bits 開發，最常用的靜態分析器 |
| [Mythril](https://github.com/Consensys/mythril) | 符號執行引擎，可偵測多種漏洞 |
| [Aderyn](https://github.com/Cyfrin/aderyn) | Rust 打造的新一代靜態分析工具 |

### 🟡 審計流程

1. 閱讀專案文件和規格
2. 手動程式碼審查（逐行閱讀）
3. 執行靜態分析工具
4. 撰寫 PoC (概念驗證) 測試
5. 撰寫審計報告（嚴重性分級：Critical / High / Medium / Low / Informational）

### ⬜ Bug Bounty 平台

| 平台 | 說明 |
|------|------|
| [Immunefi](https://immunefi.com/) | Web3 最大的漏洞獎金平台 |
| [Code4rena](https://code4rena.com/) | 競賽式審計，獎金豐厚 |
| [Sherlock](https://sherlock.xyz/) | 審計競賽 + 保險 |
| [Hats Finance](https://hats.finance/) | 去中心化漏洞獎金 |

---

## 開發者工具箱（快速參考）

| 用途 | 工具 |
|------|------|
| 開發框架 | Hardhat、Foundry |
| 線上 IDE | Remix、Solana Playground |
| 測試網 | Sepolia、Holesky（以太坊）；Devnet（Solana） |
| 區塊瀏覽器 | Etherscan、Blockscout、Solscan |
| 節點服務 (RPC) | Alchemy、Infura、QuickNode |
| 前端套件 | wagmi + viem、RainbowKit |
| 安全工具 | Slither、Mythril、Echidna |
| Gas 追蹤 | Etherscan Gas Tracker |
| 合約驗證 | Sourcify、Etherscan Verify |
| 多鏈部署 | Hardhat Deploy、CREATE2 |

---

## 建議學習順序

```
程式語言基礎 (Solidity + JS/TS)
        │
        ▼
智能合約開發 (Hardhat → OpenZeppelin → 安全)
        │
        ▼
DApp 前端 (viem/wagmi → 錢包整合)
        │
        ▼
  選擇一條深入路線
   ┌────┼────┐
   ▼    ▼    ▼
  L2  Solana  ZKP
```

---

## 下一步

- [返回首頁](../README.md)
- [幣圈世界 — 交易與投資路線](./02-coin-circle.md)
- [礦圈世界 — 挖礦與驗證路線](./03-mining-circle.md)
- [參考資源總覽](./04-resources.md)
