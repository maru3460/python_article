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
  - [まとめ](#まとめ)


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
次に、多次元配列についてです。名前だけ聞くと難しそうですが、listの中にlistを入れるだけです。例えとしては、オセロをコードで表す、とすると想像しやすいかもしれません。オセロの白と黒を1と0で表した横一列のlistが縦のlistに収まっている感じです。　　

イメージ(3 x 3)
```
          list[0] = [0, 1, 0]
list =  [ list[1] = [1, 0, 1] ]
          list[2] = [0, 1, 0]  
```
っていう感じです。(こういうのうまく書けるツール知っている方いたら教えてください…)  
というわけでコードにしてみます。  
```java:list in list
public class ListTest {

	public static void main(String[] args) {		
		List<List<Integer>> arr = new ArrayList<>();
		
		List<Integer> tmp1 = new ArrayList<>();
		tmp1.add(1);
		tmp1.add(2);
		tmp1.add(3);
		tmp1.add(4);
		List<Integer> tmp2 = new ArrayList<>();
		tmp2.add(5);
		tmp2.add(6);
		List<Integer> tmp3 = new ArrayList<>();
		tmp3.add(7);
		tmp3.add(8);
		tmp3.add(9);
		
		arr.add(tmp1);
		arr.add(tmp2);
		arr.add(tmp3);
		
        //一個ずつ値を取り出す。
		for(int i=0; i < arr.size(); i++) {
			for(int j=0; j < arr.get(i).size(); j++) {
				System.out.println(arr.get(i).get(j));
			}
		}
		
		arr.clear();
		
        //[x ^ 0, x ^ 1, x ^ 2]
		for(int i=0; i < 10; i++) {
			List<Integer> tmp = new ArrayList<>();
			tmp.add(1);
			tmp.add(i);
			tmp.add(i * i);
			arr.add(tmp);
		}
		
		System.out.println(arr);
		
		//5の2乗は？
		System.out.println(arr.get(5).get(2));

		//3の0乗は？
		System.out.println(arr.get(3).get(0));
    }
}
```
```python:list in list
arr = [[1, 2, 3, 4], [5, 6], [7, 8, 9]]

print(arr[0])
print(arr[1])
print(arr[2])

#一個ずつ値を取り出す。
for i in range(len(arr)):
    for j in range(len(arr[i])):#ここもiにすると値がバグるので違う変数を使う
        print(arr[i][j])#arrのi番目の要素であるリストの、j番目の値を表示する

#[x ^ 0, x ^ 1, x ^ 2]
arr = []
for i in range(10):
    tmp = [1, i, i ** 2]
    arr.append(tmp)
print(arr)

#5の2乗は？
print(arr[5][2])

#3の0乗は？
print(arr[3][0])
```
慣れない書き方だとは思いますが、使っていけばそのうち慣れます。.ipynbのほうにいくつか問題を用意しておいたので、解いてみてください。(３についてはすぐに答えを見てしまっても大丈夫です。)  
ちなみに、\#一個ずつ値を取り出す。のところを言語化してみると
```
arrの大きさの分だけ以下繰り返す(現在の繰り返し回数はiで表す)
    arr[i]の大きさの分だけ以下繰り返す(現在の繰り返し回数はjで表す)
        arrに含まれるlistの内、i番目のlistのj番目の要素を取り出して表示する
```
となります。

## まとめ
今日は以上となります。疲れた人は[ねこ](https://www.youtube.com/watch?v=tgfGiTA1pek)でも見て癒されてください。  

