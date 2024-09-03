
### 简单题
1. 私有、内部、公共和外部函数之间的区别？
2. 智能合约大小大约可以有多大？
3. create 和 create2 之间有什么区别？
4. Solidity 0.8.0 版本对算术运算有什么重大变化？
5. 代理需要哪种特殊的 CALL 才能工作？
6. 在 EIP-1559 之前，如何计算以太坊交易的美元成本？
7. 在区块链上创建随机数的挑战是什么？
8. 荷兰式拍卖和英式拍卖之间有什么区别？
9. ERC20 中的 transfer 和 transferFrom 之间有什么区别？
10. 对于地址 allowlist，使用映射还是数组更好？为什么？
11. 为什么不应该使用 tx.origin 进行身份验证？
12. 以太坊主要使用什么哈希函数？
13. 1 个Ether 相当于 多少个 gwei ？
1 个Ether 相当于 多少个 wei ？
assert 和 require 之间有什么区别？
什么是闪电贷？
什么是检查效果（ check-effects ）模式？
运行独立验证节点所需的最小以太数量是多少？
fallback 和 receive 之间有什么区别？
什么是重入？
上海升级后，每个区块的 gas 限制是多少？
什么阻止无限循环永远运行？
tx.origin 和 msg.sender 之间有什么区别？
如何向没有payable 函数、receive 或回退的合约发送以太？
view 和 pure 之间有什么区别？
ERC721 中的 transferFrom 和 safeTransferFrom 之间有什么区别？
如何将 ERC1155 代币转换为非同质化代币？
访问控制是什么，为什么重要？
修饰符（modifier）的作用是什么？
uint256 可以存储的最大值是多少？
什么是浮动利率和固定利率？
中等难度
transfer 和 send 之间有什么区别？为什么不应该使用它们？
如何在 Solidity 中编写高效的 gas 循环？
代理合约中的存储冲突是什么？
abi.encode 和 abi.encodePacked 之间有什么区别？
uint8、uint32、uint64、uint128、uint256 都是有效的 uint 大小。还有其他的吗？
在权益证明之前后，block.timestamp 发生了什么变化？
什么是抢跑（frontrunning）？
什么是提交-揭示方案，何时使用它？
在什么情况下，abi.encodePacked 可能会产生漏洞？
以太坊如何确定 EIP-1559 中的 BASEFEE？
冷读（cold read）和热读（warm read）之间有什么区别？
AMM 如何定价资产？
代理中的函数选择器冲突是什么，它是如何发生的？
payable 函数对 gas 的影响是什么？
什么是签名重放攻击？
什么是 gas griefing ？
如何设计一个石头-剪刀-布的智能合约游戏，使玩家无法作弊？
自由内存指针是什么，它存储在哪里？
接口中有效的函数修饰符有哪些？
函数参数中的 memory 和 calldata 有什么区别？
描述三种存储 gas 成本类型。
为什么可升级合约不应该使用构造函数？
UUPS 和 Transparent Upgradeable Proxy 模式之间有什么区别？
如果合约通过 delegatecall 调用一个空地址或之前已自毁的实现，会发生什么？如果是常规调用而不是 delegatecall 呢？
ERC777 代币存在什么危险？
根据 Solidity 风格指南，函数应该如何排序？
根据 Solidity 风格指南，函数修饰符应该如何排序？
什么是债券曲线(bonding curve)？
OpenZeppelin ERC721 实现中的 safeMint 与 mint 有何不同？
Solidity 提供哪些关键字来测量时间？
什么是三明治(sandwich)攻击？
如果向一个会回滚的函数进行 delegatecall，delegatecall 会怎么做？
乘以和除以二的倍数的 gas 高效替代方法是什么？
多大 uint 可以与一个地址在一个槽中？
哪些操作会部分退还 gas？
ERC165 作用于什么？
如果代理对 A 进行 delegatecall，而 A 执行 address(this).balance，返回的是代理的余额还是 A 的余额？
滑点参数有什么用？
ERC721A 如何减少铸造成本？有什么权衡？
为什么 Solidity 不支持浮点数运算？
什么是 TWAP？
Compound Finance 如何计算利用率？
有难度题
定点算术如何表示数字？
什么是 ERC20 授权抢跑攻击？
什么操作码可以实现 address(this).balance？
一个 Solidity 事件可以有多少个参数？
什么是匿名 Solidity 事件？
在什么情况下，函数可以接收映射作为参数？
ERC4626 中的通胀攻击是什么？
一个 Solidity 函数可以有多少个参数？
uint64[] x = [1,2,3,4,5] 使用了多少个存储槽？与内存有何不同？
上海升级之前，在什么情况下，returndatasize() 比 push zero 更有效？
为什么编译器会在 Solidity 合约中插入 INVALID 操作码？
自定义错误和带错误字符串的 require 在 EVM 层面编码有什么区别？
Compound DeFi 公式中的 kink 参数是什么？
函数名称如何影响 gas 成本，如果有的话？
ecrecover 存在什么常见漏洞？
乐观 Rollup 和 zk-rollup 之间有什么区别？
EIP1967 如何选择存储槽，有多少个存储槽，它们代表什么？
1 个 Sazbo 价值多少？
delegatecall 除了在代理中使用之外还可以用于什么？
在什么情况下，一个在以太坊上运行的智能合约在 Polygon 或 Optimism 上无法运行？（假设没有依赖于外部合约）
智能合约如何在不更改地址的情况下改变其字节码？
在循环中将 msg.value 放入有什么危险？
描述一个函数 calldata，该函数接受一个动态长度的 uint128 数组作为参数，当传递 uint128[1,2,3,4] 作为参数时会发生什么
为什么严格的不相等比较比 ≤ 或 ≥ 更节省 gas？额外的操作码是什么？
如果代理调用一个实现，并且在被调用的函数中实现自毁，会发生什么？
变量作用域和堆栈深度之间有什么关系？
访问列表交易是什么？
如何使用 mload 操作码终止执行？
在代理的上下文中，什么是信标（beacon）？
为什么在进行治理投票之前需要对余额进行快照？
如何执行一个不需要用户支付 gas 的交易？
在 Solidity 中，不使用汇编，如何获取 calldata 的函数选择器？
以太坊地址是如何派生的？
什么是元代理标准？
如果 try catch 调用一个不会回滚的合约，但在 try 块内发生回滚，会发生什么？
如果用户调用代理并使代理进行 delegatecall 到 A，A 从其角度来看，msg.sender 是谁？从 B 的角度来看，msg.sender 是谁？从代理的角度来看，msg.sender 是谁？
为什么大量合约字节码以 6080604052 开头？这个字节码序列是做什么的？
Uniswap V3 如何确定流动性区间的边界？
什么是无风险利率？
当一个合约通过 call、delegatecall 或 staticcall 调用另一个合约时，它们之间如何传递信息？
内存中的 bytes 和 bytes1[] 之间有什么区别？
高难度题
以太坊预编译合约的地址是什么？
当函数数量超过 4 个时，Solidity 如何管理函数选择器？
如果对一个合约进行委托调用，而该合约又对另一个合约进行委托调用，那么在代理合约、第一个合约和第二个合约中，msg.sender 是谁？
如果有的话，ABI 编码在 calldata 和 memory 之间有何不同？
uint64 和 uint256 在 calldata 中的 ABI 编码有何不同？
什么是只读重入？
从不受信任的智能合约调用中读取（内存）字节数组的安全考虑是什么？
如果部署一个空的 Solidity 合约，在区块链上会有什么字节码，如果有的话？
以太虚拟机如何定价内存使用？
智能合约的元数据部分存储了什么？
从 MEV 的角度来看，什么是叔块攻击？
如何进行签名篡改攻击（malleability attack）？
在什么情况下，具有前导零的地址可以节省 gas，以及为什么？
payable(msg.sender).call{value: value}("")和 msg.sender.call{value: value}("")之间有什么区别？
一个字符串占用多少个存储槽？
Solidity 编译器中的--via-ir 功能是如何工作的？
函数修饰符是从右到左调用还是从左到右调用，还是不确定的？
如果对一个合约进行委托调用，而执行了指令 CODESIZE，将返回哪个合约的大小？
为什么 ECDSA 对哈希而不是任意 bytes32 进行签名很重要
描述符号操作测试( symbolic manipulation testing)是如何工作的。
复制内存区域的最有效方式是什么？
如何在链上验证另一个智能合约是否触发了一个事件，而不使用预言机？
当调用 selfdestruct 时，以太何时转移？智能合约的字节码何时被擦除？
在什么条件下，Openzeppelin 的 Proxy.sol 会覆盖自由内存指针？为什么这样做是安全的？
为什么 Solidity 废弃了"years"关键字？
verbatim 关键字的作用是什么，以及它可以在哪里使用？
在调用另一个智能合约时可以转发多少 gas？
存储 -1 的 int256 变量在十六进制中是什么样子的？
signextend 操作码有什么用？
为什么 calldata 中的负数会消耗更多的 gas？
什么是 zk-friendly 哈希函数，它与非 zk-friendly 哈希函数有何不同？
在零知识的背景下，什么是 nullifier，它的用途是什么？
