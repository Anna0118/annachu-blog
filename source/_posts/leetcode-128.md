---
title: Leetcode [128. Longest Consecutive Sequence]
date: 2024-04-16 14:25:39
tags: 
    - leetcode
---

使用者的日常打卡數據不只是一些數字，它們透露了用戶的行為模式和參與程度。
如果計算出連續打卡的最長天數，也許能指引我們開發出更有效的激勵策略...

<!-- more -->

<img src="https://i.imgur.com/sY2ZBvn.jpeg" width="70%" height="50%">
<br>

刷題時心中總有個 OS : 這些演算法和數據結構在實際工作中真的會用到嗎？

這篇將帶你用情境來了解題目！


{% callout info %}
[128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/description/)
🧡 Medium
Topics: `Array` `HashTable` `UnionFind`
{% endcallout %}

#### 解題思路 :

假設數據是一系列表示使用者打卡日的日期時，這些日期是在一年的範圍內（即365天），最直觀的方法可能是對日期進行排序，然後逐一檢查來確定連續的最長天數。

確實這是一個很好的開始，因為它讓我們能夠直接看到日期之間的間隔。不過這種方法的時間複雜度為 `O(n log n)`，主要是由於排序步驟的需求。對於特別大的數據集，這可能會變得效率低下。

題目指出需要使用 `O(n)` 的方法來解決這一問題。請我們寫出一種更為高效的方法，讓整體處理的時間複雜度線性增長。這樣就可以更快地得到結果，且不會隨數據量的增加而顯著增加計算時間。

<hr>

#### 思考步驟 :
1. 先檢查陣列是否為空值和去除重複元素
2. 假設當前連續長度為 1 (至少陣列會有一個元素)
3. 遍歷陣列內的元素，開始計算連續序列長度
4. 檢查並更新最終的連續序列長度
5. 返回最大連續序列長度

#### 解題程式碼 :

```python
def longestConsecutive(nums):
    # 如果列表為空，則返回0
    if not nums:
        return 0

    # 使用集合去除重複元素
    nums_set = set(nums)

    # 初始化變數
    max_length = 0

    # 遍歷集合中的每個數字
    # {0,3,7,2,5,8,4,6,1}
    for num in nums_set:
        # 檢查是否可以將當前數字作為連續序列的起點
        # 假設 0 -1 = -1，而 -1 不在陣列
        if num - 1 not in nums_set:
            current_num = num
            current_length = 1

            # 持續檢查後續數字是否存在，就可開始建立連續序列
            while current_num + 1 in nums_set:
                current_num += 1
                current_length += 1

            # 更新找到的最長連續序列長度
            max_length = max(max_length, current_length)

    # 返回最長連續序列的長度
    return max_length

# 假設打卡數據
user_data = [0,3,7,2,5,8,4,6,0,1] // Output: 9

```
<hr>

除了 Social Media 情境外，還有一些情境也存在：

- 醫療: 追蹤病人的連續治療日或藥物使用日，也許可作為病情監控和治療效果的評估指標。

- 金融: 分析股票或其他金融產品的連續上漲或下跌天數可以幫助投資者做出一些決策。

- 教育: 分析學生的連續學習天數，可以幫助教育者評估學生的學習習慣和課程的吸引力。
