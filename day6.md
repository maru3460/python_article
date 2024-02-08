# Java初心者のためのPython×競技プログラミング入門Day6
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)(誘導あり)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴も長くないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
前回：[Java初心者のためのPython×競技プログラミング入門Day5](https://qiita.com/maru3460/private/8b5f58f44081111d90ce)
次回：[Java初心者のためのPython×競技プログラミング入門Day7](https://qiita.com/maru3460/private/b2af82d55d8330a353a0)

### 前提条件
 - Javaの基本がわかる
 - googleのアカウントを持っている
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day6.ipynb](https://colab.research.google.com/drive/1lXBuIgEX_Z6kqcpK8jk5g2KUdD4ajYSe?usp=sharing)  
各sectionはこのファイルに対応しています。  
[github](https://github.com/maru3460/python_article)：記事含め、ソースコードが置いてあります。  

## 問題に慣れる
今日は問題に慣れるために、実際に問題を解いていこうと思います。 
※最適な解き方を考えているわけではありません。無駄な処理や書き方もしています。

## ABC324 B問題 -> section1
まずはABC324のB問題を見ていきましょう。まずは問題文、制約、入出力、例とその回答をよく読んで、どのようなコードを書けばいいか考えてみてください。紙にメモを書いてみるのも効果的だと思います。　　

<br><br><br><br><br>

わかりやすく言い直すと、自然数Nが与えられてその約数が2の累乗と3の累乗のみであればYes、それ以外はNoを出力せよって感じですね。

### 準備
まずは準備として、以下のaとbを求めてみましょう。

```python
2 ** a <= n < 2 ** b
``` 

pythonで対数をとりたい場合、math.logを使いましょう。logを習ってない方、忘れてしまった方は[こちら](https://lab-brains.as-1.co.jp/enjoy-learn/2023/02/41579/)をどうぞ。わかりやすく解説してくださっていると思います。  

```python
#pythonでも、モジュールを使う場合はimportで使うモジュールを指定する
#自動では補完されないので注意
import math

#math.log(a, b)とすると、bの何乗がaになるのか、が返ってきます。
print(math.log(64, 2))#2 ** 6 == 64
print(math.log(63, 2))#2 ** 5.977… == 63
```
よって、aとbは以下のようになります。

```python
import math

n = int(input())

#int()の引数にfloatを入れた場合、小数点以下切り捨てです。
a = int(math.log(n, 2))
b = a + 1

print(a)
print(b)
```

これで何を求めるかというと、xとyの値の範囲です。`n = 2 ** x * 3 ** y`となる可能性のあるxとyを考える場合、`n < 2 ** x`や`n < 3 ** y`となるようなxとyについては考える必要がないです。ゆえに上記のaを用いると、xの範囲は0以上a以下で考えればよい、となります。

### アルゴリズム
xとyの取りうる値の範囲を求めたところで、これをどのように使えばいいでしょうか？C問題以降であれば効率を考える必要がありますが、AやB問題であれば考えなくていいです。つまり、取りうるxとyを全部試してみましょう。  
例として、`0 <= x < 5, 0 <= y < 3`として、xとyの組み合わせをすべて出力してみましょう。  
```python
for x in range(5):
  for y in range(3):
    print(f'x: {x}, y: {y}')
```
x(0～4), y(0～2)の全ての組み合わせを表示しています。

### 解く
準備とアルゴリズムでやったことを組み合わせて問題を解いていきます。自力で解けそうな方はいったん自分でコードを書いて提出してみましょう。  

<br><br><br><br><br>

```python
import math

#入力を受け取る
n = int(input())

#xとyの上限を求める
x_max = int(math.log(n, 2))
y_max = int(math.log(n, 3))

ans = 'No'
#取りうるxとyを全て確かめていって、nになるxとyの組み合わせが見つかったらbreak
for x in range(x_max + 1):
  for y in range(y_max + 1):
    if n == 2 ** x * 3 ** y:
      ans = 'Yes'
      break

#見つからなかった場合は、初期値のNoが出力される
print(ans)
```

## ABC335 B問題 -> section2
次に、ABC335のB問題です。これもまた、問題文、制約、入出力、例とその回答をよく読んで、どのようなコードを書けばいいか考えてみてください。

<br><br><br><br><br>

言っていることはややこしいですが、要するにxを百の位、yを十の位、zを一の位としたときに、小さい順に全て並べろってことです(ただし、各位が9までではなく、21まであります)。

### アルゴリズム
ぱっと見で考えるとx、y、zをそれぞれ0からNまでfor文で繰り返せばよさそうですが、その場合`x + y + z <= N`が満たせないときがあります。`x = 0, y = 0`の時と`x = 0, y = 1`の時を比較してみます。`x = 0, y = 0`の時は`0 <= z <= N`ですが、`x = 0, y = 1`の時は`0 <= z <= N - 1`となります。  
試しにxは0、Nは3としてコードを書いてみます。
```python
x = 0
n = 3

for y in range(n + 1):#range(n)とすると0からn-1であるため
  for z in range(n + 1):
    print(f'{x} {y} {z}')
```
このままでは`x + y + z <= N`を満たせないため、range()でyの分を引いておきます。  
```python
x = 0
n = 3

for y in range(n + 1):
  for z in range(n + 1 - y):
    print(f'{x} {y} {z}')
```

### 解く
というわけで、いったん自力で解いてみてください。  

<br><br><br><br><br>

```python
n = int(input())
for x in range(n + 1):
  for y in range(n + 1 - x):
    for z in range(n + 1 - x - y):
      print(f'{x} {y} {z}')          
      #ややこしいですがこれでもおっけー
      #mapで全部strにする -> listにする -> joinで間に空白を入れて出力する
      #print(' '.join(list(map(str, [x, y, z]))))
```

最後に課題です。ABC327のB問題を解いてみましょう。

<details><summary>ヒント</summary><div>

1 <= B <= 10 ** 18であり、
```python
print(15 ** 15 <= 10 ** 18)
#True

print(16 ** 16 <= 10 ** 18)
#False
```
となります。
</div></details>

## まとめ
今日は以上となります。これであと一日になります。頑張りましょう。  
[おすすめの曲](https://www.youtube.com/watch?v=XogSflwXgpw)でも紹介しておきます。勉強のお供にどうぞ。