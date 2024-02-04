# Java初心者のためのPython×競技プログラミング入門Day5
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)(誘導あり)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴も長くないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
前回：[Java初心者のためのPython×競技プログラミング入門Day4](https://qiita.com/maru3460/private/36ee56dbf4d7b42e3d56)
次回：[Java初心者のためのPython×競技プログラミング入門Day6](https://qiita.com/maru3460/private/00b2796580b6fc1b0e6e)

### 前提条件
 - Javaの基本がわかる
 - googleのアカウントを持っている
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day5.ipynb](https://colab.research.google.com/drive/1LFPJTMOdTroMTf-7rur5E3QOLH9XY5lF?usp=sharing)  
各sectionはこのファイルに対応しています。  
[github](https://github.com/maru3460/python_article)：記事含め、ソースコードが置いてあります。  

## ソートと探索、関数について
今日はソートと関数についてです。

## ソートについて -> section1
やりたいことは単純で、並び替えです。1から100までの数字が付いた書類をランダムで渡されたら並び替えたくなりますよね。それと同じです。  
例を書いてみます。
```python:bubblesort
arr = [4, 1, 8, 3, 6, 2, 0, 5, 1]

#一週目：一番大きいものを一番後ろに
#二週目：二番目に大きいものを二番目に後ろに
#…
#ってやってます。
for i in range(len(arr) - 1):
    for j in range(len(arr) - 1 - i):
        if arr[j] > arr[j + 1]:
            arr[j], arr[j + 1] = arr[j + 1], arr[j]

print(arr)
```
これを理解する必要はないです。なぜなら、一行でやってくれるようにしてくれているからです。  
```python:sort
arr = [4, 1, 8, 3, 6, 2, 0, 5, 1]

arr.sort()

print(arr)
```
昇順にもできます
```python:sort
arr = [4, 1, 8, 3, 6, 2, 0, 5, 1]

arr = sorted(arr, reverse=True)

print(arr)
```
**課題１**
以下のリストを降順にソートして、順番に表示してください。
```python
arr = [4, 7, 23, 6785, 3, 4, 234, 56, 235, 45, 7, 34, 5, 45, 7]
```

## 探索について -> section2
一番小さい数、大きい数を探すのであればソートして0か最後を出力すればいいです
```python:search
arr = [4, 1, 8, 3, 6, 2, 0, 5, 1]

arr.sort()
print(arr[0])
print(arr[len(arr) - 1])
```
ただ、特定の値を探すときはそうもいきません。一つずつ値を確かめていく必要があります。  
例題 以下のlistのうち、6のindexを求めて出力せよ(6は一つだけ存在する)  
```python:search
arr = [4, 1, 8, 3, 6, 2, 0, 5, 1]

#一つずつチェックしていって、求める値が見つかったらbreak
for i in range(len(arr)):
    if arr[i] == 6:
        ans = i
        break

print(ans)
```
というわけで問題です。
**課題２**
以下の二次元listから、一つ目の値が8であるものの二つ目の値を出力してください。  
```python
arr = []
for i in range(10):
    arr.append([i, i * 2])
#arr = [[0, 0], [1, 2], [2, 4], [3, 6], [4, 8], [5, 10], [6, 12], [7, 14], [8, 16], [9, 18]]
```

## 関数について -> section3
次は関数についてです。
```python:function
def func(a, b):
    return a + b

print(func(1, 2))
```
pythonはオブジェクト指向言語ですが、いったんオブジェクトとかは忘れましょう。関数を定義しておけば使えるようになります。書き方は上記のように、
```
def 関数名(引数…):
    処理内容
    return 返り値
```
です。関数内で使える変数は引数か関数内で定義したものだけですが、globalを使えばアクセスできます。
```python:function
num = 1

def func():
    global num
    num += 1

for i in range(100):
    func()

print(num)
```

**課題３**
引数が2の倍数であれば1、それ以外は0を返す関数を定義し、以下のlistの値にそれぞれ適用していって、出力していってください。
```python
arr = list(range(10))
#arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## まとめ
今日は以上となります。余裕があればAtCorderのA問題(ABC338, 328など)を解いてみてください。