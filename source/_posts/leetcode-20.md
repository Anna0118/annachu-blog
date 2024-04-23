---
title: Leetcode [20. Valid Parentheses]
date: 2024-04-23 23:43:48
tags: stack
categories: Leetcode
---

有沒有遇過修了三天三夜的 bug，居然是少了一個括號 ! 無論是程式錯誤或是版面一直不對，幸好現在的IDE都能安裝強大的擴充套件...

<!-- more -->

![](https://i.imgur.com/QZTy09S.png)


{% callout info %}
[20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/description/)
💚 Easy
Topics: `String` `Stack`
{% endcallout %}

#### 解題思路

![我的解題思路手繪圖](https://i.imgur.com/pvcRGSS.png)

`s = "({}])"`

i = 0，`stack = ['(']`
i = 1，`stack = ['(', '{']`
i = 2 碰到 `}` 的時候，從 stack 檢查：

從 stack 的尾巴找到 `}` -> ✅ ，移除尾巴元素 `}`，但表有成對

i = 3 碰到 `]` 的時候，從 stack 檢查：

從 `stack = ['(']` 的尾巴找不到`]` -> ❌ 

<hr>

#### 解題步驟

遍歷陣列：
- 當遇到左括號時，將符號 append 到 Stack
- 當遇到右括號時，stack 尾巴是否存在對應的左括號
    - 存在：將左括號 pop 出來
    - 不存在：返回 `False`
- 檢查 stack 若為空陣列，返回 `True` ; 反之為 `False`

複雜度
  - 時間複雜度: O(N)
  - 空間複雜度: O(N)


#### 解題程式碼

```python
 def isValid(s):
   brackets ={"}":"{", "]":"[",")":"("}
   stacks=[]
   for char in s:
     if char in brackets.values():
       stacks.append(char)
     elif char in brackets:
       if stacks and brackets[char] == stacks[-1]:
         stacks.pop()
       else:
         return False
   return len(stacks)==0

```

<hr>

VS studio 乾貨分享：

- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - 自動整理程式碼格式，支援 JavaScript, CSS and JSON。

- [Ruff](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff) - 由 Rust 實作的 Python Linter, 號稱速度快上其他常見的 Linter 約 10 ~ 100 倍之間。
