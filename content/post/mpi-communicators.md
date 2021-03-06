---
title: "MPIのコミュニケータについて"
date: "2015-06-16T14:40:51+09:00"
---

MPIのコミュニケータについて、日本語の資料は基礎的なものしか見当たらなかったので
、少し発展的な内容についてメモしておく。この [発表資料](https://computing.llnl.gov/tutorials/mpi_advanced/DavidCronkSlides.pdf) 、およびMPICHのドキュメントを参考にしている。

<!--more-->

## 用語
MPIにおけるコミュニケータ、グループ、プロセスについて整理する。

- プロセス
    - MPIはプロセス間の通信を抽象化して記述するライブラリである。
    - プロセスは複数のマシンで分散して並列に動作する。1つのマシンで複数のプロセスが
        動作することもできる。
- グループ
    - グループは、複数のプロセスの順序付けられた集合である。
    - グループに所属する全てのプロセスは、0から始まるIDが振られている。この
        IDのことを**ランク**という。
    - グループは積、和、差などの演算で自由に操作できる。
- コミュニケータ
    - コミュニケータは、MPIの通信を行うランク空間を表現するものである。
    - コミュニケータは、いずれかのグループにひも付けられている。
    - MPI上の全ての通信は、いずれかのコミュニケータを指定して行われる。
    - デフォルトで、全てのプロセスを含んだ`MPI_COMM_WORLD`と
        自プロセスのみを含んだ`MPI_COMM_SELF`が存在する。

コミュニケータとグループはm:nの関係、グループとプロセスもm:nの関係にある。
ここで意識したいのが、コミュニケータとグループの違いである。多くの資料で
コミュニケータとグループを等価なものであるかのように扱っている。しかし実際は、
1つのグループに対して複数のコミュニケータを割り当てることができる。

## コミュニケータに関連する関数

- `MPI_Comm_size`: あるコミュニケータに含まれるプロセスの数を得る。
- `MPI_Comm_rank`: あるコミュニケータの自プロセスのランクを得る。
- `MPI_Comm_dup`: 既存のコミュニケータと同じグループにひも付けられた、新しい
    コミュニケータを作成する。
- `MPI_Comm_create`: 与えられたグループにひも付けらた新しいコミュニケータを
    作成する。
- `MPI_Comm_split`: 既存のコミュニケータのグループを、複数のグループに分割し、
    それぞれのグループに対して新しいコミュニケータを作成する。
- `MPI_Comm_group`: コミュニケータをにひも付けられたグループを得る。

## グループに関連する関数
- `MPI_Group_union`: グループの和集合を得る。
- `MPI_Group_intersection`: グループの積集合を得る。
- `MPI_Group_difference`: グループの差集合を得る。
- `MPI_Group_incl`, `MPI_Group_excl`, `MPI_Group_range_incl`, `MPI_Group_range_excl`:
    グループの一部から新しいグループを作成する。
- `MPI_Group_translate_ranks`: あるグループにおけるランクを、別のグループに
    おけるランクに変換する。


## イントラコミュニケータとインターコミュニケータ
コミュニケータは、2種類に分類できる。1つ目がイントラコミュニケータである。
イントラコミュニケータは1つのグループにひも付けられたコミュニケータで、通信を
そのグループ内のみに限定する。2つ目はインターコミュニケータである。
インターコミュニケータは、通信を2つの互いに素なグループ (=両方のグループに所属するプロセスが
存在しない) 間のみに限定する。

以下ではインターコミュニケータの説明を行う。自プロセスが所属するグループを
ローカルグループ、もう片方のグループをリモートグループと呼ぶ。送受信の相手と
なるプロセスは常にリモートグループに所属していることになる。下記に
インターコミュニケータに特有な関数の一部を示す:

- `MPI_Comm_test_inter`: コミュニケータがインターコミュニケータであるか判定する。
- `MPI_Comm_remote_size`: リモートグループのプロセス数を得る。
- `MPI_Comm_remote_group`: リモートグループを得る。
- `MPI_Intercomm_create`: 2つのコミュニケータからインターコミュニケータを作成する。
- `MPI_Intercomm_merge`: インターコミュニケータのローカルグループとリモートグループ
    をマージし、新しいイントラコミュニケータを作成する。

`MPI_Comm_create`, `MPI_Comm_dup`, `MPI_Comm_split`などの関数は、
インターコミュニケータでも動作する。また、集合通信の大半もインターコミュニケータで
動作する。詳しい説明は、[MPIのドキュメント](http://www.mpich.org/static/docs/v3.1/www3/)
を参照すると良いと思う。

