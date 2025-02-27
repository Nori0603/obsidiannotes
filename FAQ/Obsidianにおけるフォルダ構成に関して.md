---
tags:
  - obsidian設定
datetimeCreate: 2025-02-27 07:39
---

### Complete Notes

本記事のように、外部公開することを前提に・または外部公開してもよいクオリティで書き上げられたノート。

### FAQ

キーボードが繁体字から戻らなくなった、Noxのインストールに失敗してしまう、などの「詰まり」への解答。  
ノートのタイトルは基本的に「～する方法」とか、「～の場合にやること」などわかりやすい形式にしておく。

### Archive

ほぼ見なくなったファイルなどのたまり場。いずれ空っぽにすべきゴミ箱候補。

### res

Obsidian内の画像やその他ノートではないファイルを収容するためのフォルダ。

### Web Clip

Advanced URIでWebから取得したマークダウンを保管する場所。





```dataviewjs
dv.header(3, "関連ノート");
var maxLoop = Math.min(dv.current().file.tags.length, 3);
for(let i=0;i<maxLoop;i++){
dv.span(dv.current().file.tags[i]);
dv.list(dv.pages(dv.current().file.tags[i]).sort(f=>f.file.mtime.ts,"desc").limit(15).file.link);
}

for (let outgo of dv.pages('outgoing([[' + dv.current().file.name + ']])')) {
    dv.header(4, outgo.file.name);
    dv.list(outgo.file.inlinks.sort());
}
```