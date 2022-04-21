这是跟着代码随想录的顺序学习算法的第？天。（二刷）

以下是学习时自己的一些理解与笔记，如有错误欢迎指正与讨论。

<br/>

# 剑指 Offer 58 - II. 左旋转字符串

参考相关链接：

[剑指 Offer 58 - II. 左旋转字符串](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

[代码随想录](https://www.programmercarl.com/%E5%89%91%E6%8C%87Offer58-II.%E5%B7%A6%E6%97%8B%E8%BD%AC%E5%AD%97%E7%AC%A6%E4%B8%B2.html)

<br/>

# 笔记

题目不难，但是用几种不同的方法来实现就变得有意思起来。

### 使用额外空间

```js
// 剪切粘贴
var reverseLeftWords = function(s, n) {
    s = [...s];
    return s.concat(s.splice(0, n)).join('');
};

// 固定指针，拼接字符串
var reverseLeftWords = function(s, n) {
    const length = s.length;
    let i = 0;
    while (i < length - n) {
        s = s[length - 1] + s;
        i++;
    }
    return s.slice(0, length);
};
```

### 不使用额外空间

```javascript
// 不使用额外空间
var reverseLeftWords = function(s, n) {
    s = [...s];
    // 前面字符反转
    let l = -1, r = n;
    while(++l < --r) [s[l], s[r]] = [s[r], s[l]]; 
	// 后面字符反转
    l = n - 1, r = s.length;
    while(++l < --r) [s[l], s[r]] = [s[r], s[l]]; 
    // 全部字符反转 
    l = -1, r = s.length;
    while(++l < --r) [s[l], s[r]] = [s[r], s[l]]; 
    return s.join('');
};
```





