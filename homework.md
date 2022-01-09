---
tags: diaries
---

# Java 作業

> 大二上學期的java作業 
> 
> 每題都有一個題目敘述、參考解答及我的程式碼
> 
> 如果覺得不傷眼的話可以參考一下
> 
> 就一下而已
> 
> 使用程式:eclipse
> 
> JDK版本:16.0.1



## 06

:::spoiler {state="close"}  01-周年慶禮券(課堂練習)
#### 題目描述
假設某百貨公司周年慶活動，購物滿10000元送1000元禮券，滿20000元送2000元禮券，以此類推。寫一程式，輸入購物金額，輸出禮券。
#### 參考答案
範例1:
《輸出》請輸入購物金額：《輸入》56000
《輸出》恭禧您獲得禮券：5000元

#### 程式碼
``` java =
package s1410931031;
import java.util.Scanner;

public class s1410931031 {
    public static void main(String[] args) {
        int money = 0;
        int price = 0;
        
        System.out.print("請輸入購物金額：");
        var console = new Scanner(System.in);
        money = console.nextInt();
        console.close();
        
        if(money>=10000){
            price = money / 10000;
            System.out.println("恭喜您獲得禮券：" 
                               + price * 1000 + "元");
        } 
    }
}

```
:::
## 07

:::spoiler {state="close"}  01-工讀金(課堂練習)

#### 題目描述
假設某加油站的工讀金，依照下列方式計算：
60個小時以內，每小時98元，61~80個小時，每小時工讀金以1.2倍計算，超過80個小時之後，每小時工讀金以1.5倍計算。
寫一程式，輸入工讀生的工作時數，輸出實領的工讀金
#### 參考答案
範例1:
請輸入工讀時數：30
30小時的工讀金為 2940元

範例2:
請輸入工讀時數：70
30小時的工讀金為 7056元

#### 程式碼
``` java=
package s1410931031;

import java.util.Scanner;

public class s1410931031 {

	public static void main(String[] args) {
		var console = new Scanner(System.in);
		System.out.print("請輸入打工工時 :");
		int hour = console.nextInt();
		double money = 0;
		
		if(hour<60) {
			money = hour * 98;
		}
		else if(hour<80) {
			money = ( 60 * 98 ) + ( hour - 60 ) * ( 98 * 1.2); 
		}
		else {
			money = ( 60 * 98 ) + 20 * ( 98 * 1.2) + ( hour - 80 ) * ( 98 * 1.5 ); 
		}
		System.out.print("薪水: " + (int) money + "元");
		
		console.close();
		

	}

}

```
:::
## 08

:::spoiler {state="close"}  01-分數相加(課堂練習)

#### 題目描述
使用迴圈敘述撰寫程式，使用者輸入小於100的正整數n，計算：
     1  +  1/2  +  1/3 +  1/4  +   …   +  1/n  之和
#### 參考答案
《輸出》請輸入一個整數: 《輸入》50
《輸出》1+ 1/2 + … + 1/50 = 4.4992056

#### 程式碼
``` java=
package s1410931031;

import java.util.Scanner;

public class number {

	public static void main(String[] args) {
		var console = new Scanner(System.in);
		double sum = 0;
		int n = 0;

		do {
			System.out.print("請輸入n(小於100的正整數):");
			n = console.nextInt();
		} while(n >= 100 || n <= 0);
		
		for(int i = 1; i <= n; i++) {
			sum += (1 / (double) i);
		}
		System.out.print(sum);
		console.close();
	}

}

```
:::
:::spoiler {state="close"}  02-紙鈔兌換(課堂練習)

#### 題目描述
假設有一提款機只提供1元、10元、100元三種紙鈔兌換。
模擬提款機作業，輸入提領金額，輸出1元、10元、100元三種紙鈔各兌的數量 (總數最少)。
#### 參考答案
《輸出》輸入提領金額:《輸入》256
《輸出》兌換100元紙鈔2張，10元紙鈔5張，1元紙鈔6張

