Java筆記
===

物件導向(特別厲害)
===

在java當中撰寫的程式基本上都是由物件所組成 所以須具備物件導向概念，現在就來基本的認識一下物件

類別與實例說明
---

在物件導向當中，**類別就是產品的設計圖，物件就是依照設計圖做出來的產品**

類別
---

在這段程式碼中 **class就是我們所定義的類別**
最基本的類別會包含定義(屬性)+**呼叫自己的建構式(與類別同名的方法)**

``` java
class Clothes2 {
  String color;
  char size;

  // 創建建構式+定義
  Clothes2(String color, char size) {
    this.color = color;
    this.size = size;
  }
}
```

物件
---
Q：既然知道了怎麼建立類別，那要怎麼建立物件實例呢?
A：在建立物件實例時，我們會使用new這個關鍵字來操作
請看以下範例

``` java
    var sun = new Clothes2("red", 's');
    var spring = new Clothes2("green", 'M')
```

以JAVA專業術語來說，這叫宣告參考名稱(Reference name)、參考變數(Reference variable)或叫做直接參考(Reference)。
用物件導向的術語來說，這叫**新建一個物件/新建一個類別的實例**

最終
---

組合一個完整程式碼

``` java
class Clothes2 {
  String color;
  char size;

  // 創建建構式+定義
  Clothes2(String color, char size) {
    this.color = color;
    this.size = size;
  }
}


class Main {
  public static void main(String[] args) {
    
    // 使用指定建構式建立物件
    var sun = new Clothes2("red", 's');
    var spring = new Clothes2("green", 'M');

    System.out.printf("sun (%s, %c)%n", sun.color, sun.size);
    System.out.printf("spring (%s, %c)%n", spring.color, spring.size);
  }
}
```

執行這段程式會在cmd顯示

    sun (red, s)
    spring (green, M)



