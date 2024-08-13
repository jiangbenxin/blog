### 01-HelloWorld
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.21;
contract HelloWeb3{
    string public _string = "Hello Web3!";
}
```
### 02-值类型

布尔值
```
    bool public _bool = true;
    // 布尔运算
    bool public _bool1 = !_bool; //取非
    bool public _bool2 = _bool && _bool1; //与
    bool public _bool3 = _bool || _bool1; //或
    bool public _bool4 = _bool == _bool1; //相等
    bool public _bool5 = _bool != _bool1; //不相等

```
整数
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
地址
```
    address public _address = 0x7A58c0Be72BE218B41C608b7Fe7C5bB630736C71;
    address payable public _address1 = payable(_address); // payable address，可以转账、查余额
    // 地址类型的成员
    uint256 public balance = _address1.balance; // balance of address

    // 固定长度的字节数组
    bytes32 public _byte32 = "MiniSolidity"; // bytes32: 0x4d696e69536f6c69646974790000000000000000000000000000000000000000
    bytes1 public _byte = _byte32[0]; // bytes1: 0x4d
 ```
Enum
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
### 03-函数类型
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

pure: 纯纯牛马
    
```
    function addPure(uint256 _number) external pure returns(uint256 new_number){
        new_number = _number+1;
    }
```
view: 看客
```
    function addView() external view returns(uint256 new_number) {
        new_number = number + 1;
    }
```
internal: 内部函数
```
    function minus() internal {
        number = number - 1;
    }
```
 合约内的函数可以调用内部函数
```
    function minusCall() external {
        minus();
    }
```
payable: 递钱，能给合约支付eth的函数
```
    function minusPayable() external payable returns(uint256 balance) {
        minus();    
        balance = address(this).balance;
    }
```
### 04-函数
返回多个变量
```
    function returnMultiple() public pure returns(uint256, bool, uint256[3] memory){
        return(1, true, [uint256(1),2,5]);
    }
```
命名式返回
```
    function returnNamed() public pure returns(uint256 _number, bool _bool, uint256[3] memory _array){
        _number = 2;
        _bool = false; 
        _array = [uint256(3),2,1];
    }
```
命名式返回，依然支持return
```
    function returnNamed2() public pure returns(uint256 _number, bool _bool, uint256[3] memory _array){
        return(1, true, [uint256(1),2,5]);
    }
```

读取返回值，解构式赋值
```
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
```
### 05-变量数据储存和作用域
```
 // The data location of x is storage.
    // This is the only place where the
    // data location can be omitted.
    uint[] public x = [1,2,3];
```
storage
```
    function fStorage() public{
        //声明一个storage的变量xStorage，指向x。修改xStorage也会影响x
        uint[] storage xStorage = x;
        xStorage[0] = 100;
    }
```
memory
```
    function fMemory() public view{
        //声明一个Memory的变量xMemory，复制x。修改xMemory不会影响x
        uint[] memory xMemory = x;
        xMemory[0] = 100;
        xMemory[1] = 200;
        uint[] memory xMemory2 = x;
        xMemory2[0] = 300;
    }
```
calldata
```
    function fCalldata(uint[] calldata _x) public pure returns(uint[] calldata){
        //参数为calldata数组，不能被修改
        // _x[0] = 0 //这样修改会报错
        return(_x);
    }
uint public x = 1;
    uint public y;
    string public z;
```
状态变量
```
    function foo() external{
        // 可以在函数里更改状态变量的值
        x = 5;
        y = 2;
        z = "0xAA";
    }
```
局部变量
```
    function bar() external pure returns(uint){
        uint xx = 1;
        uint yy = 3;
        uint zz = xx + yy;
        return(zz);
    }
```
全局变量
```
    function global() external view returns(address, uint, bytes memory){
        address sender = msg.sender;
        uint blockNum = block.number;
        bytes memory data = msg.data;
        return(sender, blockNum, data);
    }
```
以太单位
```
    function weiUnit() external pure returns(uint) {
        assert(1 wei == 1e0);
        assert(1 wei == 1);
        return 1 wei;
    }

    function gweiUnit() external pure returns(uint) {
        assert(1 gwei == 1e9);
        assert(1 gwei == 1000000000);
        return 1 gwei;
    }

    function etherUnit() external pure returns(uint) {
        assert(1 ether == 1e18);
        assert(1 ether == 1000000000000000000);
        return 1 ether;
    }