#### 程式碼

``` java=
package s1410931031;

import java.util.Scanner;

public class ans2 {
	
	public static void main(String[] args) {
		var console = new Scanner(System.in);
		int money = 0;
		int i100 = 0;
		int i10 = 0;
		int i1 = 0;
		System.out.print("請輸入你要換的面額");
		money = console.nextInt();
//		i100 = money / 100;
//		i10 = (money % 100) / 10;
//		i1 = money % 10;
		
		while(money >= 100) {
			money -= 100;
			i100++;
		} 
		
		while(money >= 10) {
			money -= 10;
			i10++;
		} 
		
		while(money >= 1) {
			money -= 1;
			i1++;
		} 
		
		System.out.println("100面額張數:" + i100 );
		System.out.println("10面額張數:" + i10 );
		System.out.println("1面額張數:" + i1 );
		console.close();
	}

}

```
:::
## 09
:::spoiler {state="close"}  01-學生姓名與成績(課堂練習)

#### 題目描述
輸入學生人數n，再輸入n次學生的姓名和成績，使用二維陣列存放。完成輸入後，再顯示成績總和及平均數。

提示：陣列內只能放相同資料型別的資料，故成績必須使用字串存入陣列。
#### 參考答案
《輸出》輸入學生人數：《輸入》 5
《輸出》輸入第1位學生姓名和成績(空白間隔)：《輸入》Amy 95
《輸出》輸入第2位學生姓名和成績(空白間隔)：《輸入》Brown 70
《輸出》輸入第3位學生姓名和成績(空白間隔)：《輸入》Bob 80
《輸出》輸入第4位學生姓名和成績(空白間隔)：《輸入》John 72
《輸出》輸入第5位學生姓名和成績(空白間隔)：《輸入》Tom 91
《輸出》成績總和 = 408, 平均分數＝81.6

#### 程式碼
``` java =
package s1410931031;

import java.util.Scanner;

public class test1 {
	public static void main(String[] args) {
		int n = 0;
		int sum = 0;
		double avg = 0;
		var console = new Scanner(System.in);
		System.out.print("《輸出》輸入學生人數：《輸入》");
		n = console.nextInt();
		String[][] student = new String[n][2];
		for(int i = 0; i < n; i++) {
			System.out.print("輸入第" + (i + 1) + "位學生姓名和成績(空白間隔)：《輸入》");
			student[i][0] = console.next();
			student[i][1] = console.next();
			sum = sum + Integer.parseInt(student[i][1]);
		}
		avg = (double) (sum) / n;
		System.out.print("成績總和 = " + sum + ", 平均分數 ＝ " + avg);
		console.close();
		
		
	}
}

```
:::
:::spoiler {state="close"}  02-數字格式化

#### 題目描述
提示使用者輸入一個整數。
將數字每三位以逗號進行分隔並輸出。

註: 本題可以使用陣列暫存數字。
#### 參考答案
《輸出》輸入一個整數：《輸入》12345678
《輸出》12,345,678

#### 程式碼

``` java =
import java.util.Scanner;
import java.text.DecimalFormat;

class Main {
  public static void main(String[] args) {
    var console = new Scanner(System.in);
    var decimalFormat = new DecimalFormat("#,###");

    System.out.print("輸入一個整數：");
    long input = console.nextLong();
    String formatNumber = decimalFormat.format(input);
    System.out.print(formatNumber);
    console.close();
  }
}
```
:::
:::spoiler {state="close"}  03-找出最大數

#### 題目描述
提示使用者輸入多個數字( 3~10，以空白隔開)。
輸出最大數。

#### 參考答案
《輸出》請輸入3~10個數字，以空白隔開：《輸入》0 0 0 0 1 -5 -200 3 6
《輸出》最大值為 6

