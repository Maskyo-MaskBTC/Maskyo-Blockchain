```markdown
# Maskyo Blockchain Framework

![License](https://img.shields.io/badge/License-MIT-blue)
![Solidity](https://img.shields.io/badge/Solidity-0.8.0-green)
![ReactNative](https://img.shields.io/badge/React%20Native-0.70+-yellow)

一个集成区块链、隐私保护与社交功能的开源框架，支持多链部署与抗量子加密。

[GitHub 仓库](https://github.com/Maskyo-MaskBTC/Maskyo-Blockchain) | [文档目录](/docs)

---

## 🌟 核心功能

### 区块链模块
- **智能合约体系**
  - `ReferralChain`: 用户推荐关系链（两层推荐人绑定）
  - `QuaReward`: QUA奖励计算与月度结算（性别差异化上限）
  - `MaskBTC`: 多计量单位代币（Myst/Voxel/Quanta）与衰减模型
  - `MaskWallet`: 机构多签钱包与个人生物特征钱包

### 客户端应用
- **跨平台视频社交**
  - P2P WebRTC 视频聊天（iOS/Android 原生实现）
  - 面具检测集成（TensorFlow Lite 模型）
- **去中心化钱包**
  - 生物特征认证（FaceID/TouchID/指纹）
  - 抗量子签名交易

### 服务器端
- **实时匹配系统**
  - 匿名匹配池管理（基于加密筛选条件）
- **链下服务**
  - QUA 临时存储与 Merkle 树验证
  - 后台管理系统（用户数据仪表盘）
  - 客户服务工单系统

### 安全架构
- **抗量子加密**
  - 晶格加密算法（Lattice-based Crypto）
  - 模糊提取器（生物特征密钥生成）
- **多层级钱包**
  - 个人钱包：单签+生物特征
  - 机构钱包：多签+阈值控制

---

## 🛠 项目结构

```bash
Maskyo/
├── /blockchain    # 智能合约（支持 BSC/Solana/Polygon）
├── /client        # 跨平台客户端（React Native + 原生模块）
├── /server        # Node.js 服务（含后台管理）
├── /security      # 加密与钱包安全模块
├── /docs          # 技术文档与 API 说明
└── /tests         # 智能合约与客户端测试
```

---

## 🚀 快速开始

### 合约部署
```bash
# 部署到 BSC 测试网
cd blockchain/deploy
npm install
npx hardhat run deploy_bsc.js --network bsc_testnet
```

### 客户端运行
```bash
# 安装依赖
cd client/shared
npm install

# iOS 端
cd ../ios
pod install
open MaskyoApp.xcworkspace

# Android 端
cd ../android
./gradlew assembleDebug
```

### 服务器启动
```bash
cd server
npm install
node src/server.js
```

---

## 🔍 关键组件

### MaskBTC 代币特性
| 功能              | 说明                          |
|-------------------|-----------------------------|
| **多计量单位**     | 1 MBTC = 1,000 Myst = 1M Voxel |
| **月度衰减**       | 48 个月期，每月减少 10% 奖励   |
| **灵活转账**       | 支持 Myst/Voxel/Quanta 单位转换 |

### 视频社交流程
1. 用户通过面具检测后加入匹配池
2. 服务端返回加密的候选用户列表
3. 建立 P2P WebRTC 连接
4. 通话时长自动计算 QUA 值（女性上限 360/天）

---

## 📚 开发指南

### 智能合约注意事项
```solidity
// ReferralChain 注册逻辑示例
function registerUser(bytes32 userHash, bytes32 referrer1Hash) {
  require(!registered[userHash], "用户已注册");
  // 自动绑定二级推荐人
  bytes32 referrer2Hash = referralChain[referrer1Hash].referrer1Hash;
}
```

### 客户端生物特征集成
```swift
// iOS 钱包签名（Swift）
LAContext().evaluatePolicy(.deviceOwnerAuthenticationWithBiometrics) { 
  success, _ in if success { signTransaction() }
}
```

### 安全建议
- 机构钱包需配置至少 2 个 MKey 和 2/3 多签策略
- 使用 `LatticeCrypto.js` 生成抗量子密钥
- 定期调用 `decayReward()` 更新代币奖励

---

## 🤝 贡献协议
- 遵循 MIT 开源协议
- 提交 PR 前请运行 `npm test` 通过所有测试用例
- 重大功能修改需同步更新 `/docs/api.md`

---

> 由 Maskyo 团队构建未来隐私社交基础设施 💫
``` 

这个 README 包含：
1. 项目徽章与快速导航
2. 模块化功能说明
3. 多平台部署指南
4. 关键特性表格化展示
5. 代码片段直接关联开发文档
6. 明确的贡献规范
可根据实际需求补充截图或详细 API 文档链接。