```
时间单位
```
    
    function secondsUnit() external pure returns(uint) {
        assert(1 seconds == 1);
        return 1 seconds;
    }

    function minutesUnit() external pure returns(uint) {
        assert(1 minutes == 60);
        assert(1 minutes == 60 seconds);
        return 1 minutes;
    }

    function hoursUnit() external pure returns(uint) {
        assert(1 hours == 3600);
        assert(1 hours == 60 minutes);
        return 1 hours;
    }

    function daysUnit() external pure returns(uint) {
        assert(1 days == 86400);
        assert(1 days == 24 hours);
        return 1 days;
    }

    function weeksUnit() external pure returns(uint) {
        assert(1 weeks == 604800);
        assert(1 weeks == 7 days);
        return 1 weeks;
    }
```
### 06-引用类型
固定长度 Array
```
uint[8] array1;
bytes1[5] array2;
address[100] array3;
```
可变长度 Array
```
uint[] array4;
bytes1[] array5;
address[] array6;
bytes array7;
```
memory动态数组
```
uint[] memory array8 = new uint[](5);
bytes memory array9 = new bytes(9);
  
```
数组第一个要给类型
```
 function f() public pure {
        g([uint(1), 2, 3]);
    }
    function g(uint[3] memory _data) public pure {
        // ...
    }
```
如果创建的是动态数组，你需要一个一个元素的赋值
```
uint[] memory x = new uint[](3);
x[0] = 1;
x[1] = 3;
x[2] = 4;
 function arrayPush() public returns(uint[] memory){
        uint[2] memory a = [uint(1),2];
        array4 = a;
        array4.push(3);
        return array4;
    }
```
结构体 Struct
```
    struct Student{
        uint256 id;
        uint256 score; 
    }
    Student student; // 初始一个student结构体
    //  给结构体赋值
    // 方法1:在函数中创建一个storage的struct引用
    function initStudent1() external{
        Student storage _student = student; // assign a copy of student
        _student.id = 11;
        _student.score = 100;
    }

    // 方法2:直接引用状态变量的struct
    function initStudent2() external{
        student.id = 1;
        student.score = 80;
    }
    
    // 方法3:构造函数式
    function initStudent3() external {
        student = Student(3, 90);
    }

    // 方法4:key value
    function initStudent4() external {
        student = Student({id: 4, score: 60});
    }
```
转换
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
### 07-映射类型
映射Mapping
```
    mapping(uint => address) public idToAddress; // id映射到地址
    mapping(address => address) public swapPair; // 币对的映射，地址到地址
```
规则1：映射的_KeyType只能选择Solidity内置的值类型，比如uint，address等，不能用自定义的结构体。而_ValueType可以使用自定义的类型。下面这个例子会报错，因为_KeyType使用了我们自定义的结构体：  
```
// 我们定义一个结构体 Struct
struct Student{
    uint256 id;
    uint256 score; 
}
mapping(Student => uint) public testVar;
```
规则2：映射的存储位置必须是storage，因此可以用于合约的状态变量，函数中的storage变量和library函数的参数（见例子）。不能用于public函数的参数或返回结果中，因为mapping记录的是一种关系 (key - value pair)。  
规则3：如果映射声明为public，那么Solidity会自动给你创建一个getter函数，可以通过Key来查询对应的Value。  
规则4：给映射新增的键值对的语法为_Var[_Key] = _Value，其中_Var是映射变量名，_Key和_Value对应新增的键值对。例子  
```
function writeMap (uint _Key, address _Value) public{
    idToAddress[_Key] = _Value;
}
```
**映射的原理**  
原理1: 映射不储存任何键（Key）的资讯，也没有length的资讯。  
原理2: 映射使用keccak256(abi.encodePacked(key, slot))当成offset存取value，其中slot是映射变量定义所在的插槽位置。  
原理3: 因为Ethereum会定义所有未使用的空间为0，所以未赋值（Value）的键（Key）初始值都是各个type的默认值，如uint的默认值是0。
### 08-变量初始值
**值类型初始值**  
boolean: false
string: ""
int: 0
uint: 0
enum: 枚举中的第一个元素
address: 0x0000000000000000000000000000000000000000 (或 address(0))
function
internal: 空白函数
external: 空白函数
```
    bool public _bool; // false
    string public _string; // ""
    int public _int; // 0
    uint public _uint; // 0
    address public _address; // 0x0000000000000000000000000000000000000000
    
    enum ActionSet { Buy, Hold, Sell}
    ActionSet public _enum; // 第1个内容Buy的索引0
    
    function fi() internal{} // internal空白函数
    function fe() external{} // external空白函数 