#### 程式碼
``` java=
import java.util.Scanner;

public class main {
    public static void main(String[] args) {
        var console = new Scanner(System.in);
        System.out.print("請輸入3~10個數字，以空白隔開： ");
        String input = console.nextLine();
        var console2 = new Scanner(input);
        int max = console2.nextInt();
        int number;
        while(console2.hasNext()){
            number = console2.nextInt();
            if(number > max) {
                max = number;
            }
        }
        System.out.print("最大值為 " + max);
        console.close();
        console2.close();

    }
}

```
:::
## 10
:::spoiler {state="close"}  01-座標距離(課堂練習)

#### 題目描述
寫一程式，輸入平面座標上的任意兩點，輸出兩點的距離。
提示：座標兩點距離：((𝑥1−𝑥2 )^2+(𝑦1−𝑦2 )^2 ) 再開根號。
#### 參考答案
《輸出》請輸入第1點座標 x y (空白隔開):《輸入》 4 6 
《輸出》請輸入第2點座標 x y (空白隔開):《輸入》 7 2
《輸出》兩點座標的距離為: 5

#### 程式碼

``` java=
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    int[] x = new int[2];
    int[] y = new int[2];
    double d;
    var console = new Scanner (System.in);
    for(int i = 0; i < 2; i++) {
      System.out.println("請輸入第" + (i+1) + "點座標");
      x[i] = console.nextInt();
      y[i] = console.nextInt();
    }
    d = Math.sqrt((x[0] - x[1]) * (x[0] - x[1]) + (y[0] - y[1]) * (y[0] - y[1]));
    System.out.println("兩點座標的距離為: " + d);
    console.close();
  }
}
```
:::
:::spoiler {state="close"}  02-加法練習(課堂練習)

#### 題目描述
由使用者輸入兩個浮點數，再請使用者輸入這兩個數字的和(round到整數)。
若答錯，則顯示 "答案錯誤, 再試一次"，繼續提示並請使用者作答；
若答對，則回饋 "答對了, 你好棒!" 並結束迴圈。
(使用 break)
#### 參考答案
《輸出》請輸入第1個浮點數:《輸入》 46.1 
《輸出》請輸入第2個浮點數:《輸入》 72.3
《輸出》46.100000+72.300000=(整數) 《輸入》100
《輸出》答案錯誤, 再試一次
《輸出》46.100000+72.300000=(整數) 《輸入》118
《輸出》答對了, 你好棒!

#### 程式碼
``` java=
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    var console = new Scanner (System.in);
    double[] inputs = new double[2];
    double ans = 0;
    int yourAns;


    for(int i = 0; i < 2; i++) { 
      System.out.print("請輸入第" + (i+1) + "個浮點數");
      inputs[i] = console.nextDouble();
      ans += inputs[i];
    }
    while(true) {
      System.out.print(inputs[0] + "+" + inputs[1] + "=");
      yourAns = console.nextInt();
      if(yourAns == Math.round(ans)) {
        System.out.println("答對了, 你好棒!");
        break;
       }
      else {
        System.out.println("答案錯誤, 再試一次");
      }
    }
    console.close();
 
  }
}
```
:::
:::spoiler {state="close"}  03-兩數運算

#### 題目描述
寫一程式，輸入一個數學運算式。運算式內只有兩數進行 + 或 - 或 * 或 /。
判斷數學運算子後，進行正確的運算。
提示：
1. 先找到運算子，可用 indexOf() 找四個運算子是否存在。
2. 若找到則將字串拆成兩個數字(字串型態)，可用split()或substring()
3. 將兩數轉為整數後，進行運算。
#### 參考答案
[範例1]
 《輸出》輸入數學運算式: 《輸入》5+90
《輸出》5+90=95

[範例2]
《輸出》輸入數學運算式: 《輸入》9999-90
《輸出》9999-90=9909

#### 程式碼

