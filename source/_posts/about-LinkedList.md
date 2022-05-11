---
title: 単方向LinkedListを反転する
date: 2022-01-05 21:25:00
tags: アルゴリズム
categories: アルゴリズム
comment: true
---

### 単方向 Linked List ってなに？

基本的なデータ構造の一つである線形リスト（linear linked list）のうち、
各要素が自分の「次」の要素へのリンクを持ち、
先頭側から末尾側へのみたどっていくことができるもの。

#### 例

[1 -> 2 -> 3 -> 4 ]

### 重要点

- 各要素が次の要素へ指している。
- 一番後ろの要素は null に指している。
- 一番目の要素だけが渡されることが多い。

### LinkedList のオブジェクトはどうやって定義する？

```java
 class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}
```

### LinkedList の反転

#### 目的：[1 -> 2 -> 3 ] => [3 -> 2 -> 1]

#### 手順：

1. 一番目の要素の next を覚える。 つまり、[2]を臨時で保存する。[1 -> 2 -> 3 -> null]
2. 一番目の要素は最後の要素 [1] になるので、null へポインタすべき。[null <- 1 2 -> 3 -> null]
3. 最後の要素 [1] は [2] に対して、next になるべき。[null <- 1 <- 2 3 -> null ]
4. 上記 1,2,3 でループし、head が null になったら停止。

#### サンプルコード

```java
//[1,2,3] -> [3,2,1]
public ListNode solution(ListNode head){
  ListNode prev = null;
  while(head != null){
    ListNode next = head.next;
    head.next = prev;
    prev = head;
    head = next;
 }
    return prev;
}
```
