### HelloWorld
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.21;
contract HelloWeb3{
    string public _string = "Hello Web3!";
}
```
### 01-值类型

#### 布尔值
```
    bool public _bool = true;
    // 布尔运算
    bool public _bool1 = !_bool; //取非
    bool public _bool2 = _bool && _bool1; //与
    bool public _bool3 = _bool || _bool1; //或
    bool public _bool4 = _bool == _bool1; //相等
    bool public _bool5 = _bool != _bool1; //不相等

```
#### 整数
```
    int public _int = -1;
    uint public _uint = 1;
    uint256 public _number = 20220330;
    // 整数运算
    uint256 public _number1 = _number + 1; // +，-，*，/
    uint256 public _number2 = 2**2; // 指数
    uint256 public _number3 = 7 % 2; // 取余数
    bool public _numberbool = _number2 > _number3; // 比大小
```
#### 地址
```
    address public _address = 0x7A58c0Be72BE218B41C608b7Fe7C5bB630736C71;
    address payable public _address1 = payable(_address); // payable address，可以转账、查余额
    // 地址类型的成员
    uint256 public balance = _address1.balance; // balance of address

    // 固定长度的字节数组
    bytes32 public _byte32 = "MiniSolidity"; // bytes32: 0x4d696e69536f6c69646974790000000000000000000000000000000000000000
    bytes1 public _byte = _byte32[0]; // bytes1: 0x4d
 ```
#### Enum
```
    // 将uint 0， 1， 2表示为Buy, Hold, Sell
    enum ActionSet { Buy, Hold, Sell }
    // 创建enum变量 action
    ActionSet action = ActionSet.Buy;

    // enum可以和uint显式的转换
    function enumToUint() external view returns(uint){
        return uint(action);
    }
```
### 02-函数类型
```
    uint256 public number = 5;
    
    constructor() payable {}
```
```
    // function (<parameter types>) {internal|external} [pure|view|payable] [returns (<return types>)]
    // 默认function
    function add() external{
        number = number + 1;
    }
```
    // pure: 纯纯牛马
```
    function addPure(uint256 _number) external pure returns(uint256 new_number){
        new_number = _number+1;
    }
```
    // view: 看客
```
    function addView() external view returns(uint256 new_number) {
        new_number = number + 1;
    }
```
    // internal: 内部函数
```
    function minus() internal {
        number = number - 1;
    }
```
    // 合约内的函数可以调用内部函数
```
    function minusCall() external {
        minus();
    }
```
    // payable: 递钱，能给合约支付eth的函数
```
    function minusPayable() external payable returns(uint256 balance) {
        minus();    
        balance = address(this).balance;
    }
```
### 03
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.21;

// 返回多个变量
// 命名式返回
// 解构赋值

contract Return {
    // 返回多个变量
    function returnMultiple() public pure returns(uint256, bool, uint256[3] memory){
        return(1, true, [uint256(1),2,5]);
    }

    // 命名式返回
    function returnNamed() public pure returns(uint256 _number, bool _bool, uint256[3] memory _array){
        _number = 2;
        _bool = false; 
        _array = [uint256(3),2,1];
    }

    // 命名式返回，依然支持return
    function returnNamed2() public pure returns(uint256 _number, bool _bool, uint256[3] memory _array){
        return(1, true, [uint256(1),2,5]);
    }

    // 读取返回值，解构式赋值
    function readReturn() public pure{
        // 读取全部返回值
        uint256 _number;
        bool _bool;
        bool _bool2;
        uint256[3] memory _array;
        (_number, _bool, _array) = returnNamed();
        
        // 读取部分返回值，解构式赋值
        (, _bool2, ) = returnNamed();
    }
}

```
### 04
```
```
### 05
```
```
### 06
```
```
### 07
```
```
### 08
```
```
### 09
```
```
### 10
```
```
### 11
```
```
### 12
```
```
### 13
```
```
### 14
```
```
### 15
```
```
### 16
```
```
### 17
```
```
### 18
```
```
### 19
```
```
### 20
```
```
### 21
```
```
### 22
```
```
### 23
```
```
### 24
```
```
### 25
```
```
### 26
```
```
### 27
```
```
### 28
```
```
