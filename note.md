Java筆記
===


[![hackmd-github-sync-badge](https://hackmd.io/zzWDJExySwu-zrd5RRCIKQ/badge)](https://hackmd.io/zzWDJExySwu-zrd5RRCIKQ)

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

LinkedList
---
``` java=
package alexlin7.nutc;

public class SimpleLinkedList {
	
	private class Node {
		Node(Object o) {
			this.o = o;
		}
		Object o;
		Node next;
	}
	
	private Node first;
	
	public void add(Object elem) {
		var node = new Node(elem);
		if(first == null) {
			first = node;
		}
		else {
			append(node);
		}
	}
	
	private void append(Node node) {
		var last = first;
		while(last.next != null) {
			last = last.next;
		}
		last.next = node;
	}
	
	public int size() {
		var count = 0;
		var last = first;
		while(last != null) {
			last = last.next;
			count++;
		}
		return count;
	}
	
	public Object get(int index) {
		checkSize(index);
		return findElemOf(index);
	}
	
	private void checkSize(int index) 
                                throws IndexOutOfBoundsException {
		var size = size();
		if(index>=size) {
			throw new IndexOutOfBoundsException(
					String.format("index: %d, Size: %d", index, size));
		}
	}
	
	private Object findElemOf(int index) {
		var count = 0;
		var last = first;
		while(count < index) {
			last = last.next;
			count++;
		}
		return last.o;
	}
	
	
}
```

# Lambda

## 標準API介面

> 標準API介面是在JDK8的時候所定義的通用函式介面 </br>
> 基本上都建議先使用這些通用函式介面來撰寫程式
>
統用函式介面如下
1. Consumer
3. Function
4. Predicate
5. Supplier

### Consumer
> 接受一個傳入的引數 處理完不回傳 </br>
> 通常會用來輸出值或改變物件狀態

Consumer定義
``` java=
package java.util.function;

import java.util.Object;

@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
    ...
}
```

### Function
> 就像數學式 f(x) = y 我傳入值 會得到回傳值 </br>
> 當需要接受一個引數執行完並回傳結果 就可以使用Function

Function定義
``` java=
package java.util.function;

import java.util.Object;

@FunctionalInterface
public interface Function<T, R> {
    //T為傳入值 ,R為回傳值
    R accept(T t);
    ...
}
```

### Predicate
>傳入一個引數 然後自己寫一個判斷式判斷是不是我們要的
>最後回傳Boolean

Predicate定義

``` java=
package java.util.function;

import java.util.Object;

@FunctionalInterface
public interface Predicate<T> {
    //T為傳入值 回傳型別為Boolean
    Boolean accept(T t);
    ...
}
```

### Supplier
>不接受任何引數並回傳值
>也就是說只要呼叫 他就動作

Supplier定義
``` java=
package java.util.function;

import java.util.Object;

@FunctionalInterface
public interface Supplier<T> {
    //無傳入值 並回傳
    T get();
    ...
}
```
# Spring boot

只配置maven而不使用spring initilizr的話

## maven配置

要先在maven專案下的pom.xml新增兩項東西

![](https://i.imgur.com/aXtxEFb.png)

parent 此項目告訴我們繼承的父類別為spring-boot-starter-parent

dependencies 看名字就知道 就是依賴</br>
他告訴maven我們需要下載(注入)哪些依賴來調入我們的專案lib中</br>


## 主程式

我們要在src資料夾內新增我們的Application</br>
大概像這樣

![](https://i.imgur.com/aJZlSis.png)

class上的註解@SpringBootApplication用來告訴spring</br>
**這是springboot的主程序 </br>
而他將會幫我們自動配置、掃描、註冊組件...等等(後面會講</br>
而你不能在有這個這個註解的情況下</br>
@EnableAutoConfiguration註解不然IDE會直接報錯給你看</br>

再來就是main方法內的執行ㄌ </br>
SpringApplication.run是在</br>
org.springframework.boot.SpringApplication內的static方法</br>
~~反正就 讓他跑起來~~</br>
~~讓甚麼跑起來 讓編譯後的MyApplication.class跑起來~~</br>
**2022/4/16更正**</br>
在intellij內以alt+enter 點introduce local variable

![](https://i.imgur.com/b2xYqdm.png)

你會看到其實它的作用為返回IoC容器</br>
而這個IoC容器內的組件已經透過Spring boot的自動配置幫我們配置好了</br>

我們將IoC內部的組件全部顯示到terminal上
![](https://i.imgur.com/kE0ujSb.png)

termainl畫面

![](https://i.imgur.com/aUJg64R.png)

你會看到在日誌下印出來的是我們呼叫出來的組件名 </br>
你也會了解到說spring boot到底為我們簡化了多少流程

## Controller

![](https://i.imgur.com/O1Z6Xef.png)

一個最基本的Controller大概就這麼寫 跟asp.net差不多</br>
上面的標註基本上就都告訴我們跟Spring 這是甚麼物件了</br>

比較重要的標註:

### @RestController

在spring boot 的doc內是這樣寫的</br>
>The @RestController annotation tells Spring to render the resulting string directly back to the caller.
>[來自 <4.3.1. The @RestController and @RequestMapping Annotations>](https://docs.spring.io/spring-boot/docs/current/reference/html/getting-started.html#getting-started.first-application.code.mvc-annotations) 

意思就是說，這會告訴spring:將這個function生成出來的內容轉為字串回傳給調用者。</br>
 
### @RequestMapping

在這個標註後方的括弧內 放的是route 也就是路由</br>
在asp.net會放在單翼資料夾內 這邊的話是放在標註後 不過也有可能只是暫時 之後大概會有跟方便的寫法</br>
甚至就跟asp.net一樣 直接獨立出來</br>

而這支程式的邏輯就很簡單</br>
我切到網站的/hello內</br>
spring就會return一個request</br>
而我們request會傳回一組字串</br>

## 深入解析pom.xml
今天就是要來深入探討pom文件內 我們所放入的tab到底包含了些甚麼</br>
首先與昨日一樣 先來看parent標籤內的內容 

![](https://i.imgur.com/fvGEnmm.png)

我們可以看到 在artifactId內寫著 spring-boot-starter-parent</br>


![](https://i.imgur.com/N8ZG7Si.png)

我們會看到 在我們繼承的項目當作 還有繼承了spring-boot-dependencies</br>
這裡點開來 就是spring-boot內的依賴的版本號

![](https://i.imgur.com/UmLjq6P.png)

由於在marven設定文件當中就已經寫好自動配置時要使用的API版本</br> 
於是可以達到自動管理的 spring boot內的所有依賴(沒有寫在denendencies裡面的就是另外一回事了)</br>
所以他就是一個**版本管理中心**</br>

接下來我們來看到dependencies標籤內的

![](https://i.imgur.com/nR8wUq9.png)

這裡我們會看到artifactId內的文字當中有一串文字寫著 starter</br>
顧名思義 就是啟動器</br>
點進去看我們會看到我們要實作web時所需要的依賴包 </br>
**根據maven的依賴傳遞原則** 我們透過denpendency導入這個starter</br>
我們就能將注入的依賴透過marven來進行管理

![](https://i.imgur.com/OaWa6Ex.png)

若以後需要增加甚麼功能(或者老闆說要你幹嘛幹嘛)的話就到spring boot的官方文件搜尋starter </br>
我們就可以看到 官方預先設定好 幫我們配置完的 各種所需要的依賴模板</br>
[Spring-Boot-starter](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.build-systems.starters)
![](https://i.imgur.com/ulqjPEV.png)

>**補充說明** </br>
>spring-boot-starter-* 為官方提供的模板</br>
>*-spring-bppt-start- * 這就是別人寫的或是我們自己寫的

## 依賴管理補充

如果不想使用預設定義引入的version
你可以在pom.xml這樣寫
```xml=
<properties>
    <要改的依賴.version>版本號</要改的依賴.version>
</properties>
```
為何可以這樣改? maven的特性 **就近優先原則**</br>

因為我已經在我的pom內寫入我要配置的版本
否則的話他會使用由父項目繼承下來的依賴(但如果你要引入的jar不在他預設內 那你還是要寫你要配置的版本)

又或者是到application.properties內修改

![](https://i.imgur.com/yQzTClz.png)

但是這樣在日後修改版本或更新時會不好修 所以還是到pom.xml內會比較方便

## 分析依賴樹

想知道自己依賴到底有甚麼嗎
就來這裡

打開你的pom.xml
![](https://i.imgur.com/xhoQx1L.png)

右鍵->show dependencies

![](https://i.imgur.com/LJkezN8.png)

然後你就能看到你的依賴樹ㄌ

![](https://i.imgur.com/v0VGhmL.png)


## Spring boot 主程式標籤解析

有點複雜 需要消化一下

![](https://i.imgur.com/xImW2oV.png)

### @SprongBootApplication

首先我們來解析@SpringBootApplication這個標籤

![](https://i.imgur.com/xBbXABE.png)

點進來之後你會發現到這裏也有很多標籤</br>
其中我們所需要特別關注的是
1. @SpringBootConfiguration
2. @EnableAutoConfiguration
3. @ComponentScan

### @SpringBootConfiguration:SpringBoot的配置

![](https://i.imgur.com/QhzwYhg.png)

點進來後我們會發現到還有一個@Configuration標籤 我們再點進去

![](https://i.imgur.com/2Ya3bCy.png)

真相大白 其實他是一個Component</br>
也就是說 我們把我們的配置文件做成Component來置入我們的專案當中</br>
然後因為我們沒有學spring 我是直接學spring boot的，~~所以我並不知道spring的配置文就有多難寫~~</br>

### @EnableAutoConfiguration:啟用自動配置

這個部分最複雜了 妳各位小心

![](https://i.imgur.com/tJioOMX.png)

要看的內容:
1. @AutoConfigurationPackage
2. AutoConfigurationImportSelector.class

#### @AutoConfigurationPackage

我們先來看這個@AutoConfigurationPackage(自動配置包)

![](https://i.imgur.com/1s9hAJb.png)

在這個包內有個@import註解  我們來點開他import的Registrar.class

``` java = 
static class Registrar implements ImportBeanDefinitionRegistrar, DeterminableImports {
        Registrar() {
        }

        public void registerBeanDefinitions(AnnotationMetadata metadata, BeanDefinitionRegistry registry) {
            AutoConfigurationPackages.register(registry, (String[])(new AutoConfigurationPackages.PackageImports(metadata)).getPackageNames().toArray(new String[0]));
        }

        public Set<Object> determineImports(AnnotationMetadata metadata) {
            return Collections.singleton(new AutoConfigurationPackages.PackageImports(metadata));
        }
    }
```

在這個class檔下方 你會看到說其實他引入了兩個方法</br>
 一個是註冊用來Bean(給容器導組件:以MyApplication的Package向下的組件)</br>
另一個是決定Import的metadata(元資料) </br>
至此 也就是說@AutoConfigurationPackage這個註解可以用來決定導入的配置文件</br>
~~再更深入一點的內容我就不懂了 之後在學~~</br>

#### AutoConfigurationImportSelector.class(直譯:自動配置引入選擇器)

用來選擇要引入的自動配置包</br>
將所有需要導入的組件以全類名的方式return，然後組件就會添加到容器中
配置類包名**org.springframework.boot.autoconfigure**</br>

![](https://i.imgur.com/r4eYT35.png)

你所需要的配置基本上都在這裡</br>
要是spring boot官方給的配置不滿意</br>
你還能參考配置文件 修改出一個屬於自己的配置

### @ComponentScan:組件掃描

先來看一下官方給我們的 專案結構圖

![](https://i.imgur.com/EjjBvqm.png)

[連結](https://docs.spring.io/spring-boot/docs/current/reference/html/using.html#using.structuring-your-code)

你會發現到說其實結構是從我們的主程式一路向下的</br>
而如何掃描我們組件是否在主程式向下的位置?</br> 
就要透過@ComponentScan來設定掃描位置

![](https://i.imgur.com/76gHajg.png)


## 改學spring boot 2.xx版啦 
發現這兩天看的Spring boot是1代的</br>
而現在已經2代快要換三代了 趕快換學2</br>


將雷神對spring boot 2的開頭介紹看過了一遍 基本上跟一代的介紹差不多 最多就加上了如何看原文件</br>

[雷神的spring boot 2教學(b站)](https://www.bilibili.com/video/BV19K4y1L7MT?p=6&share_source=copy_web)

## applicaton.properties

這是用來設定spring boot內依賴的設定檔</br>
老話一句 我沒學過spring or smm</br>
所以我不知道之前的xml設定地獄到底有多可怕</br>
但是我知道只要有了這個，不過你是想要設定tomcat還是甚麼其他的</br>
只要上到官方文檔中找相關聯的設定 </br>
然後丟到這個檔案當中重啟spring boot 就能夠修改你要的設定</br>
(看B站彈幕 一堆人說他流下了眼淚)</br>

![](https://i.imgur.com/gVzAkA7.png)

放在src的resources資料夾

![](https://i.imgur.com/1B8tXZA.png)

例如我現在設定我要把port號改到12300port去執行</br>
然後重啟spring boot</br>

![](https://i.imgur.com/oQx3H60.png)

我們就會看到 tomcat已經幫我們在12300port開好端口了</br>

![](https://i.imgur.com/I5MtWiz.png)


原理:
1. 透過反射將配置反射到設置文件的properties上
2. 最終的配置結果會綁定到配置後的類別上，在IoC容器中創建物件
