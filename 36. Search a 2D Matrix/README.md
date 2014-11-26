这道题看似很简单，擦，意外真多啊。

我 submit 了不下5次，几乎把各种边界用例都搜集全了。所以说，小到**二分查找算法**，都有无数坑等着你。

矩阵只是个幌子，这道题的本质还在于考察查找算法，你把矩阵变成一个更大的数组就行了（注意看题意中的两个属性，天然有序，二分查找）。

而在这个大矩阵(n*m)中，`pos[i]`的行恰是 `i/n`，列恰是 `i%n`。这就是本题的重点。

难点在于，怎么把控好不越界，怎么不需要重复判断一些条件。我觉得能够一次性把这道题写对的人，思维一定是超级严密的，可以去微软面试去了。

最后我的教训是: 不要把**标准的二分查找算法**往里面硬套，一定要结合具体情况微调。死用算法是大忌，切记。

这道题微调的地方在于，

```cpp
[1,2,3,4,5,6,7,8,9]
 ^       ^       ^
 low    mid     high
// find 3
[1,2,3,4,5,6,7,8,9]
 ^       ^
 low    mid
        high
```

注意 high 的位置，为了避免溢出，要让high == mid. 然后返回之际，只需判断 `pos[high] ?= target` 即可。