``` java=
package s1410931031;
import java.util.Scanner;


public class Test2 {

	public static void main(String[] args) {
		var console = new Scanner(System.in);
		String str1;
		int c, d;
		int ans = 0;
		int temp;
		System.out.print("請輸入運算式");
		str1 = console.next();
		
		int index = 0;
		String[] str2 = {"+", "-", "*", "/"};
		for(int i = 0; i < str2.length; i++) {
			temp = str1.indexOf(str2[i]);
			if(temp != -1) {
				index = temp;
				break;
			}
		}
		String a = str1.substring(0, index);
		String b = str1.substring(index+1, str1.length());
		c = Integer.parseInt(a);
		d = Integer.parseInt(b);
		String e = str1.substring(index, index+1);
		System.out.print(a + e + b + "=");
		switch (e) {
			case "+":
				ans = c+d;
				break;
			case "-":
				ans = c-d;
				break;
			case "*":
				ans = c*d;
				break;
			case "/":
				ans = c/d;
				break;
		}
		System.out.print(ans);
	}

}

```
:::
:::spoiler {state="close"}  04-句子之個數加總(課堂練習)

#### 題目描述
寫一程式，輸入一字串，以逗點隔開。判斷逗點間的子字串是 String 還是 digit, 並做計數。
輸出文字的個數、數字的個數、和數字的加總。
[提示]：
1. 使用 nextLine() 取得整行後, 使用 split() 用逗點拆解
2. 使用兩層迴圈, 外層一一讀取拆解後的子字串, 內層迴圈判斷子字串中的字元是否是數字, 只要其中一個不是數字, 這個子字串就是String (不考慮小數)
3. 若是String, 則String的計數+1
4. 若是digit, 則digit的計數+1, 再將子字串轉換為整數並累加到總數

#### 參考答案
《輸出》輸入一句英文句子:《輸入》 I,100,you,90,she,101,happy
《輸出》共有4個英文字, 3個數字, 數字總計291

#### 程式碼

``` java=
package ss1525;

import java.util.*;

public class sss {
	public static void main(String[] args) {
		int str = 0, digit = 0, sum = 0;
		var console = new Scanner(System.in);
		boolean isNumeric = true;
		System.out.print("輸入一句英文句子: ");
		String str1 = new String(console.nextLine());
		String[] str2 = str1.split(",");
		for(var i : str2) {
			isNumeric = true;
			for (int j = 0; j < i.length(); j++) {
				if (!Character.isDigit(i.charAt(j))) {
					if (i.charAt(j) == '-') {
						isNumeric = true;
						break;
					}
					isNumeric = false;
					break;
					
	            }
		            
	        }
			if(isNumeric) {
				digit++;
				sum += Integer.parseInt(i);
			}
			else {
				str++;
			}
	//		if(i.matches("[+-]?\\d*(\\.\\d+)?")) {
	//			digit++;
	//			sum += Integer.parseInt(i);
	//		}
	//		else {
	//			str++;
	//		}
					
		}
		System.out.print("共有" + str + "個英文字," + digit +"個數字, 數字總計" + sum);

	}
}
```
:::
:::spoiler {state="close"}  05-解碼器

#### 題目描述
在密碼學裡面有一種很簡單的加密方式，就是把明碼的每個字元的ASCII碼加上某一個整數K而得到密碼的字元（明碼及密碼字元一定都在ASCII碼中可列印的範圍內）。
例如若K=2，那麼apple經過加密後就變成crrng了。解密則是反過來做。
程式要求如下:
1. 使用者選擇 1->加密、2->解密。(輸入其他值則結束程式)
2. 使用者輸入要加密或解密的字串。
3. 使用者輸入K值。
4. 系統輸出加密或解密後的字串。
#### 參考答案
範例1
《輸出》請選擇 1->加密、2->解密:《輸入》1
《輸出》請輸入要加密的字串:《輸入》learning java is fun.
《輸出》請輸入密碼:《輸入》9
《輸出》加密後字串: unj{wrwp)sjj)r|)o~w7

