# 映射

映射记录的是一种关系，语法 mapping(keyType => valueType)
keyType 必须是内置类型（包括bytes, string, contract等），不能是自定义的结构体等
valueType 可以是任何类型，包括结构体、另一个映射等

``` js
contract Mapping {
    mapping(address => uint) public myMap;

    function get(address _addr) public view returns (uint) {
        return myMap[_addr];
    }

    function set(address _addr, uint _i) public {
        myMap[_addr] = _i;
    }
}

contract NestedMapping {
    // mapping 作为 valueType
    mapping(address => mapping(uint => bool)) public nested;
}
```