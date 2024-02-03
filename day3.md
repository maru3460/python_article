# Java初心者のためのPython×競技プログラミング入門Day３
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)(誘導あり)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴も長くないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
前回：[Java初心者のためのPython×競技プログラミング入門Day2](#)
次回：[Java初心者のためのPython×競技プログラミング入門Day4](#)

### 前提条件
 - Javaの基本がわかる。
 - googleのアカウントを持っている。
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください。

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day3.ipynb](https://colab.research.google.com/drive/1bVs4U-iZvnR5KrvYTOjfkj5b11fy-L4N?usp=sharing)  
各sectionはこのファイルに対応しています。  

- [Java初心者のためのPython×競技プログラミング入門Day３](#java初心者のためのpython競技プログラミング入門day３)
    - [前提条件](#前提条件)
  - [A問題を解いてみる](#a問題を解いてみる)
  - [標準入力 -\> section1](#標準入力---section1)
  - [AtCorderについて](#atcorderについて)
  - [Atcorder Problemsで提出してみる -\> section2](#atcorder-problemsで提出してみる---section2)
  - [まとめ](#まとめ)


## A問題を解いてみる
今日はAtCoderのA問題を触ってみようと思います。

## 標準入力 -> section1
AtCoderをやるうえで最初の壁となっているのがこの標準入力です。出力は自分の好きなようにすればいいですが、入力はそうもいきません。入力される値が最初から決まっており、それを正しく受け取る必要があります。  
まずは以下のものをコピーして使っていってください。  
```python:inout
#入力
#Hello
s = input()

#入力
#123
n = int(input())

#入力
#ab, cd, ef
s_list = input().split()
s1, s2, s3 = input().split()

#入力
#12, 34, 56
n_list = list(map(int, input().split()))
n1, n2, n3 = map(int, input().split())

#入力
#3      この後に入力される行の数
#123
#234
#345
n = int(input())
n_list = []
for i in range(n):
    tmp = int(input())
    n_list.append(tmp)

#入力
#4 5
#1 2 3 4 5
#1 2 3 4 5
#1 2 3 4 5
#1 2 3 4 5
h, w = map(int, input().split())   #h = height, w = wide
field = []
for i in range(h):
    tmp = list(map(int, input().split()))
    field.append(tmp)
```

**課題１**
入力値を「123 456 789」として、以下のように出力してください。
```
123
456
789
```

## AtCorderについて
とても分かりやすく解説している方々がいらっしゃるので、おすすめの記事を貼っておきます。
 - [レッドコーダーが教える、競プロ・AtCoder上達のガイドライン【初級編：競プロを始めよう】](https://qiita.com/e869120/items/f1c6f98364d1443148b3)
 - [AtCoder コンテストについての tips](https://qiita.com/drken/items/8a6f139158cde8a61dce)
 - [【AtCoder】普通の人である私が緑になるまでにしたこと](https://qiita.com/Kota-Y/items/396ab3c57830dad65cfb)

## Atcorder Problemsで提出してみる -> section2
[Atcorder Problems](https://kenkoooo.com/atcoder/#/table/)についてついては[こちら](https://chokudai.hatenablog.com/entry/2019/02/11/155904)のブログを参考にしていただきたいです。  
まずはAtCoder Beginner Contest(以下ABC)320のA問題を見てみましょう。  

ここで使うのがGoogleColaboratoryです。自分でコードを書いてみて、いったんGoogleColaboratoryで試してみてください。[Java初心者のためのPython×競技プログラミング入門Day3.ipynb](https://colab.research.google.com/drive/1d8luAEE1CpgQbvZRTvHU3xbfAdFGwAle?usp=sharing)を代用してもいいですし、自分でファイルを作って書いてもおっけーです。

いけそうな方は以下のヒントを見ずに解いてみましょう
<details><summary>ヒント1</summary><div>

まずは問題文の情報から読み取れることを整理してみましょう。
入力：A B
出力：AのB乗とBのA乗の和
制約：AとBは2以上9以下の整数で、AはB以下
</div></details>

<details><summary>ヒント2</summary><div>

pythonでは累乗は以下のように書きます。
```python
n = 2
m = 5
print(n ** m)
#32
```
</div></details>

<br><br><br><br><br><br><br><br><br><br><br><br><br><br>
解けましたでしょうか。まだの方は下にスクロールせずに解いてみてください。  

pythonにもpythonの入出力にも慣れていない今の状況では難しく感じると思います。これに関しては慣れてくださいとしか言えません🙇  
以下答えです。

```python:answer
a, b = map(int, input().split())
ans = a ** b + b ** a
print(ans)
```
やっていることは  
 - AとBを受け取る
 - AのB乗とBのA乗をansに入れる
 - ansを表示する

です。これだけ見ると簡単ですね。以下に二つ問題を置いておきます。まずは問題文を整理して考えてみてください。ヒントを見て解く、または解けなかったら戻ってきてください。  

ABC315 A問題
<details><summary>ヒント</summary><div>

pythonのstrは以下のようにindexでそれぞれの要素にアクセスできます。
```python:str
s = hello
print(s[0] + s[1])
```

また、この問題にはもう一つの落とし穴があります。[0]で、listと同じようにそれぞれの要素にアクセスできますが、実際はstrです。pop、appendなどの関数は使えません。
```python
#エラー：'str' object has no attribute 'pop'
s = 'hello'
for i in range(5):
  if s[i] == 'e':
    s.pop(1)
```

また、途中で要素を削除してしまうと、range(5)よりも要素数が少なくなってしまい、存在しない要素にアクセスすることになります。
```python
#エラー：list index out of range
s = list('hello')
print(s)

for i in range(5):
  if s[i] == 'e':
    s.pop(i)
```

これを回避するには、新しいリストに要素を入れたうえで、strに戻しましょう。  
```python
s = list('hello')
ans = []

for i in range(5):
  if s[i] != 'e':
    ans.append(s[i])

print(ans)
print(''.join(ans))
```
</div></details>

<br>  

ABC318 A問題

<details><summary>ヒント</summary><div>

まずは問題文を整理てみましょう。
N：日数
M：最初に満月を見られる日
P：次に満月を見られるまでの日数
    
まずはNがMよりも大きければ一回は見れますね。そのあとは(N - M)のなかで何回見られるでしょうか？具体的な数字を入れて試してみましょう。
たとえば、(N - M) = 10、P = 3のときは3回、28と5のときは5回見れます。あとはそれを式にして実装してみましょう。
</div></details>

<br><br><br><br><br><br><br><br><br><br><br><br><br><br>
解けましたでしょうか。まだの方は下にスクロールせずに解いてみてください。

以下答えです。
```python:ABC315 A問題
s_list = list(input())
ans = []

for i in range(len(s_list)):
    #s_list[i]がaiueoでなければansに追加する
    if s_list[i] != 'a' and s_list[i] != 'i' and s_list[i] != 'u' and s_list[i] != 'e' and s_list[i] != 'o':
        ans.append(s_list[i])

print(''.join(ans))

#こっちでもおっけー
s_list = list(input())
ans = []
wrong_list = ['a', 'i', 'u', 'e', 'o']

for i in range(len(s_list)):
    #s_list[i]がaiueoでなければansに追加する
    if not s_list[i] in wrong_list:#<=>もしs_list[i]がwrong_listになければ
        ans.append(s_list[i])

print(''.join(ans))
```
```python:ABC318 A問題
n, m, p = map(int, input().split())
ans = 0

#n < mのときは一回も月が見れない
if n >= m:
    #n >= mであれば最初の一回は見れるのでans += 1しておく
    ans = 1
    #m日たったと仮定して、nからmを引いておく
    n -= m
    #残りのn日のうち、pが入る分だけ満月が見れる
    ans += n // p

print(ans)
```

## まとめ
今日は以上となります。解けなかった方は今日の問題の解きなおし、解けた方はほかのA問題を解いてみるといいかもしれません。お疲れさまでした。