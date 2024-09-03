### [来自登链社区Solidity开发者应掌握的十个智能合约](https://www.learnblockchain.cn/article/6826) 
1. ERC-20 合约
去中心化金融的基础，ERC-20 代币标准是每个 Solidity 开发者必须了解的。它定义了一组规则，使得在以太坊网络上创建同质的代币成为可能。无论你计划发行自己的加密货币还是参与 DeFi 生态系统，这个合约都是必不可少的。

代码示例：
```
// ERC-20 Token Contract
contract ERC20Token {
    string public name;
    string public symbol;
    uint8 public decimals = 18;
    uint256 public totalSupply;

    mapping(address => uint256) public balanceOf;
    mapping(address => mapping(address => uint256)) public allowance;

    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);

    constructor(uint256 initialSupply, string memory tokenName, string memory tokenSymbol) {
        totalSupply = initialSupply * 10 ** uint256(decimals);
        balanceOf[msg.sender] = totalSupply;
        name = tokenName;
        symbol = tokenSymbol;
    }

    // Additional functions...
}
```
2. ERC-721 合约
非同质化代币（NFT）已经在数字世界中掀起了风暴。ERC-721 标准定义了创建这些独特、不可分割代币的规则。无论你对数字艺术、收藏品还是游戏资产感兴趣，ERC-721 合约是你的首选。

代码示例：
```
// ERC-721 Token Contract
contract ERC721Token {
    string public name;
    string public symbol;

    mapping(uint256 => address) public ownerOf;
    mapping(address => uint256) public balance;
    mapping(uint256 => address) public approved;

    event Transfer(address indexed from, address indexed to, uint256 tokenId);
    event Approval(address indexed owner, address indexed approved, uint256 tokenId);
    event ApprovalForAll(address indexed owner, address indexed operator, bool approved);

    function transferFrom(address from, address to, uint256 tokenId) external;
    function approve(address to, uint256 tokenId) external;
    
    // Additional functions...
}
```
3. 简单拍卖合约
你有想过在线拍卖如何在区块链上运作吗？一个简单的拍卖合约就是你的答案。竞标者可以争夺物品，在拍卖结束时最高出价者获胜。

代码示例：
```
// Simple Auction Contract
contract SimpleAuction {
    address public beneficiary;
    uint256 public auctionEndTime;

    address public highestBidder;
    uint256 public highestBid;

    mapping(address => uint256) public pendingReturns;

    bool public ended;

    event HighestBidIncreased(address bidder, uint256 amount);
    event AuctionEnded(address winner, uint256 amount);

    constructor(uint256 _biddingTime, address _beneficiary) {
        beneficiary = _beneficiary;
        auctionEndTime = block.timestamp + _biddingTime;
    }

    function bid() public payable;
    function withdraw() public returns (bool);
    function auctionEnd() public;
    
    // Additional functions...
}
```
4. 众筹合约
众筹已经被区块链技术革新。通过众筹合约，贡献者可以为一个共同的目标提供资金，当目标达成时，资金将释放给项目创建者。

代码示例：
```
// Crowdfunding Contract
contract Crowdfunding {
    address public creator;
    uint256 public goal;
    uint256 public endTime;
    mapping(address => uint256) public contributions;

    event FundingReceived(address contributor, uint256 amount);
    event GoalReached(uint256 totalAmount);
    event FundsWithdrawn(address creator, uint256 amount);

    constructor(uint256 _goal, uint256 _duration) {
        creator = msg.sender;
        goal = _goal;
        endTime = block.timestamp + _duration;
    }

    function contribute() public payable;
    function withdraw() public;
    
    // Additional functions...
}
```
5. 托管合约
在充满不确定性的世界中，托管合约提供了一种安全的方式来保留资金，直到满足预定义的条件。这个中立的第三方（托管合约）确保了各种交易的信任。

代码示例：
```
// Escrow Contract
contract Escrow {
    address public payer;
    address public payee;
    address public arbiter;

    function deposit() public payable;
    function release() public;
    function refund() public;
    
    // Additional functions...
}
```
6. 多签钱包合约
安全在区块链领域至关重要。多签名钱包需要多个参与方批准交易，提供了额外的保护层。

代码示例：
```
// Multisignature Wallet Contract
contract MultiSigWallet {
    address[] public owners;
    uint256 public requiredSignatures;

    mapping(address => bool) public isOwner;
    mapping(uint256 => Transaction) public transactions;
    uint256 public transactionCount;

    struct Transaction {
        address to;
        uint256 value;
        bytes data;
        bool executed;
    }

    event Deposit(address indexed sender, uint256 value);
    event Submission(uint256 indexed transactionId);
    event Confirmation(address indexed sender, uint256 indexed transactionId);
    event Execution(uint256 indexed transactionId);
    
    // Additional functions...
}
```
7. 投票合约
区块链上的民主！投票合约使用户能够对重要事项进行投票，所有结果都被不可变地记录在区块链上。

代码示例：
```
// Voting Contract
contract Voting {
    address[] public voters;
    mapping(address => bool) public hasVoted;
    mapping(string => uint256) public votes;

    event Voted(address indexed voter, string option);

    function vote(string memory option) public;
    
    // Additional functions...
}
```
8. 域名注册合约
去中心化域名是一个热门话题。域名注册合约允许用户为以太坊地址注册和管理可读性强的人类名称。

代码示例：
```
// Domain Name Registry Contract
contract DomainRegistry {
    mapping(string => address) public domainToOwner;
    mapping(address => string) public ownerToDomain;

    event DomainRegistered(address indexed owner, string domain);
    event DomainTransferred(address indexed from, address indexed to, string domain);

    function registerDomain(string memory domain) public;
    function transferDomain(address to, string memory domain) public;
    
    // Additional functions...
}
```
9. 预测市场合约
预测与区块链相遇，预测市场合约应运而生。用户可以购买和出售未来事件结果的股份，并根据现实世界的结果确定支付。

代码示例：
```
// Predictive Market Contract
contract PredictiveMarket {
    mapping(string => uint256) public outcomeShares;
    mapping(address => uint256) public balances;

    event MarketCreated(string question);
    event SharesPurchased(address indexed buyer, string outcome, uint256 shares);
    event MarketResolved(string outcome, uint256 totalShares);

    function createMarket(string memory question) public;
    function purchaseShares(string memory outcome, uint256 shares) public;
    function resolveMarket(string memory outcome) public;
    
    // Additional functions...
}
```
10. 游戏合约
准备构建下一个基于区块链的游戏或赌博平台了吗？游戏合约是你创建以太坊上去中心化游戏和娱乐的通行证。

代码示例：

```
// Gaming Contract
contract Game {
    address public owner;
    uint256 public pot;
    uint256 public outcome;
    uint256 public gameEndTime;

    event GameStarted(uint256 endTime);
    event GameEnded(uint256 outcome, uint256 winnings);

    function startGame(uint256 duration) public;
    function play(uint256 guess) public payable;
    function endGame(uint256 actualOutcome) public;
    
    // Additional functions...
}
```
