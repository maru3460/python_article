# Java初心者のためのPython×競技プログラミング入門Day４
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴が長いわけでもないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
前回：[Java初心者のためのPython×競技プログラミング入門Day3](#)
次回：[Java初心者のためのPython×競技プログラミング入門Day5](#)

### 前提条件
 - Javaの基本がわかる。
 - googleのアカウントを持っている。
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください。

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day4.ipynb](https://colab.research.google.com/drive/18hyferPW_lPXoeKPUgTwl5AixgY0KfVI?usp=sharing)  
各sectionはこのファイルに対応しています。  

- [Java初心者のためのPython×競技プログラミング入門Day４](#java初心者のためのpython競技プログラミング入門day４)
    - [前提条件](#前提条件)
  - [文字列操作、多次元配列について](#文字列操作多次元配列について)
  - [文字列操作について](#文字列操作について)
  - [多次元配列について](#多次元配列について)


## 文字列操作、多次元配列について
今日は文字列操作、多次元配列について解説していこうと思います。

## 文字列操作について
まずは文字列操作についてですが、これについては前回少し触れたため、軽くいこうと思います。
```java:String
public class StringTest {

	public static void main(String[] args) {
		//文字列の足し算
		System.out.println("Hello" + " " + "World");
		
		//文字の取り出し
		String s1 = "hello";
        for (int i = 0; i < s1.length(); i++) {
            System.out.println(s1.charAt(i));
        }

        // スライス(部分文字列の取り出し)
        String s2 = "abcdefghijk";
        System.out.println(s2.substring(1, 5));

        // Listにする
        //略
	}
}
```
```python:str
#文字列の足し算
print('Hello' + ' ' + 'World')

#文字の取り出し
s = 'hello'
for i in range(len(s)):
    print(s[i])

#スライス(部分文字列の取り出し)
s = 'abcdefghijk'
print(s[1:5])#これはlistでも使えます

#listにする
s = 'abcdefghijk'
print(s)
s = list(s)
print(s)

#strのlistから文字列に
s_list = ['a', 'b', 'c', 'd', 'e']
print(''.join(s_list))
#s_listの要素はstrである必要があります。そのためintのlistの時は
#print(''.join(map(str, num_list)))
#のようにmap()をつかって各要素をstrにしてからjoinに入れる必要があります。
```

これだけ覚えておけばそこまで困らないと思います。物足りない方は、python 文字列操作などで調べてみてください。  
スライスに関してですが、s[1:5]とした場合、s[1]からs[4]までのstrが返ってきます。そのため、最初から最後まで取り出そうとしたら(無意味な操作ですが)、s[0:len(s)]となります。  

**課題１**
「abcdefg」からbcとefを取り出し、bcefとして表示してみましょう。  

## 多次元配列について
