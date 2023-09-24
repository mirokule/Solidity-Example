# 接收ETH

声明为 **payable** 的函数、地址可以接收 ETH。
``` js
address payable public owner;

function deposit() public payable {}
```

接收 ETH 的函数**至少要有一个**，否则向该合约发送ETH时将报错：
- receive() external payable: 专门接收ETH的函数，msg.data必须为空，不需要function关键字，不能有参数、返回值
- fallback() external payable: 调用不存在的合约函数时触发，可以兼职接收ETH，不需要function关键字，可以处理msg.data不为空的情况

``` js
contract ReceiveEther {
    /*
    Which function is called, fallback() or receive()?

           send Ether
               |
         msg.data is empty?
              / \
            yes  no
            /     \
receive() exists?  fallback()
         /   \
        yes   no
        /      \
    receive()   fallback()
    */

    // Function to receive Ether. msg.data must be empty
    receive() external payable {}

    // Fallback function is called when msg.data is not empty
    fallback() external payable {}

    function getBalance() public view returns (uint) {
        return address(this).balance;
    }
}

```