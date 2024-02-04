# Java初心者のためのPython×競技プログラミング入門Day7
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)(誘導あり)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴も長くないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
前回：[Java初心者のためのPython×競技プログラミング入門Day6](https://qiita.com/maru3460/private/00b2796580b6fc1b0e6e)

### 前提条件
 - Javaの基本がわかる
 - googleのアカウントを持っている
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day7.ipynb](https://colab.research.google.com/drive/1B0V6aDzuSNyY5slFeNxAakN7ZjpmGidu?usp=sharing)  
各sectionはこのファイルに対応しています。  
[github](https://github.com/maru3460/python_article)：記事含め、ソースコードが置いてあります。  

## 目標
今日で最後です。最初に目標として掲げた問題を解いてみましょう。

## 解く -> section1
頑張ってみてください。使えそうなlistとdictを置いておきます。  
```python
char_set = []

n = ord('a')
for i in range(26):
    char_set.append(chr(n + i))

#char_set = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']

chars = {}
for i in range(26):
    chars[char_set[i]] = 0

#chars = {'a': 0, 'b': 0, 'c': 0, 'd': 0, 'e': 0, 'f': 0, 'g': 0, 'h': 0, 'i': 0, 'j': 0, 'k': 0, 'l': 0, 'm': 0, 'n': 0, 'o': 0, 'p': 0, 'q': 0, 'r': 0, 's': 0, 't': 0, 'u': 0, 'v': 0, 'w': 0, 'x': 0, 'y': 0, 'z': 0}
```

<details><summary>方針</summary><div>

それぞれの文字の出現回数をcharsに記録する
↓
出現回数が多いものを探す
ちなみに、ランダムで探していった場合、出現回数が同じ時にアルファベット順を比較する必要がありますが、最初からアルファベット順で探していけば、数が大きいときのみ考えればよくなります。
</div></details>

<details><summary>途中まで</summary><div>

```python
#入力を受け取る
s = input()

#char_setとcharsを作っておく
char_set = []
chars = {}

n = ord('a')
for i in range(26):
    char_set.append(chr(n + i))
for i in range(26):
    chars[char_set[i]] = 0

#出現回数を数える
for i in range(len(s)):
    chars[s[i]] += 1
```
</div></details>

## まとめ
お疲れさまでした。解けましたでしょうか。解けなかったとしたらこの記事が悪いので、心の中で低評価でも押しておいてください。  
ここまで読んでいただき、本当にありがとうございました。  
