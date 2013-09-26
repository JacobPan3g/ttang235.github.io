---
layout: post
title: 判断一个数n的二进制表达的最高非0位的位置
categories: algorithm
---
一个简单的想法就是每次向右移一位，然后判断是否为0，同时记录移动的次数，这个算法的复杂度与待判断的这个数n有关，是<span>$O(log_2n)$</span>，需要移动的次数越多。不过，可以采用二分查找的思想，比如对一个32位int型变量（正数），可以先右移16位（mid point），判断得到的数是否大于0，然后在缩小的范围里继续查找。代码如下：

```c++
int find_bits(int n){//假设n为正数，即二进制表示最高位为0，且至少有一个1
	//返回n的二进制表示的位数，leading zeros are ignored
	//采用二分的移位
	int left = 31, right = 1;//至少移1位，至多31位,左边是高位
	while (left > right) {
		int mid = (left + right) / 2;
		if ((n >> mid) > 0) {
			right = mid + 1;
		} else {
			left = mid;
		}
	}
	return left;
}
```

对这个问题，不知道有没有常数时间的算法，比如通过巧妙的与、或、非操作，如果你知道，可以告诉我～