```
**引用类型初始值**  
映射mapping: 所有元素都为其默认值的mapping
结构体struct: 所有成员设为其默认值的结构体
数组array
动态数组: []
静态数组（定长）: 所有成员设为其默认值的静态数组
```
// Reference Types
uint[8] public _staticArray; // 所有成员设为其默认值的静态数组[0,0,0,0,0,0,0,0]
uint[] public _dynamicArray; // `[]`
mapping(uint => address) public _mapping; // 所有元素都为其默认值的mapping
// 所有成员设为其默认值的结构体 0, 0
struct Student{
    uint256 id;
    uint256 score; 
}
Student public student;
```
delete操作符
```
// delete操作符
bool public _bool2 = true; 
function d() external {
    delete _bool2; // delete 会让_bool2变为默认值，false
}
```
### 09-常数
**constant变量必须在声明的时候初始化，之后再也不能改变。尝试改变的话，编译不通过。**
```
// constant变量必须在声明的时候初始化，之后不能改变
uint256 constant CONSTANT_NUM = 10;
string constant CONSTANT_STRING = "0xAA";
bytes constant CONSTANT_BYTES = "WTF";
address constant CONSTANT_ADDRESS = 0x0000000000000000000000000000000000000000;
```
**immutable变量可以在声明时或构造函数中初始化，因此更加灵活。在Solidity v8.0.21以后，immutable变量不需要显式初始化。反之，则需要显式初始化。 若immutable变量既在声明时初始化，又在constructor中初始化，会使用constructor初始化的值。**
```
// immutable变量可以在constructor里初始化，之后不能改变
uint256 public immutable IMMUTABLE_NUM = 9999999999;
address public immutable IMMUTABLE_ADDRESS;
uint256 public immutable IMMUTABLE_BLOCK;
uint256 public immutable IMMUTABLE_TEST;
```
**你可以使用全局变量例如address(this)，block.number 或者自定义的函数给immutable变量初始化。在下面这个例子，我们利用了test()函数给IMMUTABLE_TEST初始化为9**
```
// 利用constructor初始化immutable变量，因此可以利用
constructor(){
    IMMUTABLE_ADDRESS = address(this);
    IMMUTABLE_NUM = 1118;
    IMMUTABLE_TEST = test();
}

function test() public pure returns(uint256){
    uint256 what = 9;
    return(what);
}
```
### 10-控制流
if-else
```
function ifElseTest(uint256 _number) public pure returns(bool){
    if(_number == 0){
        return(true);
    }else{
        return(false);
    }
}
```
for循环
```
function forLoopTest() public pure returns(uint256){
    uint sum = 0;
    for(uint i = 0; i < 10; i++){
        sum += i;
    }
    return(sum);
}
```
while循环
```
function whileTest() public pure returns(uint256){
    uint sum = 0;
    uint i = 0;
    while(i < 10){
        sum += i;
        i++;
    }
    return(sum);
}
```
do-while循环
```
function doWhileTest() public pure returns(uint256){
    uint sum = 0;
    uint i = 0;
    do{
        sum += i;
        i++;
    }while(i < 10);
    return(sum);
}
```
三元运算符
```
// 三元运算符 ternary/conditional operator
function ternaryTest(uint256 x, uint256 y) public pure returns(uint256){
    // return the max of x and y
    return x >= y ? x: y; 
}
```
用Solidity实现插入排序
```
// 插入排序 正确版
function insertionSort(uint[] memory a) public pure returns(uint[] memory) {
    // note that uint can not take negative value
    for (uint i = 1;i < a.length;i++){
        uint temp = a[i];
        uint j=i;
        while( (j >= 1) && (temp < a[j-1])){
            a[j] = a[j-1];
            j--;
        }
        a[j] = temp;
    }
    return(a);
}
```
### 11-构造函数
constructor每个合约可以定义一个，并在部署合约的时候自动运行一次。它可以用来初始化合约的一些参数
```
address owner; // 定义owner变量

// 构造函数
constructor(address initialOwner) {
    owner = initialOwner; // 在部署合约的时候，将owner设置为传入的initialOwner地址
}
```
构造函数的旧写法代码示例：
```
pragma solidity =0.4.21;
contract Parents {
    // 与合约名Parents同名的函数就是构造函数
    function Parents () public {
    }
}
```
修饰器
```
// 定义modifier
modifier onlyOwner {
   require(msg.sender == owner); // 检查调用者是否为owner地址
   _; // 如果是的话，继续运行函数主体；否则报错并revert交易
}
```
带有onlyOwner修饰符的函数只能被owner地址调用，比如下面这个例子：
```
function changeOwner(address _newOwner) external onlyOwner{
   owner = _newOwner; // 只有owner地址运行这个函数，并改变owner
}
```
### 12
声明事件
```
event Transfer(address indexed from, address indexed to, uint256 value);
```
释放事件
```
// 定义_transfer函数，执行转账逻辑
function _transfer(
    address from,
    address to,
    uint256 amount
) external {

    _balances[from] = 10000000; // 给转账地址一些初始代币

    _balances[from] -=  amount; // from地址减去转账数量
    _balances[to] += amount; // to地址加上转账数量

    // 释放事件
    emit Transfer(from, to, amount);
}
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