範例2
《輸出》請選擇 1->加密、2->解密:《輸入》2
《輸出》請輸入要解密的字串:《輸入》unj{wrwp)sjj)r|)o~w7
《輸出》請輸入密碼:《輸入》9
《輸出》解密後字串: learning java is fun.

#### 程式碼

``` java=
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    Scanner keyin = new Scanner(System.in);
    int select;
    String input;
    int psw;

    System.out.println("請選擇 1->加密、2->解密: ");
    select = keyin.nextInt();
    keyin.nextLine(); //抵銷nextLine 換行bug
    switch (select) {
      case 1 :
        System.out.print("請輸入要加密的字串: ");
        input = keyin.nextLine();
        System.out.print("請輸入密碼: ");
        psw = keyin.nextInt();
        Encryption(input, psw);
        break;
      
      case 2 :
        System.out.print("請輸入要解密的字串: ");
        input = keyin.nextLine();
        System.out.print("請輸入密碼: ");
        psw = keyin.nextInt();
        Decryption(input, psw);
        break;
    }

    keyin.close();
  }

  static void Encryption(String input, int psw) {
    byte[] strBytes = input.getBytes();
    for( int i = 0; i < strBytes.length; i++) {
      strBytes[i] += psw;
    }
    String targetStr = new String(strBytes);
    System.out.println( "加密後字串:  " + targetStr);
  }

  static void Decryption(String input, int psw) {
    byte[] strBytes = input.getBytes();
    for( int i = 0; i < strBytes.length; i++) {
      strBytes[i] -= psw;
    }
    String targetStr = new String(strBytes);
    System.out.println( "解密後字串: " + targetStr);
  }
}
```
:::
## 11
:::spoiler {state="close"}  01-骰子點數和統計(課堂練習)

#### 題目描述
使用亂數方法來模擬擲兩個骰子的動作，擲100次後，分別輸出點數和為2,3,…,12的次數。
#### 參考答案
《每次執行結果不同》
亂數擲兩個骰子擲100次後，點數和的次數:
點數為2共出現3次
點數為3共出現7次
點數為4共出現9次
點數為5共出現7次
點數為6共出現12次
點數為7共出現16次
點數為8共出現14次
點數為9共出現14次
點數為10共出現10次
點數為11共出現4次
點數為12共出現4次　

#### 程式碼

``` java=
package s1410931031;

public class test1 {

	public static void main(String[] args) {
		int[] sum = new int[13];
		int d1,d2;
		for(int i = 0 ; i < 100; i++) {
			d1 = (int)(Math.random()*6+1);
			d2 = (int)(Math.random()*6+1);
			sum[(d1+d2)]++;
		}
		System.out.println("亂數擲兩個骰子擲100次後，點數和的次數:");
		for(int i = 2; i < 13; i++ ) {
			System.out.println("點數為" + i + "共出現" + sum[i] + "次");
		}
	}

}

```
:::
:::spoiler {state="close"}  02-Arrays sort(課堂練習)

#### 題目描述
利用Arrays類別的sort方法，將二維陣列的第０列元素{1,3,5,4,6}及第1列元素{7,5,9,6,8}，各自從小排到大後，再利用foreach迴圈結構將二維陣列顯示在螢幕。

提示: 記得使用 import Arrays 類別
#### 參考答案
1 3 4 5 6
5 6 7 8 9
#### 程式碼
``` java=
package s1410931031;

import java.util.*;

public class test3 {
	public static void main(String[] args) {
		int[][] array = {{1,3,5,4,6}, {7,5,9,6,8}};
		
		for(var i : array) {
			Arrays.sort(i);
			for(var j : i) {
				System.out.print(j + " ");
			}
			System.out.println();
		}
		
	}

}

```
:::
## 13

