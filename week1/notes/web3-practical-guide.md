# Web3 实操指南：从零到链上交互

## 前置准备

- 浏览器：Chrome / Firefox / Brave（推荐 Chrome）
- 网络：稳定的互联网连接
- 时间：约 30-60 分钟

---

## 第一步：安装 MetaMask 钱包

### 1.1 安装扩展

1. 打开 Chrome，访问 [MetaMask 官网](https://metamask.io/)
2. 点击 "Download" → "Install MetaMask for Chrome"
3. 在 Chrome Web Store 点击 "添加至 Chrome"
4. 安装完成后，浏览器右上角出现狐狸图标

### 1.2 创建钱包

1. 点击狐狸图标，点击 "开始使用"
2. 点击 "创建钱包"（不是"导入钱包"）
3. 同意或跳过数据使用计划
4. **设置密码**（至少 8 位，包含大小写和数字）
5. **备份助记词**：
   - 系统会显示 12 个英文单词
   - **必须按顺序手抄到纸上**（不要截图、不要复制到电脑）
   - 系统会要求你按顺序点击确认
6. 完成创建

### 1.3 记录你的地址

1. 点击账户名（顶部），复制地址
2. 地址格式：`0x...`（42 个字符）
3. **记录到下方"实验记录"中**

### 安全提醒

- 助记词 = 你的资产控制权，泄露 = 失去一切
- 永远不要在任何网站输入助记词（除了恢复你自己的钱包）
- 永远不要截图或电子存储助记词
- MetaMask 官方永远不会主动找你要助记词

---

## 第二步：切换到 Sepolia 测试网

### 2.1 添加 Sepolia 网络

1. 点击 MetaMask 顶部的网络选择器（默认显示 "Ethereum 主网"）
2. 点击 "显示测试网络"（如果没看到，去 设置 → 高级 → 显示测试网络，打开开关）
3. 选择 "Sepolia"
4. 确认切换

### 2.2 验证网络

- 网络选择器应显示 "Sepolia 测试网络"
- 余额应显示 0 SepoliaETH（正常，还没领测试币）

---

## 第三步：领取 Sepolia 测试币

### 3.1 使用 Alchemy Faucet

1. 访问 [Sepolia Faucet](https://sepoliafaucet.com/)
2. 用 GitHub 账号登录（需要 GitHub 账号）
3. 粘贴你的钱包地址（从第一步复制的 `0x...`）
4. 点击 "Send Me ETH"
5. 等待 1-2 分钟

### 3.2 备选方案（如果 Alchemy 不可用）

- [Infura Sepolia Faucet](https://www.infura.io/faucet/sepolia)
- [QuickNode Faucet](https://faucet.quicknode.com/ethereum/sepolia)

### 3.3 验证到账

1. 回到 MetaMask
2. 确认网络为 Sepolia
3. 余额应显示约 0.5-1 SepoliaETH
4. **记录到账金额**

---

## 第四步：发送一笔测试交易

### 4.1 发送交易

1. 在 MetaMask 点击 "发送"
2. 收款地址：输入你自己的地址（发给自己，测试用）
3. 金额：输入 0.01（很小的金额）
4. 点击 "下一步"
5. 查看 Gas 费估算
6. 点击 "确认"

### 4.2 等待确认

- 交易会出现在 "活动" 标签页
- 等待 15-30 秒，交易状态变为 "已确认"
- 点击交易详情，可以看到交易哈希

### 4.3 在区块浏览器查看

1. 在交易详情中，点击 "在区块浏览器上查看"（或直接访问 [Sepolia Etherscan](https://sepolia.etherscan.io/))
2. 搜索你的交易哈希
3. **记录以下信息**：
   - 交易哈希（TxHash）
   - 状态（Status）：应为 Success
   - 区块高度（Block）
   - Gas Used
   - Gas Price

---

## 第五步：用 Remix 部署智能合约

### 5.1 打开 Remix IDE

1. 访问 [Remix IDE](https://remix.ethereum.org/)
2. 等待加载完成（可能需要 30 秒）

### 5.2 创建合约文件

1. 在左侧文件浏览器，点击 "新建文件"
2. 命名为 `SimpleStorage.sol`
3. 粘贴以下代码：

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleStorage {
    // 状态变量
    uint256 private storedValue;
    address public owner;

    // 事件
    event ValueChanged(address indexed updater, uint256 newValue);

    // 构造函数
    constructor() {
        owner = msg.sender;
    }

    // 写入函数
    function set(uint256 x) public {
        storedValue = x;
        emit ValueChanged(msg.sender, x);
    }

    // 读取函数
    function get() public view returns (uint256) {
        return storedValue;
    }

    // 获取所有者
    function getOwner() public view returns (address) {
        return owner;
    }
}
```

### 5.3 编译合约

1. 点击左侧 "Solidity 编译器" 图标（第二个）
2. 确认编译器版本为 0.8.x
3. 点击 "编译 SimpleStorage.sol"
4. 确认没有错误（绿色勾）

### 5.4 部署合约

1. 点击左侧 "部署并运行交易" 图标（第三个）
2. 环境选择 "Injected Provider - MetaMask"
3. MetaMask 会弹窗连接请求，点击 "下一步" → "连接"
4. 确认账户是你的 Sepolia 账户
5. 合约选择 "SimpleStorage"
6. 点击 "部署"
7. MetaMask 弹窗确认交易，点击 "确认"
8. 等待 15-30 秒

### 5.5 记录部署结果

1. 部署成功后，在 Remix 底部控制台会显示合约地址
2. 点击合约地址，跳转到 Etherscan
3. **记录以下信息**：
   - 合约地址
   - 部署交易哈希
   - 区块高度

---

## 第六步：与合约交互

### 6.1 读取合约

1. 在 Remix 的 "已部署合约" 部分，展开你的合约
2. 点击 "get" 按钮
3. 应返回 0（初始值）

### 6.2 写入合约

1. 在 "set" 输入框输入一个数字（如 42）
2. 点击 "transact"
3. MetaMask 弹窗确认，点击 "确认"
4. 等待交易确认

### 6.3 验证写入

1. 再次点击 "get"
2. 应返回 42

### 6.4 记录交易

1. 在 Etherscan 查看 set 交易
2. **记录交易哈希和状态**

---

## 实验记录

### 钱包信息

- 钱包地址：`0x__________________`
- 网络：Sepolia 测试网

### 测试币

- 来源：（Faucet 名称）
- 到账金额：______ SepoliaETH
- 到账时间：______

### 测试交易

- 交易哈希：`0x__________________`
- 状态：______
- 区块高度：______
- Gas Used：______
- Etherscan 链接：`https://sepolia.etherscan.io/tx/0x...`

### 智能合约部署

- 合约地址：`0x__________________`
- 部署交易哈希：`0x__________________`
- 区块高度：______
- Etherscan 链接：`https://sepolia.etherscan.io/address/0x...`

### 合约交互

- set(42) 交易哈希：`0x__________________`
- get() 返回值：______
- Etherscan 链接：`https://sepolia.etherscan.io/tx/0x...`

### 遇到的问题

> 记录你遇到的问题和解决方法...

---

## 常见问题

**Q: Faucet 提示需要 GitHub 账号？**
A: 正常，大部分 Faucet 需要 GitHub 登录防止滥用。

**Q: 交易一直 pending？**
A: 可能是 Gas 费太低，等一等或尝试取消交易重发。

**Q: Remix 连接 MetaMask 失败？**
A: 确认 MetaMask 已解锁，且网络为 Sepolia。

**Q: 合约部署失败？**
A: 检查余额是否足够（需要 Gas 费），检查代码是否编译通过。

---

*Created: 2026-05-26*
