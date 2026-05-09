---
tags:
  - dp
  - notes
date: 2026-05-09
---

## 一、區間 DP（Interval DP）

### 1. 核心概念
區間 DP 的狀態通常定義為：

```
dp[i][j] = 區間 (i, j) 的最佳解
```

重點：
- 狀態本身是一段「連續區間」
- 子問題也是區間
- 通常透過枚舉分割點 k 轉移

---

### 2. 經典轉移形式

```
dp[i][j] = max/min over k in (i, j):
    dp[i][k] + dp[k][j] + cost(i, k, j)
```

特徵：
- 左右子區間彼此獨立
- 結構是「二維區間樹」
- 通常需要依區間長度遞增填表

---

### 3. 常見題型
- 矩陣鏈乘（Matrix Chain Multiplication）
- Burst Balloons
- Remove Boxes
- Minimum Cost to Cut a Stick
- Stone Game 類型

---

### 4. 思考核心
區間 DP 常用技巧：

👉 固定「最後一步」
👉 枚舉最後被處理的 k
👉 讓左右區間先完成

這樣可以保證子問題互相獨立。

---

### 5. 標準模板

```
for length in range(1, n):
    for i in range(n - length):
        j = i + length
        for k in range(i+1, j):
            dp[i][j] = max(
                dp[i][j],
                dp[i][k] + dp[k][j] + cost
            )
```

時間複雜度通常為 O(n^3)。

---

## 二、劃分 DP（Partition DP）

### 1. 核心概念
劃分 DP 通常是在線性結構上決定切點。

常見狀態：

```
dp[i] = 前 i 個元素的最佳解
```

或

```
dp[i][k] = 前 i 個元素，分成 k 段的最佳解
```

---

### 2. 經典轉移形式

```
dp[i] = min/max over k < i:
    dp[k] + cost(k, i)
```

特徵：
- 子問題是「前綴」
- 結構是單向 DAG
- 每次決定一個切點

---

### 3. 常見題型
- Split Array Largest Sum
- Palindrome Partitioning II
- Perfect Squares
- Minimum Number of Refueling Stops（部分解法）

---

### 4. 思考核心
劃分 DP 常見技巧：

👉 決定「最後一刀」
👉 枚舉切點 k
👉 子問題為前綴 dp[k]

---

### 5. 標準模板

```
for i in range(n):
    for k in range(i):
        dp[i] = min/max(
            dp[i],
            dp[k] + cost(k, i)
        )
```

時間複雜度通常為 O(n^2)。

---

## 三、區間 DP vs 劃分 DP 差異

| 比較項目 | 區間 DP | 劃分 DP |
|----------|----------|----------|
| 狀態定義 | dp[i][j] | dp[i] 或 dp[i][k] |
| 子問題 | 兩個區間 | 前綴 |
| 結構 | 二維區間樹 | 線性 DAG |
| 枚舉方式 | 枚舉區間內 k | 枚舉前綴切點 k |
| 經典轉移 | dp[i][k] + dp[k][j] | dp[k] + cost |
| 常見複雜度 | O(n^3) | O(n^2) |

---

## 四、快速判斷方法

如果問題是：

1. 在「連續區間」內做最佳化 → 區間 DP
2. 在「序列前綴」上決定切點 → 劃分 DP
3. 子問題是左右兩段 → 區間 DP
4. 子問題是單一路徑前綴 → 劃分 DP

---

## 五、練習建議

區間 DP 入門：

- [ ] [[312 - Burst Balloons]]
- [ ] [[1547 - Minimum Cost to Cut a Stick]]

劃分 DP 入門：
- [ ] [[410 - Split Array Largest Sum]]
- [ ] [[1278 - Palindrome Partitioning III]]

建議先熟練劃分 DP，再進階到區間 DP。