:::spoiler {state="close"}  01-分數加總並化簡

#### 題目描述
提示使用者輸入兩組分數。
將兩個分數加總，並簡化為最簡分數。
#### 參考答案
《輸出》請輸入第一個分數:《輸入》1/2　
《輸出》請輸入第二個分數:《輸入》1/6　　　
《輸出》1/2 + 1/6 = 4/6 = 2/3
#### 程式碼
``` java=
package alexlin7.nutc;

import java.util.Scanner;

public class Fraction {

	public static void main(String[] args) {
		
		Scanner keyin = new Scanner(System.in);
		String[] input = new String[2];
		String[][] spiltString = new String[2][2];
		int[][] a = new int[2][2];
		int x, y, z, z2, z3;
		
		for(int i = 0; i < input.length; i++) {
			System.out.print("請輸入第" + (i + 1) + "個分數:");
			input[i] = keyin.nextLine();
		}
		keyin.close();
		
		for(int i = 0 ; i < input.length; i++) {
			spiltString[i] = input[i].split("/");
			a[i][0] = Integer.parseInt(spiltString[i][0]);
			a[i][1] = Integer.parseInt(spiltString[i][1]);
		}
		
		x = a[0][0] * a[1][1] + a[1][0]*a[0][1]; //通分
		y = a[0][1] * a[1][1]; 
		z = gcd(x, y);//輾轉相除法球最大公因數
		z2 = lcm(a[0][1], a[1][1]);
		z3 = y/z2;
		System.out.printf("%d/%d + %d/%d = %d/%d = %d/%d", a[0][0], a[0][1], a[1][0], a[1][1], x/z3, y/z3, x/z, y/z);
		
	}
	private static int gcd(int a, int b) {
		if(b == 0) {
			return a;
		}
		else {
			return gcd(b, a%b);
		}
	}
	
	private static int lcm(int m, int n){
        int m1 = m;
        int n1 = n;
        while(m % n != 0){
            int tmp = m % n;
            m = n;
            n = tmp;
        }
        return m1*n1 / n;
    }
	




}

```
:::

:::spoiler {state="close"}  03-判斷質數

#### 題目描述
寫一個方法 isPrime (可以是static 或 不是static，注意呼叫方式不同)
    * 傳入一個整數
    * 方法中判斷傳入的數是否為質數。
    * 是質數回傳true, 不是質數回傳false
主方法中, 由使用者輸入一個數, 傳給 isPrime 判斷, 再顯示結果。
#### 參考答案
範例1
《輸出》請輸入一個整數：《輸入》3 
《輸出》3 是質數

範例2
《輸出》請輸入一個整數：《輸入》213596  
《輸出》213596 不是質數

範例2
《輸出》請輸入一個整數：《輸入》3331  
《輸出》3331 是質數

#### 程式碼
``` java=
package alexlin7.nutc;

import java.util.Scanner;

public class Prime {

	public static void main(String[] args) {
		Scanner keyin = new Scanner(System.in);
		System.out.print("請輸入一個整數：");
		int i = keyin.nextInt();
		keyin.close();
		if(isPrime(i)) {
			System.out.println(i + "是質數");
		} else {
			System.out.println(i + "不是質數");
		}
		
	}
	
	static boolean isPrime(int i) {
		int count = 0;
		if(i < 2) return false;
		if(i == 2) return true;
		
		for(int j = 1; j <= (i/2); j++) { 
			if(i % j == 0) count++;
			if(count>1) return false; 
		}
		return true;
		
	}

}

```
:::
:::spoiler {state="close"}  04-密碼規則判斷

#### 題目描述
寫一個方法 isValidPW (可以是static 或 不是static，注意呼叫方式不同)
    * 傳入一個字串(密碼)
    * 依以下規則判斷是否符合。
    * 符合回傳true, 不符合回傳false
    * 規則如下：
       1.	必須至少8個字元
       2.	只包含英文字母和數字
       3.	至少一個大寫英文字母

