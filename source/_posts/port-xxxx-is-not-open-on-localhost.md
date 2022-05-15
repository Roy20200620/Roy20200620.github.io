---
title: port xxxx is not open on localhostが発生した場合の解消法
date: 2022-05-15 21:42:42
tags: node.js
categories: hints
comment: true
---
## 原因

port xxxx が既に利用されているため、該当ポートに他のスレッドが起動できないのは原因です。


## 解決方法
1. 該当ポートに何が使われているのを確認する。`{xxxx}`は確認したいポート番号を書き替えてください。
```bash
sudo lsof -i:{xxxx}
```
- 該当ポートが利用されていない場合、何も表示ないです。
- 該当ポートが利用されている場合、以下のように情報が表示されます。
{% asset_img lsof_image.png%}

2. 該当ポートをキールする。`{PID}`はキールしたいPIDを指定してください。
```bash 
kill {PID}
```

3. 再度手順１のコマンドを叩いて、成功した場合、ターミナルには何も出力しないです。
