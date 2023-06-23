# テーマ
!theme toy
!theme vibrant
!theme _none_

# example01

@startuml example01
@enduml
で囲む

2つのテーブル
entity users
entity profiles

2つのテーブルの関係
users ||--o{ profiles : resume

{} 中括弧の中にDBでいうテーブルの中身を書きます。
： 記号の後ろにエンティティ同士の関係の説明を書きます。日本語でもok。

# example02

2つのテールの関係
' Entity01 }|..|| Entity02
' Entity03 }o..o| Entity04
' Entity05 ||--o{ Entity06
' Entity07 |o--|| Entity08

|o-- 0 か 1
||-- 1 のみ
}o-- 0 以上
}|-- 1 以上

線の種類を選ぶ
Entity09 "1" ||-----o{ "0以上" Entity10 : contains
Entity11 "0以上"  }o--|| "1のみ" Entity12  : aggregation
Entity13 "1以上" }|..o| "0 or 1"  Entity14 : 破線 で つなぐ

-- 実線
.. 破線

# example03

テーブル内の線を選ぶ

--通常線--
==二重線==
..ドット線..
__太文字線__

上下左右に配置の場所を決める
users -right-o{ profiles : resume
users -down-o{ profiles : resume
users -up-o{ profiles : resume
users -left-o{ profiles : resume

# example04

' エンティティ名の日本語化
entity "ユーザー" as users {
' プライマリキー
+ USER_ID [PK]
--
USER_NAME
UID
}

[PK] プライマリキー
[FK] 外部キー

' 丸記号
+ PROFILE_ID [PK]

' ダイヤ記号
# USER_ID [FK]

項目の日本語化
entity "ユーザー" as users {

"ユーザー" 表示する項目、
users テーブルの名前、
asでつなげることで日本語を表示できます。

# example05

' 拡大縮小
scale 0.7

' タイトル
title Values communication \n example

' 丸記号
+ USER_ID [PK]

' 強調文字
**USER_NAME**

' 丸記号＋強調文字
* **UID**

' ヘッダー
header
<font color=red>Warning:</font>
Do not use in production.
製品版で使わないでね。
endheader

' フッター
center footer Generated for demonstration

center、left、rightを使ってフッタ、
ヘッダの表示位置を指定することもできます。
フッタとヘッダではHTMLタグを
使用することもできます。

' キャプション(見出し)
caption Values Network Service

' legend(説明文)
legend
' legend top right
' legend left
これは説明文です

ER図の解説を行います。
空行もそのまま表示されます。
endlegend

UID
先頭の*の後ろに空白を1つ空ける。


# example06

ER図の外側に書ける説明文

header some header
footer some footer
title My title
caption This is caption
legend
The legend
end legend

entity users
entity profiles

users ||--o{ profiles : resume

# example07

色をつける、文字の大きさを変える 装飾文字等

<style>
title {
HorizontalAlignment right
FontSize 24
FontColor blue
}
header {
HorizontalAlignment center
FontSize 26
FontColor purple
}
footer {
HorizontalAlignment left
FontSize 28
FontColor red
}
legend {
FontSize 30
BackGroundColor yellow
Margin 30
Padding 50
}
caption {
FontSize 32
}
</style>
header some header
footer some footer
title My title
caption This is caption
legend
The legend
end legend

entity users
entity profiles

users ||--o{ profiles : resume

# example08

孤立したエンティティを非表示または削除します。
デフォルトでは、すべて表示されます。

entity "ユーザー" as users {
+ USER_ID [PK]
--
USER_NAME
UID
INSERT_DATA
UPDATE_DATE
DELETE_FLAG
}

entity "プロファイル" as profiles {
+ PROFILE_ID [PK]
--
' ダイヤ記号
# USER_ID [FK]
--
PROFILE_NAME
PROFILE_OVERVIEW
INSERT_DATA
UPDATE_DATE
DELETE_FLAG
}

entity "プロファイルの画像" as profile_images {
+ IMAGE_ID [PK]
--
# PROFILE_ID [FK]
--
PROFILE_IMAGE
INSERT_DATA
UPDATE_DATE
DELETE_FLAG
}


' コメント：配置方法
users --right--o{ profiles : resume


' hide @unlinked
' remove @unlinked

hide(隠す)すると非表示になる。
remove(削除)すると非表示になり、表示領域が削除した分だけ減る。