主方法中, 由使用者輸入一個字串, 傳給 isValidPW 判斷, 再顯示結果。
#### 參考答案
範例1
《輸出》請輸入密碼：《輸入》a12345
《輸出》無效密碼：a12345

範例2
《輸出》請輸入密碼：《輸入》123As123
《輸出》有效密碼：123As123

範例3
《輸出》請輸入密碼：《輸入》123as123
《輸出》無效密碼：123as123

範例4
《輸出》請輸入密碼：《輸入》123456789
《輸出》無效密碼：123456789

#### 程式碼
``` java=
package s1410931031;

import java.util.Scanner;

public class pwTest {

	public static void main(String[] args) {
		Scanner keyin = new Scanner(System.in);
		System.out.print("請輸入密碼：");
		String pw = keyin.nextLine();
		if(isValidPW(pw)) {
			System.out.print("有效密碼：" + pw);
		} else {
			System.out.print("無效密碼：" + pw);
		}
		
	}
	
	static boolean isValidPW(String pw) {
		int count = 0 ;
		byte[] strPW =  pw.getBytes();
		
		if(!(pw.length() >= 8)) return false;
		
		for(int i = 0; i < strPW.length; i++) {
			if(strPW[i] > 64 && strPW[i] < 91) {
				count++;
			} else if(!(strPW[i] > 96 && strPW[i] < 123)) {
				if(!(strPW[i] > 47 && strPW[i] < 58)) return false;
			}
		}
		
		if(count > 0 ) return true;
		return false;
	}
}

```
:::

## 14
:::spoiler {state="close"}  01-班級成績

#### 題目描述
寫一個類別 classroom，包含以下的內容
    * private的整數陣列 grade, 只宣告, 不分配空間。
    * 建構子傳入一個整數 n(代表學生人數), 在建構子內將 grade配置n的空間, 並初始化所有值為-1。
    * 方法setGrade傳入兩個整數, id是編號，g是成績, 設定grade[id-1]值為g, 無回傳值。
    * 方法getGrade無傳入值, 回傳 grade陣列。
    * 方法getEmpty無傳入值, 無回傳值, 將尚未輸入成績的編號印出在畫面上。

主類別中, 執行以下的工作
  1.	宣告一個classRoom的變數, 學生人數10。
  2.	給以下編號對應的成績:
         1->90, 2_>80, 5->70, 9->90, 3->50
  3.	取得學生的成績, 印出在畫面上。
4.	顯示尚未輸入成績的編號
#### 參考答案
已輸入成績：
1->90
2->80
3->50
5->70
9->90
尚未輸入成績：
4 6 7 8 10

#### 程式碼

``` java=
package s1410931031;



class classroom {
	private int[] grade;
	
	public classroom(int n){
		grade = new int[n];
		for(int i = 0 ; i < grade.length; i++) {
			grade[i] = -1;
		}
	}
	
	public void setGrade(int id, int g) {
		grade[id-1] = g;
	}
	
	public int[] getGrad() {
		return grade;
	}
	
	public void getEmpty() {
		System.out.println("尚未輸入成績：");
		for(int i = 0; i < grade.length; i++) {
			if (grade[i] < 0) {
				System.out.print( (i+1) + " ");
			}
		}
	}
}

public class myClass {

	public static void main(String[] args) {
		classroom c1 = new classroom(10);
		c1.setGrade(1, 90);
		c1.setGrade(2, 80);
		c1.setGrade(5, 70);
		c1.setGrade(9, 90);
		c1.setGrade(3, 50);
		int[] r = c1.getGrad();
		for(int i = 0; i < r.length; i++) {
			if(r[i] > -1 ) {
				System.out.println((i+1) + "->" + r[i]);
			}
		}
		c1.getEmpty();
		
	}
	

}

```
:::


