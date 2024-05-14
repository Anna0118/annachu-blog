---
title: Leetcode [206. Reverse Linked List]
date: 2024-05-13 13:22:57
categories: Leetcode
---

實現反轉鏈

<!-- more -->

{%asset_img 1.png leetcode-206%}
<br>

{% callout info %}
[206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/description/)
💚 Easy
Topics: `Linked List` `Recursion`
{% endcallout %}


### 解題思路：iteratively

{%asset_img iteratively.png leetcode-206%}

**一步一步移動**

- 初始化指標
- 遍歷原始鏈表
- 反轉 (重點步驟)
- 更新指標位置
- 直到 ListNode 是空的

<br>


```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # 初始化
        prev=None
        # 將當前節點設為頭節點
        current=head
        # 當「當前節點」不為 None 時持續執行，None 表示已到達原鏈表尾
        while current:
            # 先儲存下一節點
            next_node=current.next
            # 接著將「當前節點」的 next 指向前一個節點，實現反轉
            current.next=prev
            # 更新位置，將 prev 移至當前節點，為了讓 prev 進到下一位置
            prev=current
            # 更新位置，將當前節點移動到 next_node，即向原鏈的尾部移動
            current=next_node
         # 當迴圈結束，prev 將指向新的頭節點（原鏈表的尾節點）
        return prev

# 時間複雜度：O(n)
# 空間複雜度：O(1)

```
