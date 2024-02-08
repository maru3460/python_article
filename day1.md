# Java初心者のためのPython×競技プログラミング入門Day1
本記事は、Javaの基本を学び終えた方に向けて、Pythonを使って競技プログラミングを始めてもらおうという趣旨の記事です。１週間でAtCorderのB問題(現時点で最新のABC338)(誘導あり)を解けるようにする、ということを目標として書いていきます。  
言い訳：まだ業務未経験であり、歴も長くないため、間違っているところや勘違いについてはご容赦下さい。  
初投稿のため、至らぬ点はぜひご指摘いただきたいです。
次回：[Java初心者のためのPython×競技プログラミング入門Day2](https://qiita.com/maru3460/private/848b28a92719b86c8044)

### 前提条件
 - Javaの基本がわかる
 - googleのアカウントを持っている
 - AtCorderのアカウントを持っている。持っていない方は[こちら](https://info.atcoder.jp/overview/contest/intro)を参考にしてください

Python実行用ファイル:[Java初心者のためのPython×競技プログラミング入門Day1.ipynb](https://colab.research.google.com/drive/15wbCui49Y9Ohb261tLlXNebwfoLTi4Cx?usp=sharing)
各sectionはこのファイルに対応しています。  
[github](https://github.com/maru3460/python_article)：記事含め、ソースコードが置いてあります。

## Pythonの魅力
まず最初に、Pythonの魅力について書いていこうと思います。

### 初心者へのわかりやすさ  
```java:hello, world
public class HelloWorld {

	public static void main(String[] args) {     
		System.out.println("Hello, World!");
	}
}
```
JavaでのHello, Worldです。文字が多いですね。  
次に、PythonでのHello, Worldです。
```python:Hello, world
print('Hello, World!')
```
文字が少ないですね。  

もう一つの例として、10回Hello, Worldを書いてみます。  
```java:hello, world10
public class HelloWorld {

	public static void main(String[] args) {
        for(int i=0; i < 10; i++){
            System.out.println("Hello, World!");
        }
	}
}
```
文字が多いですね。  
次に、Pythonです。  
```python:Hello, world10
for i in range(10):#指定された数の配列のようなものを返す関数。iに0から9を入れている.
    print('Hello, World!')
```
文字が少なくてわかりやすいです。  

以上からわかるように、PythonはJavaよりも少ないコードでいろいろなことができます。文字数が多くなるとそれだけでわかりずらくなってしまうため、とても初心者向きの言語だと考えています

### 書き方の違い
Javaでは文末にセミコロン(;)が必要でしたが、Pythonでは必要ないです。また、文のまとまりを区切るのが波カッコ({})ではなくインデントです。
```java
public class HelloWorld {

	public static void main(String[] args) {		
	System.out.println("Hello, World!");
	
				for(int i=0; i < 10; i++) {
System.out.println(i);
									}
	}
}
```
```python
print('Hello, World!')

for i in range(10):
	print(i)

#IndentationError: unexpected indent
for i in range(10):
    print(i)
        print(i)
```
いちいちセミコロンや波カッコを書くことのわずらわしさから解放されます。ただし、インデントが崩れると意味が変わってしまうので気を付けてください。

### 実行の手軽さ
知っての通りJavaはコンパイル型言語であり、実行するためにはコンパイルという手順を踏む必要があります。一方でPythonはインタプリタ型言語です。ソースコードを指定してあげれば実行できます。  
例を出すと、  
```shell:java
javac HelloWorld.java
java HelloWorld
```
が  
```shell:python
python hello_world.py
```
となります。  
これはそこまで変わらないですが、ソースコードを指定すれば実行できるというのはとても分かりやすいと思っています。  

## 実際に実行してみる -> section1
上記の説明でPythonの魅力は伝わった(?)と思うので、ここでは実際にコードを書いて実行してみようと思います。ここで準備していただきたいのがGoogleColaboratoryです。  
Google Driveにて、新規 > その他 からファイルを作成できるのですが、現在はGoogleColaboratoryの項目がないと思います。そのため、新規 > その他 > アプリを追加　を押し、Colaboratoryを検索してインストールしてください。インストールが終わると 新規 > その他 にGoogleColaboratoryが追加されていると思います。こちらからファイルを作成すればそこにコードを書いて実行できます。  

以下の作業は[Java初心者のためのPython×競技プログラミング入門Day1.ipynb](https://colab.research.google.com/drive/15wbCui49Y9Ohb261tLlXNebwfoLTi4Cx?usp=sharing)から実行していただけるのですが、GoogleColaboratoryは今後の作業で使っていただきます。  

Day1ではよく使う文法や関数の紹介のみして、明日以降詳しく説明しようと思います。今日はとりあえず、上記のファイルから実行してみてください。  
できる方は、変数の値を変えたり、for文の中にfor文を書いてみたりするといいかもしれません。

## まとめ
今日は以上となります。短いですが、文章を書くのは結構大変ですね。たくさんの記事を書いている方のすごさを再確認できました。