# 创建合约

#### create
通过 new 创建新合约，并传入构造参数；如果构造函数 payable，创建时可以同时转入ETH
新合约地址 = hash( 创建者地址，nonce)
nonce随时间改变，因而创建的合约地址不好预测

``` js
    function create(address _owner, string memory _model) public {
        Car car = new Car(_owner, _model);
        cars.push(car);
    }

    function createAndSendEther(address _owner, string memory _model) public payable {
        Car car = (new Car){value: msg.value}(_owner, _model);
        cars.push(car);
    }
```

#### create2
由创建者指定偏移量，使新合约地址可预测
新合约地址 = hash( “0xFF”, 创建者地址, salt, bytecode)
- 0xFF：常数，避免和 create 冲突
- salt：创建者给定的数值
- bytecode：待部署合约的字节码

``` js
    function create2(address _owner, string memory _model, bytes32 _salt) public {
        Car car = (new Car){salt: _salt}(_owner, _model);
        cars.push(car);
    }

    function create2AndSendEther(
        address _owner,
        string memory _model,
        bytes32 _salt
    ) public payable {
        Car car = (new Car){value: msg.value, salt: _salt}(_owner, _model);
        cars.push(car);
    }
```


# 销毁合约

为了应对出错的极端情况，可以将合约销毁，但会降低用户对合约的信心
销毁时将清空变量，剩余ETH发送给 msg.sender
合约被销毁后也可以交互，返回值都是0

``` js
selfdestruct(_addr);
```