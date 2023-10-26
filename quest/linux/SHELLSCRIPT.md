# シェルスクリプトを書くことができる

## 1. Hello

シェルスクリプトのファイルを作成し、「Hello!」と出力してください。

なお、シェルスクリプトを実行する際にはファイルに実行権限が付与されている必要があることに気を付けてください。
<br>
<br>
1. vimでシェルスクリプトファイルHello.shを作成、編集する。
```
$ vim Hello.sh
```
2. シェルスクリプトのファイルの１行目にしたの文字列を書きます。
```
#!/bin/bash
```
3. この文字列をシバンと言います。そのシバンの下以降に「Hello!」と出力される処理を書き、保存します。
```
#!/bin/bash

echo "Hello!"
```
4. そのあと、下のコマンドで実行権限を付けます。
```
$ chomod +x Hello.sh
```
5. 最後に、Hello.shを下のコマンドで実行してみる。うまくいけば「Hello!」と出力される。
```
$ ./Hello.sh
```

## 2. 標準入力から値を受け取る

シェルスクリプトのファイルに「What's your name?」と出力し、ユーザーに名前の入力を求めます。その後ユーザーが入力した名前に対して、「Welcome, $name!」（$name は入力された名前）と出力する処理を追加してください。
```
#!/bin/bash

echo "What's your name?"
read name

echo "Welcome, $name!"
```



## 3. 条件分岐

四則演算を行う電卓を作成してください。実行すると以下の挙動になります。

```bash
Enter two numbers:
10 # ユーザーが入力
11 # ユーザーが入力
Choose an arithmetic operation (+, -, *, /):
+ # ユーザーが入力
The result:21
```

なお、割り算の時の割る数が 0 であるケースや、演算子の記号 +, -, *, / が合致しないケースを考慮するかは任意とします。
```
#!/bin/bash

echo "Enter two numbers:"
read num1
read num2

echo "Choose an arithmetic operation (+, -, *, /):"
read operation

case "$operation" in
    "+")
        result=$((num1 + num2))
        ;;
    "-")
        result=$((num1 - num2))
        ;;
    "*")
        result=$((num1 * num2))
        ;;
    "/")
        # 0での割り算をできなくする
        if [ "$num2" -eq 0 ]; then
            echo "ゼロによる除算はできません."
            exit 1
        fi
        result=$(bc -l <<< "scale=2; $num1 / $num2")
        ;;
    *)
        echo "無効な演算子"
        exit 1
        ;;
esac


echo "The result: $result"
```


## 4. 繰り返し処理

for 文 または while 文を利用して、1~100までのうち、偶数の数字を表示する処理を書いてください。以下の結果が出力されます。

```bash
2 4 8 ... 100
```
For文の場合
```
#!/bin/bash

for ((num=2; num<=100; num+=2))
do
    echo $num
done
```
While文の場合
```
#!/bin/bash

num=1

while [ $num -le 100 ]
do
    if [ $((num % 2)) -eq 0 ]; then
        echo $num
    fi
    num=$((num + 1))
done
```

