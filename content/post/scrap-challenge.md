+++
date = "2015-02-04T03:39:22+09:00"
title = "mixi主催のScrap Challengeに参加してきた"

+++

先日、mixi主催のScrap Challengeというイベントに参加してきた。Scrap
Challengeとはmixiが学生を対象として年に数回開催している、セキュリティ分野の
イベントだ。具体的には、あえてXSSやSQLインジェクションやCSRFなどの脆弱性を盛り込んだ
mixi SNSを攻撃し、提示された 課題を解いていく。開催に至るまでの成り行きなどは、
mixiの中の人の[ブログ記事](http://alpha.mixi.co.jp/entry/2014/10/29/135814)が
詳しい。

<!--more-->

### イベント風景

まずは運営の方が撮ってくださった写真でイベントの雰囲気を伝えられればと思う。
課題には、
2人から4人のグループに分かれて、密にコミュニケーションをとりながら作業した。

![作業中の風景](/images/scrap_me.jpg)

会場はmixi本社にある「コラボ」という共有スペース。普段は社員の方が一緒にご飯
を食べたりしているらしい。この写真には写っていないが、部屋の片隅にお座敷
スペースがあり、居心地が良さそうな感じがした。

![Scrap Challenge会場](/images/scrap_room.jpg)

イベント終了後に、元mixi社員の方がプレゼンテーションをしてくださった。
この方はmixi退社後、とあるスタートアップに勤めているらしいのだが、なんと
日本人に7人しかいない[Mars One](http://www.mars-one.com/)プロジェクト
の宇宙飛行士の候補者なのだ。Mars Oneは民間の団体による、火星に人類初の
居留地をつくることを目的としたプロジェクトだ。現状の計画では、火星に派遣された
人間が地球に帰還する手段が無いため、片道切符の旅行となる。少し前にかなり話題
になったので知っている人もいるだろう。

今回ご講演くださった方は、このMars Oneプロジェクトで火星に向かう候補者の1人だ。
もし選考に通り、本当に火星に旅立つことになれば、地球に帰ってくることはない。
そういう意味では、地球で過ごす残された時間は10年少ししかない。さらに、訓練は
7年かけて行われるため、俗世で過ごす時間はごくわずかだ。そんな中で、
mixiを辞め、スタートアップで働くという選択をした理由という、極めてスケールの
大きい話だった。

![Mars One 参加者の方の後ろ姿](/images/scrap_mars_one.jpg)

目に悪いTシャツだ。作業中は、このTシャツを映像や音楽にしたようなコンテンツが
会場内に流れ続けていて、かなり苦痛だった。

![妨害コンテンツTシャツ](/images/scrap_tshirt.jpg)

### 参加してみて
セキュリティにあまり興味はないのだけど、今回のイベントは楽しめたし、得るものは
多かった。XSSやSQLインジェクションという言葉は知っていたし、対策なども分かって
るつもりだった。しかし、実際に自らが攻撃者の立場となって実際のウェブ
アプリケーションを攻撃するという経験はなかった。このような経験を、mixiのSNSを
対象としてできたのはとても貴重だったと思う。セキュリティに夢中になる人間の
気持ちが少し理解できた。

さらに、レベルの高い参加者と運営の方と交流できたのは有意義だった。昼食や
イベント終了後の交流会など、カジュアルな雰囲気の中でディープな話 (Fusion-io、
ISUCON、Linuxカーネルなどなど) ができたのは非常に興奮した。また、参加者とmixi
のエンジニアの方のレベルの高さを実感した。ちなみにイベント終了後の交流会では、
[DEAN & DELUCA](http://www.deandeluca.co.jp/catering/)のケータリングがあった。
DEAN & DELUCAがケータリングサービスを行っているのは初めて知ったのだが、これが
やはりとても美味しくてお洒落だった。大阪にはデリバリしてくれないのが残念だ。

### まとめ
ウェブアプリケーションに興味のある/開発している学生に強くおすすめしたいイベント
だと思った。イベント自体の内容は良質だし、レベルの高い人間と知り合える。
さらに、昼食・夕食が無料で、地方の学生には交通費の援助もあるなど、
ホスピタリティも充実している。一方で、CTFに参加していたり、セキュリティに
関して独自に取り組んでいる学生には少し物足りないかもしれない。
