# Java初心者のためのPython×競技プログラミング入門Day2
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)(誘導あり)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴も長くないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
前回：[Java初心者のためのPython×競技プログラミング入門Day1](#)
次回：[Java初心者のためのPython×競技プログラミング入門Day3](#)

### 前提条件
 - Javaの基本がわかる。
 - googleのアカウントを持っている。
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください。

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day2.ipynb](https://colab.research.google.com/drive/1d8luAEE1CpgQbvZRTvHU3xbfAdFGwAle?usp=sharing)  
各sectionはこのファイルに対応しています。  

- [Java初心者のためのPython×競技プログラミング入門Day2](#java初心者のためのpython競技プログラミング入門day2)
		- [前提条件](#前提条件)
	- [Pythonの基本的な文法](#pythonの基本的な文法)
		- [標準出力 -\> section1](#標準出力---section1)
		- [変数とデータ型 -\> section2](#変数とデータ型---section2)
		- [コレクション -\> section3](#コレクション---section3)
		    - [list](#list)
  		    - [dict](#dict辞書)
		- [制御構文 -\> section4](#制御構文---section4)
			- [if](#if)
			- [for](#for)
			- [while](#while)
	- [まとめ](#まとめ)


## Pythonの基本的な文法
今日はPythonの基本的な文法について解説していこうと思います。

### 標準出力 -> section1
まあ、書き方が違うだけです。ただ、文の終わりに改行を入れないようにするには少し違ってきます。
```java
public class Main {

	public static void main(String[] args) {
		for(int i=0; i < 10; i++) {
			System.out.print(i);
		}
	}
}
```
```python
print('Hello, World!')

for i in range(10):
    print(i, end='')

print()#改行
#endには何か入れても大丈夫です
for i in range(10):
    print(i, end='/')
```
**課題1**
pythonで自己紹介してみましょう。  

### 変数とデータ型 -> section2
ここで、JavaとPythonで大きく違う点が出てきます。それが、型を指定しなくてもいい、ということです。昨日のコードにもありましたが、Pythonでは勝手に型を予測して、変数に入れてくれます。また、intが入っていた変数にStringを入れることなどもできます。
```java
public class Main {

	public static void main(String[] args) {
		int i = 123;
        System.out.println(i);
        //i = "Hello, World";コンパイルエラー
	}
}
```
```python=
i = 123
print(i)
i = 'Hello, World'
print(i)
```
大規模なシステムではバグの原因となることも多いでしょうが、個人で少し書く分にはそこまで困りません。むしろ書くコードの量が減ってとても楽になります。  

Pythonでよく使われるデータ型は以下の通りです。  
```python
s = 'Hello, World!'#str  JavaのStringです
num = 123#int
num = 3.14#float
check = True#bool
arr = [1, 2, 3, 4, 5]#list
arr = {1: '北海道', 47: '沖縄'}#dict
```
また、それぞれの変換は以下の通りとなります。
```python
s = str(12345)
print(type(s))#type()を使って型を表示できます。

num = int(12345)
print(type(num))

num = float('123.456')
print(type(num))

print(range(10))
arr = list(range(10))
print(arr)
```
bool、辞書は現段階では使う予定がないため、省略しています。  

**課題２**
自分の年齢(int)を変数に入れたうえで、自己紹介文に付け加えてみましょう。  

### コレクション -> section3

#### list

まずはlistについてです。基本的な使い方はJavaのListと同じですが、作り方や関数が違ってきます。  
```java:List
public class ListTest {

	public static void main(String[] args) {
		List<Integer> list = new ArrayList<>();
		list.add(1);
		list.add(2);
		list.add(3);
        
		System.out.println(list.get(0).toString() + list.get(1) + list.get(2));
	}
}
```
```python:list
arr = []
arr.append(1)
arr.append(2)
arr.append(3)

print(str(arr[0]) + str(arr[1]) + str(arr[2]))

#便利なので載せておきます。簡単に言うと、joinはlistをまとめて文字列にしてくれるもの、
#mapはlistの各値に一定の処理をしてくれるもの(今回は全部strにしてる)です。
print(''.join(map(str, arr)))
```
これを見て気づく人がいるかもしれませんが、Pythoにはジェネリクス(\<Integer\>など)が存在しないです。つまりは、ひとつのlistにいろいろなものを入れられます。  
```python:list
arr = []
arr.append(1)
arr.append('Hello, World')
arr.append([1, 2, 3, 4, 5])
print(arr)
```
ただしバグの原因となることも多いので、できるだけ同じ型のみを入れるようにしましょう。  
次に、基本的な関数を紹介しておきます。  
```python:list
arr = [1, 2, 3, 4, 5]
#追加：リストの末尾に指定した値が追加できます。
arr.append(6)
print(arr)

#挿入：リストの好きな位置に指定した値が追加できます。
arr.insert(0, 100)#一つ目の引数にindex、二つ目の引数が入れたい値です。
print(arr)

#削除(取り出し)
arr.pop(0)
print(arr)
print(arr.pop(0))#削除時に値が返ってきます
print(arr)
```
覚えておく必要はないです。必要な時にこの記事を見返すか、調べて使いましょう。  

#### dict(辞書)

次に、辞書についてです。現時点では使う予定はないので、紹介のみしておきます。
```java:map
public class MapTest {

	public static void main(String[] args) {
		Map<String, Integer> map = new HashMap<>();
		map.put("apple", 100);
		map.put("orange", 300);
		
		System.out.println(map);		
		System.out.println(map.get("apple"));
		System.out.println(map.keySet());
		System.out.println(map.values());
		
		map.put("banana", 500);
		System.out.println(map);
		map.remove("apple");
		System.out.println(map);
	}
}
```
```python:dict
arr = {}#listは[]、dict（辞書)は{}をつかいます。
arr['apple'] = 100
arr['orange'] = 300

print(arr.items())
print(arr["apple"])
print(arr.keys())
print(arr.values())

#追加
arr['banana'] = 500
print(arr.items())

#削除
del arr['apple']
print(arr.items())
```

**課題３**
実行した結果が、
```
[1, 2, 3, 4, 5]
[2, 3, 4, 5]
[2, 3, 1, 4, 5]
[2, 3, 1, 4, 5, 6]
```
となるようにコードを書いてみましょう。  

### 制御構文 -> section4
最後に、制御構文についてです。Javaでは{}によって制御構文の中と外を区切っていましたが、Pythonではインデントによって区切りを入れます。  
見た目はわかりやすくなりますが、インデントが崩れればコードの意味が大きく変わってしまいます。Javaの時よりもインデントを気にするようにしましょう。  
#### if
```java:if
public class IfTest {

	public static void main(String[] args) {
		if(2 > 1) {
			System.out.println("Hello, World");
		}
		
		int n = 5;
		if(n > 6) {
			System.out.println("n > 6");
		}else if(n < 4 && n != 5) {
			System.out.println("n < 4 かつ n != 5");
		}else {
			System.out.println("n == 5");
		}
	}
}
```
```python:if
if 2 > 1:
    print('Hello, World')

n = 5
if n > 6:
    print('n > 6')
elif n < 4 and n != 5:
    print('n < 4 かつ n != 5')
else:
    print('n == 5')
```

基本は同じなので、まずは書いて慣れていきましょう。  

**課題４**
以下のコードを完成させてください。  
```python
n = 80
#print('テストの点数は60点未満です。')
#print('テストの点数は60点以上100点未満です')
#print('テストの点数は100点です。')
```

#### for
pythonでfor文を書く時には、基本的にrange()を使います。  
```python:range
#引数に一つだけ値(n)を渡したとき、0以上n未満の整数が生成されます。
for i in range(5):
    print(i)

#引数にnとmを渡せば、n以上m未満の整数が生成されます。
for i in range(3, 8):
    print(i)

#引数にnとmとlを渡せばnからmまでの整数がlの幅で生成されます。
for i in range(0, 5, 2):
    print(i)

#逆順にもできます。
for i in range(10, 0, -1):
    print(i)
```
実行したい回数が決まっている場合は一番最初のものを使えばおっけーです。  
listを使う場合も紹介しておきます。
```python:for
#iにlistの値を入れたい場合
arr = [100, 200, 300]
for i in arr:
    print(arr)

#listの長さ分だけ実行したい場合
for i in len(arr):
    print('Hello, World')
```

**課題５**
Hello, Worldと10回表示させてください。  

#### while
これも書き方が違うだけです。
```java:while
public class WhileTest {

	public static void main(String[] args) {
		int i = 0;
		while(i < 5) {
			System.out.println("Hello, Wold");
		}
	}
}
```
```python:while
i = 0
while(i < 5):
  i += 1
  print('Hello, World')

while(True):
  i += 1
  print('i += 1')
  if i > 10:
    break
```
**課題６**
Hello, Worldと10回表示させてください。　　

## まとめ
今日は以上となります。一気に紹介したので疲れたと思うので、散歩でもしてきましょう。  
余裕があればGooleColaboratoryのほうで遊んでいただけると、次回の記事がわかりやすくなるかもしれません。  