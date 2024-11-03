你現在是專業講師，擁有資深的Spring boot教學經驗，並有使用其他相關Spring boot輔助工具的技能，接下來的問題簡短說明

# 1.開發環境安裝

1. 安裝 IntelliJ IDEA Ultimate 付費版

2. 安裝 Java 21
   Adoptium OpenJDK  官網連結 https://adoptium.net/temurin/releases/\
   安裝時選擇「Set JAVA_HOME variable」前面的「X」點擊一下左鍵，然後選擇「將安裝在本機磁碟上」。
   之後可以用cmd的指令執行 Java 

3. 安裝 MySQL 資料庫
   MySQL Community Server 官網連結[MySQL :: Download MySQL Installer (Archived Versions)](https://downloads.mysql.com/archives/installer/)中選擇「8.0.33」，而 Select Operating System 中則選擇 「Microsoft Windows」
   安裝時選擇「Server only」![MySQL安裝 1](https://raw.githubusercontent.com/AoaoSeal/blog/main/MySQL安裝 1.png)

Authentication Method密碼加密選擇「Use Strong Password Encryption for Authentication (RECOMMENDED)」![MySQL安裝 2](https://raw.githubusercontent.com/AoaoSeal/blog/main/MySQL安裝 2.png)



Accounts and Roles設定 root user 的密碼，此密碼常重要忘記密碼的話，會需要重新安裝整個MySQL程式，學習時建議使用一樣的密碼springboot預防忘記密碼

![MySQL安裝 3](https://raw.githubusercontent.com/AoaoSeal/blog/main/MySQL安裝 3.png)

4. 安裝 Chrome 擴充功能 - Talend API Tester

 Talend API Tester 的安裝連結https://chromewebstore.google.com/detail/talend-api-tester-free-ed/aejoelaoggembcahagimdiliamlcdmfm

5. 安裝 Git
   Git 官網連結https://git-scm.com/
   議可以勾選左上角的「Additional icons」 ![Git安裝更改](https://raw.githubusercontent.com/AoaoSeal/blog/main/Git安裝更改.png)

## 總結:

只有第4項是沒看過的工具，其他按步驟安裝，沒有什麼問題



# 2.**IntelliJ建立專案、Project 設定** 

## 第一個 Spring Boot 程式

- **Name：** 這個 Spring Boot 程式的資料夾名字。
- **Location：** 這個 Spring Boot 程式預計創建出來的位置，預設是放在桌面上。
- **Language：** 使用哪種語言來開發 Spring Boot 程式，預設是 Java。
- **Type：** 選擇要使用哪種工具來構建 Spring Boot 程式，這部分比較複雜，因此先照著選 Maven 即可。
- **Group、Artifact、Package name：** 這些值和上面的 Maven 有關，一樣是比較複雜所以可以先跳過不理他。
- **JDK、Java：** 選擇想要使用的 Java 版本。
- **Packaging：** 打包 Spring Boot 的方式，預設是 Jar，這部分一樣是比較複雜（牽涉到 Tomcat），所以也是可以先跳過不理他。

![intelliJ2](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ2.png)

- 左上方紅框處，就可以去選擇 Spring Boot 的版本，這裡大家可以直接使用預設的最新版即可，不用特別去做調整。

  而在下方的部分，則是可以去選擇要載入哪些功能到這個 Spring Boot 程式裡面，這裡我們先展開Web，然後勾選裡面的「Spring Web」即可。

- ![intelliJ3](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ3.png)

  

  - 左側的部分是側邊欄，呈現了這個 demo 資料夾中的所有程式。
  - 右側則是程式的編輯區，只要在左側側邊欄對著檔案點擊兩下，就可以將程式開啟到右邊的編輯區，開始編輯這份程式。

  ![intelliJ5](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ5.png)

  展開左側的資料夾，這時候可以看到，在 src/main/java/com.example.demo 底下，有一個 DemoApplication.class 的檔案，點擊兩下開啟這個檔案之後，在右側就可以看到他的內容。

  在 DemoApplication 的程式裡面，其中最重要的，就是第 6 行的`@SpringBootApplication` 。

  @在 Java 裡面稱作「annotation」，中文是翻譯為「標註」或是「註解」。

  在Spring Boot 把「註解」賦予一個新的功能，這個 `@SpringBootApplication`，他的用法是要加在 class 上面，而他的用途，則是表示這一個 DemoApplication.class，是這個 Spring Boot 程式的啟動入口。

  ![intelliJ8](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ8.png)

  ### 添加 demo 程式

  在 com.example.demo 這個 package 上點擊右鍵，然後選擇 New，接著選擇 Java class，這樣就可以去創建一個 Java class 出來。

  ![intelliJ9](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ9.png)

  接著我們將這個 class 的名字，取名成 MyController。

![intelliJ10](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ10.png)

接著在這個 MyController 裡面，添加下列的程式。記得import相關的 library

```java
@RestController
public class MyController {
    
    @RequestMapping("/test")
    public String test() {
        System.out.println("Hi!");
        return "Hello World";
    }
}
```

### 運行 Spring Boot 程式

回到 DemoApplication.class 上，然後點擊第 7 行的播放鍵，去運行這個 Spring Boot 程式了

![intelliJ15](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ15.png)

## 總結:

Spring Boot 通過增強註解的用途，能夠更直觀地理解程式的結構和功能。不僅提高了程式的可讀性，還能簡化配置，讓開發過程更加高效。



## interface`與`implements`

接下來的學習需要使用到，所以花了點時間再去複習理解
`implements` 關鍵字用於一個類別實現一個或多個介面（interface）。介面定義了一組方法，而使用 `implements` 的類別必須提供這些方法的具體實現。這樣可以實現多重繼承的效果，因為一個類別可以實現多個介面。

`interface` 是一種特殊的引用類型，它類似於類別，但不能包含實例變數或方法的實現。介面主要用來定義一組方法的簽名，類別可以實現這些方法。這樣可以強制類別提供特定的行為，從而實現多型和解耦。

#### 1. 定義介面

```
public interface MusicPlayer {
    void play(String song);   // 播放歌曲
    void stop();             // 停止播放
}
```

#### 2. 實現介面

接下來，我們創建兩個類別，`MP3Player` 和 `WAVPlayer`，分別用於播放 MP3 和 WAV 格式的音樂。

MP3播放器

```
public class MP3Player implements MusicPlayer {
    @Override
    public void play(String song) {
        System.out.println("Playing MP3 song: " + song);
    }

    @Override
    public void stop() {
        System.out.println("Stopping MP3 playback.");
    }
}
```

WAV播放器

```
public class WAVPlayer implements MusicPlayer {
    @Override
    public void play(String song) {
        System.out.println("Playing WAV song: " + song);
    }

    @Override
    public void stop() {
        System.out.println("Stopping WAV playback.");
    }
}
```

#### 3. 使用介面

我們可以創建一個音樂播放器管理器，用來管理不同類型的播放器：

```
public class MusicPlayerManager {
    private MusicPlayer musicPlayer;

    public void setMusicPlayer(MusicPlayer musicPlayer) {
        this.musicPlayer = musicPlayer;
    }

    public void playSong(String song) {
        if (musicPlayer != null) {
            musicPlayer.play(song);
        } else {
            System.out.println("No music player selected.");
        }
    }

    public void stopSong() {
        if (musicPlayer != null) {
            musicPlayer.stop();
        } else {
            System.out.println("No music player selected.");
        }
    }
}
```

#### 4. 測試實現

最後，我們在主程序中測試這些類別的功能：

```
public class Main {
    public static void main(String[] args) {
        MusicPlayerManager manager = new MusicPlayerManager();

        // 使用 MP3 播放器
        MusicPlayer mp3Player = new MP3Player();
        manager.setMusicPlayer(mp3Player);
        manager.playSong("MyFavoriteSong.mp3"); // 輸出: Playing MP3 song: MyFavoriteSong.mp3
        manager.stopSong();                      // 輸出: Stopping MP3 playback.

        // 使用 WAV 播放器
        MusicPlayer wavPlayer = new WAVPlayer();
        manager.setMusicPlayer(wavPlayer);
        manager.playSong("AnotherSong.wav");    // 輸出: Playing WAV song: AnotherSong.wav
        manager.stopSong();                      // 輸出: Stopping WAV playback.
    }
}
```

### 小結

1. **介面** (`MusicPlayer`) 定義了播放和停止音樂的基本行為。
2. **實現** (`MP3Player` 和 `WAVPlayer`) 提供了具體的播放和停止行為。
3. **使用** 介面使得 `MusicPlayerManager` 可以靈活地切換不同的音樂播放器，符合開放封閉原則。

這個例子展示了 `implements` 的使用，以及如何通過介面來實現多型性，使系統更具擴展性和可維護性。

# 3.什麼是 IoC？

IoC 的全稱是 Inversion of Control，中文是翻譯為控制反轉， IoC 的概念，就是「將 object 的控制權交給了外部的 Spring 容器來管理」，所謂的 Control (控制)，就是對於 object 的控制權

 IoC的優點 

1.Loose coupling（鬆耦合）降低各個 class 之間的關聯性

2.Lifecycle management（生命週期管理）Spring 就會負責創建、初始化、以及銷毀

3.More testable（方便測試程式）所有的 object 都是由外部的 Spring 容器來做管理，因此我們就可以容易的使用 Mock 的技術，在測試的過程中，將 Spring 容器中的 object 給替換掉

## 什麼是 DI？

到「IoC 控制反轉」的地方，一定就要搭配「DI 依賴注入」，DI 的全稱是 Dependency Injection，每當 Spring 容器想要把 HpPrinter 「借」給 Teacher 使用時，就是表示 **Spring 容器把 HpPrinter 給「注入」到 Teacher 這個 class 裡面，因此才稱為是 「DI 依賴注入」**

## 什麼是 Bean？

由 Spring 容器來管理的 object，我們賦予他們一個新的名字，就叫做 Bean，所以 Bean 其實就只是一個 object 而已，本質上和我們直接去 new 一個出來的沒什麼差別

# 4.創建 Bean 的方法：@Component

創建 Bean `@Component ` 與注入 Bean `@Autowired`注意事項

被創建出來的 Bean，他們的名字，會是「Class 名的第一個字母轉成小寫」，舉例來說，上面的 HpPrinter class，當我們在這個 class 上面加上一個 `@Component` 之後，Spring 所生成出來的 Bean 的名字，就會是 hpPrinter

`@Autowired`兩個限制

1.想要使用 `@Autowired` 去注入一個 Bean 進來時，我們自己本身也得變成是由 Spring 容器所管理的 Bean 才可以，這樣子 Spring 容器才有辦法 DI (依賴注入)

2.`@Autowired` 是透過「變數的類型」來注入 Bean 的（所以只要 Spring 容器中沒有那個類型的 Bean，就會注入失敗），牽涉到 Java 的多型特性

由此可知Spring Boot 程式裡面 `@Component` 和 `@Autowired`使用量會非常大，

# 5.指定注入的 Bean - @Qualifier

假設在 Spring 容器中，同時有兩個一樣類型的 Bean 存在，譬如說像是下面這張圖![intelliJ46](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ46.png)在 Spring 容器中同時有 hpPrinter 和 canonPrinter 這兩個 Bean 存在，那麼在這個情況下，Spring Boot 會出現錯誤並且運行失敗，錯誤原因就會是「同時有多個同樣類型的 Bean 存在，因此無法選擇要注入哪一個」

`@Qualifier` 的用途，是去**指定要注入的 Bean 的「名字」是什麼**進而解決同時有兩個同樣類型的 Bean 存在的問題，先由 `@Autowired` 篩選類型、再由 `@Qualifier` 篩選名字

![intelliJ47](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ47.png)

使用`@Qualifier`  的兩個注意事項

1.使用 `@Qualifier` 去指定「要注入的 Bean」時，一定要搭配 `@Autowired` 一起使用，單純使用 `@Qualifier` 是沒有任何用處的

`2.@Qualifier` 是為了解決「多個類型同時存在」的問題而誕生，因此他所指定的是 **「Bean 的名字」**，也由於 `@Qualifier` 指定的是 Bean 的名字，因此掌握 Bean 的名字的生成方式就非常的重要

# 6.什麼是 Bean 的初始化？@PostConstruct

`@PostConstruct` 的用途，就是 **「為這個 Bean 去進行初始化」**，因此我們就可以透過 `@PostConstruct` 的功能，去設定這個 Bean 中的變數的初始值，

新增一個新的方法，並且在這個方法上面加上 `@PostConstruct`，這樣就可以在這個 **「有加上 `@PostConstruct` 的方法中」**，去初始化 Bean 的值了![intelliJ59](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ59.png)

@PostConstruct 的兩個注意事項

1.「被加上 `@PostConstruct` 的方法」，在宣告上格式需要遵守：

1. **方法的可見性**：被加上 `@PostConstruct` 的方法通常是 `public`，但也可以是 `protected`。不過，為了清晰和通用性，通常建議使用 `public`。

2. **返回值**：正確，這個方法的返回值必須是 `void`。

3. **參數**：這個方法「不能」有參數

4. **方法名稱**：這個方法的名字可以隨意取，不影響 Spring Boot 運作

   綜合以上 4 點，基本上這個「初始化 Bean 的方法」，通常就會長得像是下面這個樣子

   ```java
   public void method() {
       // 初始化邏輯
   }
   ```

2.使用 `@PostConstruct` 去初始化 Bean 的時候，在同一個 class 中，建議一次只讓一個方法加上  `@PostConstruct`。

同時在多個方法上都加上 `@PostConstruct`，雖然 Spring Boot 程式仍舊是可以正常運行起來，但是我們無法知道 Spring Boot 會先執行哪一個方法去初始化 Bean，因此可能會造成程式邏輯的錯誤，並且後續也很難統一管理初始化的設定。

總結:

1.Spring 本身並沒有提供像 `@Qualifier` 這樣專門用於標識方法的註解。

只能通過良好的命名、使用自定義註解、封裝邏輯或拆分類別來達到辨識的目的。

2.`@PostConstruct`U應該可以應用在用戶進入支付頁面時，在支付相關的 Bean 被創建時執行初始化邏輯，查詢並加載用戶的支付紀錄，進一步提升使用者體驗。

# 7.什麼是 Spring Boot 設定檔？

 Spring Boot 設定檔，指的是「放在 src/main/resources 這個資料夾底下的 **applicaiton.properties 檔案**」，而他的目的，就是去「存放 Spring Boot 程式的設定值」

application.properties 檔案，是使用**「properties 這個語法」**來撰寫的

 properties 的語法中，是使用 `key=value` 這樣子的格式來撰寫，並且「每一行」都是一組 key 和 value 的配對

### properties 語法的注意事項

1. **空白鍵**：在 `.properties` 文件中，`=` 前後不需要空白鍵，額外的空白可能導致解析錯誤。
2. **`.` 的意義**：`.` 符號表示層級關係，例如 `my.name=John` 意思是「我的名字是 John」。
3. **註解**：使用 `#` 符號可以添加註解，該行會被忽略，不會影響程式執行。
4. **未使用屬性**：如果屬性已定義但未在任何地方使用，IDE 可能會提示 "Cannot resolve configuration property"。這是因為在 IDE 的靜態分析中，無法找到對應的引用。此提示不代表屬性本身有問題，而是表示該屬性未被任何程式碼引用。
5. ![intelliJ60](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ60.png)

### 讀取 Spring Boot 設定檔（application.properties）中的值：@Value

在privata int count 的變數上面，去添加一個 `@Value("${count}")`就可以從 Spring Boot 設定檔讀取key 的值

![intelliJ61](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ61.png)



##  @Value 的注意事項



1. **固定格式**：屬性的寫法必須遵循特定格式。

   ```java
   @Value("${XXXX}")
   ```

2. **適用範圍**：`@Value` 只有在` Bean` 和 `Configuration` 類中才能生效。

3. **類型一致**：所注入的屬性類型必須與變數類型一致。

   ```java
   @Value("${my.name}")
   private String name;
   ```

4. **預設值**：可以為屬性設置預設值，以防屬性未定義而報錯。雖然這種寫法存在，但不推薦使用，因為它可能會導致程式混亂，難以找出錯誤的地方。

   ```java
   @Value("${printer.count:200}") 
   private int count;
   ```

   

# 8.什麼是 Spring AOP？

AOP 的全稱是 Aspect-Oriented Programming「切面導向程式設計」，**而 AOP 的概念，就是「透過切面，統一的去處理方法之間的共同邏輯」**

![intelliJ62](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ62.png)

在 pom.xml 載入 Spring AOP

如果想要在 Spring Boot 中使用 Spring AOP 的功能的話，首先會需要在 pom.xml 這個檔案裡面新增以下的程式，將 Spring AOP 的功能給載入進來

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

加完上述的程式之後，在 pom.xml 的右上角會出現一個 M 符號，點擊這個 M 符號，就可以更新這個 Spring Boot 程式，把 Spring AOP 的功能給載入進來

![intelliJ63](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ63.png)

## 製造切面的方法：@Aspect

加好 Spring AOP 的功能之後在 class 上面加上 `@Aspect`**，另外只有 Bean 才可以應用切面**，所以@Component與@Aspect都要使用。



![intelliJ64](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ64.png)

應用例子:只要在 com.example.demo 這個 package 底下，創建一個新的 MyAspect class 出來，並且添加下列的程式，只需要確認 MyController 中有成功注入 HpPrinter 進來便可以運行

1. 我們指定了「切入點為 HpPrinter 中的所有方法」
2. 在切入點的方法「執行之前」
3. 執行下面的 before() 方法

### @After、@Before、@Around

`@After` 的寫法其實和 `@Before` 一模一樣，只要把 `@Before` 換成 `@After` 使用上面的方法就行了

`@Around` 寫起來比較複雜

```java
@Aspect
@Component
public class MyAspect {

    @Around("execution(* com.example.demo.HpPrinter.*(..))")
    public Object around(ProceedingJoinPoint pjp) throws Throwable {
        System.out.println("I'm around before");

        // 執行切入點的方法，obj 為切入點方法執行的結果
        Object obj = pjp.proceed();

        System.out.println("I'm around after");
        return obj;
    }
}
```

## 切入點 (Pointcut) 怎麼撰寫？

1.切入點為 com.example.demo.HpPrinter 底下的 print() 方法

```java
execution(* com.example.demo.HpPrinter.print())
```

2.切入點為 com.example.demo.HpPrinter 底下的所有方法

```java
execution(* com.example.demo.HpPrinter.*(..))
```

3.切入點為 com.example.demo 這個 package 中的所有 class 的所有方法（不包含子 package）

```java
execution(* com.example.demo.*(..))
```

4.切入點為 com.example.demo 這個 package 及其底下所有子 package 中的所有 class 的所有方法

```java
execution(* com.example.demo..*(..))
```

5.切入點為那些帶有 `@MyAnnotation` 的方法

```java
@annotation(com.example.demo.MyAnnotation)
```

Spring AOP 以前最常被用在以下三個地方：

1. 權限驗證
2. 統一的 Exception 處理
3. log 記錄

由於 Spring Boot 發展逐漸成熟，因此上述這些功能，都已經被封裝成更好用的工具讓我們使用了，所以大家目前已經比較少直接使用 @Aspect 去創建一個切面出來了

# 9.什麼是 Spring MVC？

**Spring MVC 的用途，就是讓我們「在 Spring Boot 中實作前後端之間的溝通」，透過 Spring MVC 的功能，去創建一個 API 出來**

![intelliJ65](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ65.png)



# 10.什麼是 Http 協議？

Http 協議的目的，是「**規定資料的傳輸格式，讓前端和後端能夠有效的進行資料溝通**，可以分為「Request (請求)」和「Response (回應)」兩部分，而一個 Http request 加上一個 Http response，就可以組合成一次完整的 Http 溝通

![intelliJ66](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ66.png)



## Http Request 的格式規範

------

**Http request** 裡面，可以分成四個部分，分別是：

http method、url、request header 以及 request body![intelliJ67](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ67.png)

1. Http method

    Http 請求所使用的「請求方法」，他的值有好幾種可以選，像是常用的有 GET、POST、PUT、DELETE

2. Url

   其實就是網站的網址，也就是會出現在瀏覽器上方網址列中的那一串文字

3. Request header

   主要是放一些請求時的通用資訊

4. Request body

   是放請求的參數，只有在使用 POST 或是 PUT 這類的請求方法時，才可以去使用 request body 去傳遞參數

## Http Response 的格式規範

在一個 Http response 裡面，可以分成三個部分，分別是：

http status code、response header 以及 response body![intelliJ68](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ68.png)

1. Http status code

   中文可以翻譯為「Http 狀態碼」，用途是表達「這一次 Http 請求的結果為何」，用於快速判斷這一次 Http 請求結果是成功或失敗

2. Response header

   和上面的 Request header 類似，都是放一些通用的資訊，因為他也是屬於比較進階的部分，可以先略過

3. Response body

   可以說是在 Http response 中最重要的部分，這裡面所放的，就是「**後端要傳給前端的數據**」

   因此當前端收到了一個 Http response 時，如果此次請求是成功的話，前端就會去取得這個 Response body 中的數據，並且將這些數據結合前端的版面設計，最後就可以呈現完整的網頁給使用者看了

# 11.在 API Tester 中練習發起 Http request、查看 Http response

首先打開瀏覽器的插件 API Tester，上方的 Http request 區塊中，每一個部分，就可以對應到剛剛所介紹的 Http request 格式

![intelliJ69](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ69.png)

先在 http method 的部分選擇 GET，然後在 url 的部分填上下列的值 http://localhost:8080/test ，這樣就填好了一個最簡單的 Http request 了！

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ71.png)

按完「Send」按鈕之後，他的 http status code (http 狀態碼) 的值是 200就是表示請求成功，透過這個 http status code，**「快速的」** 知道這一次的 Http 請求是成功

 Http 請求是成功的話，後端就會將返回值放在 response body 裡面，供前端後續去存取，所以在這裡也可以看到，Spring Boot 程式就將返回值「Hello World」呈現在 response body 中

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ72.png)



### 回顧Request 和Response 

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ73.png)

接下來開始介紹Request的內容

# 12.Url 的格式

url，其實就是我們平常在打開瀏覽器的時候，在上方網址列會出現的這一串字，中文是翻譯為網址

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ74.png)

### 1. 使用的協議

在 url 的最前面，會顯示這個 url 所使用的是什麼協議，像是這邊使用的就是 http 協議

### 2. 域名

在協議後面會有一個 `://` 做分隔，後面接著的就是這個 url 的域名，以這個例子來說的話，這個 url 的域名就是「localhost」

### 3. Port

Port 有時候可以省略，所以他不一定會出現，是一個可選項

不過只要看到域名後面有加上 `:`，並且在 `:` 後面有加上一個數字的話，那這個數字就是 url 所使用的 port，像是這邊在 `:` 後面就有寫上 8080，就表示這個 url 所使用的 port 就是 8080

### 4. url 路徑

而在 port 後面，會去加上一個斜線（或是沒有 port 的話，就是在域名後面的斜線），**從這個斜線之後的所有東西，就是這個 url 的路徑**，所以像是這個例子中，url 路徑的值就是 `/test`，基本上就是決定了要對應到 Spring Boot 中的哪個方法

## Url 路徑對應：@RequestMapping

果想要將這個 `/test` 的 url 路徑，去對應到 Spring Boot 的方法上的話，我們就只要使用 `@RequestMapping`

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ75.png)

#### 使用 @RequestMapping 的注意事項

在使用 `@RequestMapping` 去指定 url 路徑的對應時，是有一個非常重要的注意事項，**就是該 class 上面一定要上加 `@Controller` 或是 `@RestController`，否則 `@RequestMapping` 不會生效**

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ76.png)

## 補充:什麼是 Json？

**Json 是一種格式，用途是更簡單、更直覺的去呈現數據，讓我們易於讀寫**，Json 格式中，可以由一組大括號 `{}` 來表示一個 object，下面一段 Json 格式的程式時，就表示我們 new 出了一個 object

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ77.png)

### Key 和 Value 的概念

寫好一對大括號之後，**在大括號 `{}` 裡面，我們是可以去定義「key 和 value 的配對」**，這個 key 的地位就等同於是去宣告一個 Java 中的變數，而 value 就是去設定這個變數的值

Json 支援以下幾種類型

- 整數`"id": 123`
- 浮點數`"score": 1.111`
- 字串`"name": "Hello"`
- Boolean`"option": true`
- List`"list": [1, 2, 3]`

### 使用 Json 的注意事項

在使用 Json 時，有一個很重要的注意事項，就是**「在 Json 中的所有 key，都必須要加上雙引號 `" "` 來框住才可以」**



### 如何將返回值轉換成是 Json 格式？

**如果想要將方法所返回的值，轉換成是 Json 格式** 的話，會有兩個步驟：

#### 1.在 class 上面加上 `@RestController`

#### 2.將該方法的返回值，改成是一個「Java 中的物件」

- ##### 使用 `Map`

  `Map<String, Object>` 是一種靈活的結構，適合處理不定數量和不定格式的 JSON 資料。

- ##### 使用 `List`

  若 JSON 中包含的是陣列結構，可以使用 `List` 來接收。常用 `List<Map<String, Object>>` 或 `List<YourClass>` 的形式，取決於陣列內的結構。

- ##### 使用 Java 類別 (自定義 POJO)

  將 JSON 對應到特定的類別，能夠提高代碼的可讀性和類型安全性。

#### 

##### 補充@Controller 和 @RestController 的差別在哪裡

- `@Controller`：將方法的返回值自動轉換成 **前端模板的名字**

  是有搭配 jsp、thymeleaf...等等這類的前端模板引擎時，再考慮去使用

- `@RestController`：將方法的返回值自動轉換成 **Json 格式**

  前後端分離的盛行、以及 Json 格式的崛起，因此目前大部分的程式都是使用 `@RestController` 來實作

# 13.Http method- GET 和 POST

## GET 的用法和特性

因為 Http 協議規定，當使用 GET 請求時，**前端只能夠將參數放在 url 的最後面，透過這個格式將參數傳遞給後端**

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ78.png)

`GET` 適合用在以下場合：

**查詢資料**：用來獲取伺服器上的資源，例如文章內容或用戶資訊。

**篩選結果**：URL 中加入查詢參數，篩選或過濾結果，如產品列表。

**靜態資源**：請求圖片、CSS、JavaScript 等不改變伺服器狀態的靜態內容。

**快取和書籤**：`GET` 請求可以快取，便於使用者書籤保存。

**注意**：避免用 `GET` 傳送敏感資訊，且適合小量數據請求。

## POST 的用法和特性

當我們使用 POST 請求時，Http 協議就規定「前端要將參數放在 request body 中做傳遞」，而由於 request body 會被封裝起來，因此參數不會洩

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ79.png)

`POST` 適合用在以下情況：

1. **新增資源**：用來將新數據發送到伺服器，像是創建新用戶或新增文章。
2. **傳送敏感資訊**：資料會隱藏在請求體中，適合密碼等敏感信息。
3. **大量數據**：可傳輸大筆數據，避免 URL 長度限制。
4. **伺服器上的動作**：執行需要更改伺服器狀態的操作，如購物結帳或提交表單。

**注意**：`POST` 不會被快取，不適合用於讀取操作。



# 14.取得Request請求參數  

##  Spring Boot 中接住參數的四個註解

在 Spring Boot 中，有四個註解可以去接住前端的參數，分別是：

1. `@RequestParam`：接住放在 Url 後面的參數
2. `@RequestBody`：接住放在 request body 中的參數
3. `@RequestHeader`：接住放在 request header 中的參數
4. `@PathVariable`：取得放在 url 路徑中的值

### 1. @RequestParam：接住放在 Url 後面的參數

GET 方法在傳遞參數時，就是把參數放在 url 的最後面來傳遞，當前端使用 GET 方法來發起一個 Http request 時，Spring Boot 這邊就是會使用 `@RequestParam`，來將前端所傳遞過來的參數給接住

![img](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ80.png)

#### 使用 @RequestParam 的注意事項

1.參數名字須一致

2.參數類型需一致

### 2. @RequestBody：接住放在 request body 中的參數

POST 方法在傳遞參數時，就是把參數放在 request body 中來傳遞，因此如果我們想要去接住這些放在 request body 中的參數的話，那麼就是要使用 `@RequestBody` 才能接住！

首先創建了一個和 Json 格式一一對應的 Java class 出來，那麼 Spring Boot 到時候，就可以去將 request body 中的 Json 格式，給轉回來成這個 Student class

![intelliJ81](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ81.png)

#### 如何運用 @RequestBody

 test2() 方法中，去新增一個 Student 類型的參數 student，並且在這個參數的前面，去加上一個 `@RequestBody`就也能成功的取得到前端傳遞過來的參數的值

![intelliJ82](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ82.png)

##### 使用 @RequestBody 的注意事項

使用 `@RequestBody` 去接住前端放在 request body 中的參數時，最需要特別注意的就是「和 Json 格式一一對應的 Java class」要小心不要寫錯

### 3. @RequestHeader：接住放在 request header 中的參數

其實前端也是可以在 request header 中傳遞參數給後端的（**通常前端是會將「權限認證」或是「通用資訊」，放在 request header 中傳遞**）

在 request header 中，他的參數也是透過 key 和 value 的方式來存放的，如果打開 API Tester，就可以看到在上方的請求區塊中，有一個 Add header 的按鈕，點擊按鈕之後，就會出現一對 key-value 的格子讓我們填寫

![intelliJ83](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ83.png)

#### 如何運用 @RequestHeader

與@RequestBody相同

![intelliJ84](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ84.png)

##### 補充`@RequestBody` 和 `@RequestHeader`差別

``@RequestBody` 和 `@RequestHeader` 是用來從請求中提取數據的，但它們針對的數據來源和用途不同，並不只是用來區分重要資訊，也沒有明顯的效能差異。以下是它們的主要區別：

1. **數據來源**：
   - `@RequestBody`：用於取得請求體中的數據（通常是 JSON 格式）。例如，當前端透過 POST/PUT 請求發送 JSON 數據時，可以使用 `@RequestBody` 來將數據映射到 Java 物件。
   - `@RequestHeader`：用於取得 HTTP 請求標頭（Headers）中的數據，例如用戶身份驗證的 `Authorization` 標頭或客戶端類型的 `User-Agent` 標頭。
2. **常見用途**：
   - `@RequestBody`：適合用於接收大量的結構化數據，如表單資料、JSON 對象、XML 等。常用在提交資料的情境中。
   - `@RequestHeader`：適合用於接收非結構化或少量的參數，比如認證資訊、追蹤 ID 等，不會包含在請求體內。
3. **效能差異**：
   - 沒有明顯的效能差異。兩者的使用主要是為了語意上的區分，讓程式更具可讀性且便於維護。

`@RequestBody` 用於解析和取得請求體內的主要數據（如 JSON），而 `@RequestHeader` 是用來提取請求標頭的值。它們的區別在於數據來源與用途，而非重要性或效能上的差異。

### 4. @PathVariable：接住放在 url 路徑中的值

假設今天有一個 url 如下，在 Spring Boot 裡面，想要去取得到 url 路徑 `/test4/123` 中的 123 的值，必須要做以下這兩件事情：

```bash
http://localhost:8080/test4/123
```

1.使用 `@RequestMapping` 去定義 url 路徑時，先將 url 路徑定義成 `"/test4/{id}"`

2.在 test4() 的方法中，去添加一個 Integer 類型的參數 id，**並且在這個參數的前面，去加上一個 `@PathVariable`**

![intelliJ85](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ85.png)

#### @PathVariable 的注意事項

1.一定要讓「url 路徑」和「參數」的名字一致才可以

2.參數類型需一致

### 所以，為什麼我們需要 @PathVariable？

假設我們要傳遞 id 為 123 的參數給前端的話，其實完全可以使用`@RequestParam`來傳遞，就直接把 `id=123` 的資訊加在 url 最後面來傳就好了（如下圖左），到底為什麼要大費周章把 123 的值給塞到 url 路徑裡面，然後再透過 `@PathVariable` 來取得（如下圖右）

![intelliJ86](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ86.png)

會這樣子做的根本的原因，**就是「為了支援 RESTful API 的設計風格」！**

RESTful API 是在現今前後端開發中，非常流行的一種設計風格，而 Spring 框架為了讓 Spring Boot 也能夠開發出符合 RESTful API 的設計風格，因此就設計出了 `@PathVariable`，讓我們有能力去取得 url 路徑中的值

# 15.RESTful API 介紹

在開始介紹「RESTful API」之前，需要先了解什麼是「API」，

API 是指「用工程師的方式，去說明某個功能的使用方法」，其實就是用特定的格式，去表示某個功能到底要怎麼使用，等於是一個使用說明書的概念

譬如說以「取得商品列表」這個功能為例，當我們在 Spring Boot 程式中寫好這個功能，想要開放給前端或是其他人使用時，我們總不可能直接把 Spring Boot 程式貼給對方看，因為對方可能不熟悉 Spring Boot、或是他根本不了解 Java 程式語言，因此這樣子會造成溝通效率低落

下面這例子，就把「取得商品列表」的 API 給定義好了，像是我們會去說明要使用 `GET` 方法來請求、並且請求參數 (query parameter) 要帶上什麼、以及可能的 Http response 回覆會是什麼

![intelliJ87](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ87.png)而當前端拿到這樣子一個定義清楚的 API 的時候，他就能夠照著上面的介紹，去決定他在發起一個 Http request 時，到底需要使用哪個 Http method（GET 還是 POST）、或是 url 路徑是多少，以及他最後可能得到的返回結果又是什麼

因此透過 API 的設計，就可以更清楚明瞭的去知道某個功能的使用方式，進而提升前後端溝通的效率！

## 什麼是 RESTful API？

RESTful API 就是「符合 REST 風格的 API」，因此要設計出這樣子的 API，重點就是要讓你的 API「很 REST 風格」

而如果想要讓你所設計的 API 符合 REST 風格，就會需要符合三項特點

## 1. RESTful API :使用 Http method 表示動作

REST 風格會把 POST、GET、PUT、DELETE 這四種 Http method，分別去對應到資料庫的 Create、Read、Update、Delete 操作上

![intelliJ88](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ88.png)

透過這樣子的方式，所以其他工程師就可以更快透過 Http method，來快速判斷這個 API 可能執行的資料庫操作為何（譬如說你看到 GET 的 API，就大概知道「哦他是要去查數據啦」這樣）

## 2. RESTful API ：使用 url 路徑來描述資源之間的階層關係

假設現在有一個 API `GET /users`，那根據我們剛剛所介紹的 REST 風格，知道 GET 是去對應到資料庫的「Read 查詢」操作，因此這個 API `GET /users` 的含義，就是去「取得所有的 user」

那假設我們又有另一個 API `GET /users/123`，這個 API 的含義，就是去「取得在所有的 user 裡面，user id 為 123 的那個 user」

![intelliJ89](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ89.png)

到這邊，REST 風格的階層概念就出現了！以下更多的例子

![intelliJ90](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ90.png)

## 3. RESTful API ：使用 Json 或是 Xml 回傳

滿足 RESTful API 的最後一個條件比較簡單，就是 REST 風格會要求後端程式所回傳的 response body，必須要是 Json 或是 Xml 的格式，回傳 Json 格式比較普遍，但是其實使用 Xml 格式來回傳，也是符合 REST 風格的

簡單的說的話，其實就是在 class 上面加上 `@RestController`，這樣就可以正確的返回 Json 格式了

### 小結：滿足 RESTful API 的三個設計

1. 使用 Http method 來表示動作
2. 使用 url 路徑描述資源之間的階層關係
3. response body 返回 json 或是 xml 格式

## RESTful API 的優點和注意事項

**RESTful API 的目的，是為了「簡化工程師之間的溝通成本」**雖然 REST 風格的使用非常普遍，有非常多工程師和公司都喜歡採用 REST 風格，但是 REST 只是一個設計 API 的風格而已，**並不是設計 API 的標準規範**

REST 風格只是一個建議做法，而不是必要的做法，因此大家的使用情境如果比較特殊的話，那麼不遵守 REST 風格的設計也是完全沒問題的！

如果今天你是要用比較敏感的資訊來查詢資料庫，譬如說你要用身分證字號來查詢，那麼在這個情況下，硬要使用 REST 風格的 GET 方法反而是不洽當的（因為請求參數會洩漏出去），這時候反而是使用 POST 這種安全性較高的 Http method，才會是更好的選擇

# 16.Spring Boot 中設計 RESTful API



通常我們會設計 4 個最基本的 RESTful API ，如下圖所示：

![intelliJ91](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ91.png)

在 Spring Boot 中，POST有兩種方式可以「限制」前端只能用某個 Http method 來請求 url 路徑，分別是：

```
1. @RequestMapping(value = "/students", method = RequestMethod.POST)
2. @PostMapping("/students")
```

上面這兩種寫法，都可以限制前端只能使用 `POST` 方法，來請求這個 `/students` 的 url 路徑，而他們的差別，就只是一行寫起來比較長、一行寫起來比較短而已

## RESTful API 系列註解

常用的 RESTful API 

- `@GetMapping`

- `@PostMapping`

- `@PutMapping`

- `@DeleteMapping`

  這些註解不需要死記，只要觀察一下就可以發現，其實這些 `@PostMapping`、`@GetMapping`....等等，**他們都是「以 Http method 作為開頭的註解」**，然後在後面加個 Mapping 而已

## 補充什麼是 Http status code（Http 狀態碼）

屬於 Http response 的一部分，**是用來「表示這次 Http request 的結果為何」**前端只要透過這個 Http status code，就可以知道這次的 Http request 結果大概為何，想要查看具體的細節的話，再回頭去查看 response body 即可

![intelliJ92](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ92.png)

Http status code 可以根據 **「首位數字」**，分成 5 個大類，分別是：

- 1xx：資訊

- 2xx : 成功

  ![intelliJ93](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ93.png)

- 3xx : 重新導向

  ![intelliJ94](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ94.png)

- 4xx : 前端請求錯誤

  ![intelliJ95](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ95.png)

- 5xx : 後端處理有問題

![intelliJ96](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ96.png)

# 17.什麼是 Spring JDBC？

Spring JDBC 的用途，就是讓我們 **「能夠在 Spring Boot 中執行 sql 語法，進而去操作資料庫」**

![intelliJ97](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ97.png)

## 1：Spring JDBC 和 Spring Data JPA 的差別在哪

實際上 **「在 Spring Boot 中操作資料庫」** 這件事，是有許多工具可以選擇的，常見的操作資料庫的工具有：

- Spring JDBC
- MyBatis
- Spring Data JPA
- Hibernate
- ...等等

這些操作資料庫的工具中，又可以將他們分成兩類：

1. 在 Spring Boot 中執行 sql 語法，去操作資料庫

   - 這一類的工具，就是直接在 Spring Boot 中去執行原始的 sql 語法，然後透過這些 sql 語法去存取資料庫的數據
   - Spring JDBC 和 MyBatis 都屬於這一類

2. 使用 ORM 的概念，去操作資料庫

   - 這一類的工具，則是會透過 ORM (Object Relational Mapping) 的概念，去操作資料庫

   - 所以只要使用這類的工具，基本上就很少寫 sql 語法了，而是會套用另一種新的概念（即是 ORM），去存取資料庫的數據

   - Spring Data JPA 和 Hibernate 都屬於這一類

     也因為這兩種概念差比較多，因此此系列文只會介紹 Spring JDBC 的部分，也就是介紹要如何在 Spring Boot 中去執行 sql 語法，進而去操作資料庫

     

##  2：什麼是 CRUD？

CRUD 所代表的，是「資料庫」中的「Create (新增)、Read (查詢)、Update (修改)、Delete (刪除) 操作」的統稱，用以表示資料庫中最基礎的那些操作

![intelliJ98](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ98.png)

### 在 pom.xml 載入 Spring JDBC、資料庫 Driver

如果想要在 Spring Boot 中使用 Spring JDBC 的功能的話，首先會需要在 pom.xml 這個檔案裡面新增以下的程式，將 Spring JDBC 的功能給載入進來

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jdbc</artifactId>
</dependency>
```

除了加入 Spring JDBC 的功能之外，同時也得加入對應的資料庫 driver (驅動程式)，這樣 Spring Boot 後續才能去操作該資料庫

由于此系列文使用的是 MySQL 資料庫，因此大家可以在 pom.xml 檔案裡面，再新增以下的程式，將 MySQL 的 driver 給載入進來

```xml
<dependency>
    <groupId>com.mysql</groupId>
    <artifactId>mysql-connector-j</artifactId>
    <version>8.0.33</version>
</dependency>
```

> 補充：此處是以 MySQL 為例，如果大家之後使用的資料庫是 PostgreSQL 或是 SQL Server，則需要加入不同的 driver

加完上述的兩段程式之後，在 pom.xml 的右上角會出現一個 M 符號，點擊這個 M 符號，就可以更新這個 Spring Boot 程式，把 Spring JDBC 和 MySQL driver 一起給載入進來

![intelliJ99](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ99.png)

### 在 Spring Boot 中設定資料庫連線資訊

載入好 Spring JDBC 和 MySQL driver 之後，要在 Spring Boot 中設定資料庫的連線資訊的話，需要打開 resources 資料夾底下的 application.properties 檔案，添加以下的四行程式，這樣就完成了 MySQL 資料庫的連線設定了！

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/myjdbc?serverTimezone=Asia/Taipei&characterEncoding=utf-8
spring.datasource.username=root
spring.datasource.password=springboot
```

而我們也可以來分別介紹一下，這四行程式的用途分別是什麼

#### 1. spring.datasource.driver-class-name

spring.datasource.driver-class-name 是表示要使用的是哪種資料庫的 driver，此處我們填寫的是 MySQL 的 driver

#### 2. spring.datasource.url

spring.datasource.url 表示要連接到哪台資料庫上

此處的 `jdbc:mysql://localhost:3306` 是表示要連接到我們自己電腦上的 MySQL 資料庫裡面

而後面跟著的 `/myjdbc`，是指定要連線到 MySQL 資料庫中的 `myjdbc` 這個 database

並且在 myjdbc 後面的 `?` 處，有加上兩個參數：

- 其中 `serverTimezone=Asia/Taipei` 是表示我們指定所使用的時區是台北時區
- 而 `characterEncoding=utf-8` 則表示，我們所使用的編碼是 utf-8（這樣在處理中文的時候才不會出現亂碼）

#### 3. spring.datasource.username

spring.datasource.username 是要填入 MySQL 資料庫中的帳號，此處填上預設的帳號 `root`

#### 4. spring.datasource.password

spring.datasource.password 是填入上面那個帳號的密碼，此處填上 `springboot`



#### 補充：IntelliJ 中的資料庫管理工具（僅限付費版）

IntelliJ Ultimate (付費版) 中有一個非常好用的功能，就是讓我們可以直接透過 IntelliJ 中的介面，去管理資料庫中的數據

點擊 IntelliJ 右側的 Database 標籤，就可以開啟 IntelliJ 中的資料庫管理工具

![intelliJ100](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ100.png)

開啟設定的視窗之後，在 User 處填上 `root`，在 Password 處填上 `springboot`（此密碼即是當初安裝 MySQL 時設定的密碼）

![intelliJ101](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ101.png)

創建好 MySQL 連線之後，IntelliJ 就會跳出一個 console 的視窗，我們就可以在裡面撰寫 sql 語法，直接去存取這個 MySQL 資料庫中的數據

譬如說我們可以寫上以下的 sql，嘗試去創建一個 myjdbc 的 database 出來

```sql
CREATE DATABASE myjdbc
```

寫好之後，只需要按下左上方的「播放鍵」，就可以去執行這條 sql

而 sql 執行成功之後，在右側的視窗也會出現 myjdbc 的 database 資訊

![intelliJ 2024-11-02 00-23-00](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ%202024-11-02%2000-23-00.png)

除了能夠創建 myjdbc database 之外，我們也是可以在這個 console 上面，去執行其他的 sql，在 myjdbc database 裡面去創建新的 table 出來的

譬如說我們可以寫上以下的程式，去創建一個 student table 出來

```sql
CREATE TABLE student (
    id INT PRIMARY KEY ,
    name VARCHAR(30)
)
```

**不過此處要特別注意，在執行這個 sql 之前，需要先確認我們「是否是在 myjdbc 這個 database 底下運行 sql」**，在 console 視窗的上方有一個 `<schema>` 的按鈕，點擊他之後會出現許多選項，此處就是在設定我們目前正在哪個 database 底下執行 sql

因此此處我們需要點擊 myjdbc，即是表示之後是在 myjdbc 這個 database 底下執行 sql 語法

![intelliJ2024-11-02 00-25-52](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ2024-11-02%2000-25-52.png)

選擇好 myjdbc 之後，接著就可以回到 console 視窗上，然後點擊播放鍵，去執行 `CREATE TABLE student ....` 的 sql 語法了

執行完成之後，就會在右側的視窗中就會出現 student table 的資訊

![intelliJ2024-11-02 00-30-17](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ2024-11-02%2000-30-17.png)

在右側視窗中的 student table 使用左鍵點擊兩下，就可以開啟該 table，查看該 table 中的數據，像是目前在 student table 中一筆數據都沒有

![intelliJ2024-11-02 00-33-37](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ2024-11-02%2000-33-37.png)

但如果我們回到 console 上，然後執行下面的 INSERT sql，在 student table 中插入一筆 Judy 的數據的話

```sql
INSERT INTO student(id, name) VALUES (1, 'Judy')
```

![Screenshot 2024-11-02 00-35-59](https://raw.githubusercontent.com/AoaoSeal/blog/main/Screenshot%202024-11-02%2000-35-59.png)

那麼在 student table 中，就可以看到呈現了一筆 Judy 的數據出來了！

![Screenshot 2024-11-02 00-36-03](https://raw.githubusercontent.com/AoaoSeal/blog/main/Screenshot%202024-11-02%2000-36-03.png)

因此我們之後就可以透過 IntelliJ 的這項工具，直接在 IntelliJ 中去查看和修改資料庫中的數據

# 18.Spring JDBC 的用法  - 執行 INSERT、UPDATE、DELETE sql

### Spring JDBC 根據 sql 分成兩大類：update 和 query

- 在 update 系列的方法中，可以去執行 INSERT、UPDATE、DELETE 這三種 sql 語法
- 而在 query 系列的方法中，只能執行 SELECT 這一種 sql 語法

![intelliJ102](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ102.png)

如果想要執行的是 INSERT sql，那就是得使用 `update()` 來執行，而想要執行 SELECT sql 的話，那就是得改用 `query()` 來執行



### 1.update() 的基本用法

#### 1.注入一個 NamedParameterJdbcTemplate

首先第一步，就是在你的 Bean 裡面，先去注入一個 NamedParameterJdbcTemplate 進來

因此我們就可以在 StudentController 裡面，先使用 `@Autowired`，去注入 NamedParameterJdbcTemplate 這個 Bean 進來

```java
@Autowired
private NamedParameterJdbcTemplate namedParameterJdbcTemplate;
```

這個 NamedParameterJdbcTemplate 是 Spring JDBC 自動幫我們生成的 Bean，他會負責去處理和資料庫溝通的所有事項，因此我們後續就通通都會透過 NamedParameterJdbcTemplate，去幫我們執行 sql 語法

所以換句話說的話，只要你使用的是 Spring JDBC，那你基本上就都是在跟 NamedParameterJdbcTemplate 打交道

#### 2.撰寫 sql 語法

寫出想要執行的 sql 語法，所以我們就可以去創建一個 String 類型的變數 sql，並且在裡面寫上到時候想要執行的 sql 語法，

```
String sql = "INSERT INTO student(id, name) VALUES (3, 'John')";
```

#### 3.新增一個 `Map<String, object>` 的 map 變數

```
Map<String, Object> map = new HashMap<>();
```

#### 4.使用 update() 方法

使用 namedParameterJdbcTemplate 的 `update()` 方法，並且把上面所新增的 sql 和 map 這兩個變數，依照順序的給傳進去

```
namedParameterJdbcTemplate.update(sql, map);
```

當前端請求/students過來`update()` 方法就會去執行 sql 參數中所儲存的 sql 語法

###### update() 中的 map 參數用法

這個 map 變數的用途，是去 **「放 sql 語法裡面的變數的值」，我們想要「動態的決定」當前 sql 語法中的值的話，那就需要依靠 map 這個變數**

因此可以先創建一個 Student class 出來，並且在裡面創建兩個變數 id 和 name（和其對應的 getter 和 setter），程式如下：

```java
public class Student {

    private Integer id;
    private String name;

    // getter 和 setter
    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

接著在 StudentController 裡，在 insert() 方法的參數部分，使用 `@RequestBody`，去接住前端傳過來的參數

```java
@RestController
public class StudentController {

    @Autowired
    private NamedParameterJdbcTemplate namedParameterJdbcTemplate;

    @RequestMapping("/students")
    public String insert(@RequestBody Student student){

        String sql = "INSERT INTO student(id, name) VALUES (3, 'John')";
        Map<String, Object> map = new HashMap<>();
        
        namedParameterJdbcTemplate.update(sql, map);
        return "前端POST ,後端執行 INSERT sql";
    }


}
```

###### 修改 sql 語法、添加 map 變數中的值

接住前端所傳遞的變數之後，接著我們就可以來運用 map 變數，將前端所傳過來的 id 和 name 的值，插入一筆數據到資料庫中

這裡有兩個地方要修改：

1. **sql 語法**：將「3 和 John」的地方，改成「`:studentId` 和 `:studentName`」
2. **map 變數**：在 map 變數中 put 兩組 key-value 的值進去

在 Spring JDBC 裡面，只要在 sql 語法中加上了「:」，就表示這是一個「sql 中的變數」

- 譬如說像是 `:studentId`，就表示我們指定這是一個 sql 中的變數，名字叫做 studentId
- 而又像是 `:studentName`，就表示我們指定這又是另一個 sql 中的變數，名字則是叫做 studentName

```java
@RestController
public class StudentController {

    @Autowired
    private NamedParameterJdbcTemplate namedParameterJdbcTemplate;

    @RequestMapping("/students")
    public String insert(@RequestBody Student student){

        String sql = "INSERT INTO student(id, name) VALUES (:studentId,:studentName)";
        Map<String, Object> map = new HashMap<>();
        map.put("studentId", student.getId());
        map.put("studentName", student.getName());

        namedParameterJdbcTemplate.update(sql, map);
        return "前端POST ,後端執行 INSERT sql";
    }


}
```

###### 小結：`update()` 方法的用法

1. sql 參數：放想要執行的 sql 語法
2. map 參數：動態的決定 sql 變數中的值

![intelliJ4](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ4.png)

### 2.query() 的用法

`query()` 方法的前兩個參數和 `update()` 方法一樣，都是先放入「要執行的 sql 語法」，接著是放入「動態決定 sql 變數的 map」

而 `query()` 方法特別的地方，就在於他的第三個參數 **RowMapper**

![intelliJ6](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ6.png)

## RowMapper 的用途

 `query()` 方法中的第三個參數 RowMapper，他的用途，就是**「將資料庫查詢出來的數據，轉換成是 Java object」**

可以創建一個新的 StudentRowMapper class，然後讓他去 implements RowMapper 這個 interface，實作如下的程式：

```java
public class StudentRowMapper implements RowMapper<Student> {

    @Override
    public Student mapRow(ResultSet rs, int rowNum) throws SQLException {
        Student student = new Student();
        student.setId(rs.getInt("id"));
        student.setName(rs.getString("name"));
        return student;
    }
}
```

# 19.MVC 架構模式 - Controller-Service-Dao 三層式架構

所謂的「MVC 架構模式」，他是軟體工程中的一種軟體架構，而 MVC 架構模式的用途，就是將一個系統，去拆分成「Model、View、Controller」三個部分，並且讓每一個部分都各自負責不同的功能

![intelliJ7](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ7.png)

上面這一張圖看起來可能有點抽象，不過其實 MVC 架構模式的概念很簡單，他就只是「想要去把我們所寫的程式分個類」而已

譬如說你今天寫的這段程式，他可能是屬於 Model 的部分，又或是你寫的這段程式，他是被分類到 Controller 的部分，僅此而已，MVC 架構模式並不會添加什麼新功能到你的程式裡面

## Model

Model 所負責的，是「實作業務邏輯，並且處理數據」

也因為 Model 是負責處理數據，因此 Model 會需要去跟資料庫做溝通，將這些數據的改動給儲存起來

因此 Model 算是在 MVC 的架構中，最重要的一個部分，因為他實際上就是負責去處理數據，所以我們都會將核心的業務邏輯，寫在 Model 這個部分裡面

## Controller

在 MVC 架構模式中，Controller 所負責的，是「轉發 Http request」

所以簡單的說的話，當 Controller 收到來自前端的 Http request 之後，Controller 就會負責將這些 request，去轉發給 Model，讓 Model 去處理後續的操作

## View

在 MVC 架構模式中，View 所負責的，是「使用 Html 的模板去呈現數據」

不過因為近幾年提倡「前後端分離」的關係，所以版面設計就都會交給前端處理，因此在後端這裡，就不需要處理 Html 的版面部分，改成是使用 Json 格式來傳遞數據給前端，因此 View 這部分，相對來說就變得越來越不重要

### MVC 架構模式的優點

1. **職責分離**，更容易維護程式

2. 使程式結構更直覺，有利於**團隊分工**

3. **可重複使用**寫好的程式

   

## 在 Spring Boot 中套用 MVC 架構模式

在 Spring Boot 裡面，我們會將 MVC的架構模式，去轉化成是 **「Controller-Service-Dao 的三層式架構」** 來實作

### Controller-Service-Dao 三層式架構

下圖中，就呈現了 Controller、Service、Dao 這三層架構之間的關係，以及他們個別負責的功能

![intelliJ11](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ11.png)

### Controller 層

Controller 層的用途，是負責去 **「接收前端傳過來的 Http request，並且去驗證請求參數」**@RequestMapping、@RequestParam等等

### Service 層

當 Controller 層接收到前端傳過來的 Http request、並且對其驗證之後，就會去 call Service層，讓 Service 負責去接手後續的處理

Service 層的用途，主要是負責 **「商業邏輯的處理」**，而 Service 層在處理商業邏輯的過程中，Service 層會再去 call Dao這一層

### Dao 層

Dao 層是 Data access object的縮寫

這一層所負責的功能，就是 **「專門去和資料庫進行溝通的」**，所以換句話說的話，Dao 這一層，就會透過 sql 語法，去操作資料庫，進而去查詢/修改資料庫中的數據

# 20.實際使用 Controller-Service-Dao 三層式架構

### 在使用 Controller-Service-Dao 三層式架構之前...

在以前沒有 Controller-Service-Dao 三層式架構的概念時，我們所寫出來的 Spring Boot 程式會是下面這樣的

將取得前端參數的 `@GetMapping` 功能，以及去和資料庫溝通的 `namedParameterJdbcTemplate` 功能，全部放在同一個 class 中去實作，這樣子雖然同樣可以完成功能，但是在後續的管理和維護上，就會比較吃力

![intelliJ12](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ12.png)

### 使用 Controller-Service-Dao 三層式架構之後！

而當我們將上面的程式，改成是使用 Controller-Service-Dao 的三層式架構的話，就可變成下面這樣的寫法

![intelliJ13](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ13.png)

當我們套用了 Controller-Service-Dao 的三層式架構之後，會將上面的程式，去拆分成是「3 個 class」來負責

#### Controller 層：StudentController

![intelliJ14](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ14.png)

在 StudentController 裡面，我們只保留 `@GetMapping` 和 `@PathVariable` 的部分，使用 Spring MVC 的功能，去和前端溝通，取得前端傳過來的參數 studentId

而取得到 studentId 這個參數的值之後，StudentController 就會去 call StudentService 的 `getById()` 方法，後續交由 Service 層來處理

#### Service 層：StudentService

![intelliJ16](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ16.png)

StudentService 裡面，我們新增了一個 `getById()` 的方法，而這個方法的用途，就是去根據 student 的 id，去查詢這一筆 student 的數據出來

#### Dao 層：StudentDao

![intelliJ17](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ17.png)

負責處理和資料庫的溝通，因此我們在這裡就會直接去透過 namedParameterJdbcTemplate 的寫法，使用 Spring JDBC 的功能，從資料庫中查詢一筆數據出來

#### API Tester測試

如果完成了以上練習，可以用API Tester來測試看看結果

這邊就可以想想查詢時前端該下什麼METHOD，

URL該怎麼輸入可以應對Controller寫的@GetMapping

成功後得到的Response 是哪個http status code，並且內容是什麼

## Controller-Service-Dao 三層式架構的注意事項

### 1. 透過 Class 名字結尾，表示這是哪一層

透過命名快速的知道負責的功能是「和前端溝通」、「處理商業邏輯」、還是「和資料庫溝通」

### 2. 將 Controller、Service、Dao，全部變成 Bean

需要使用的時候，就可以透過 `@Autowired` 的方式去注入想要使用的 Bean 進來

![intelliJ18](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ18.png)

![intelliJ19](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ19.png)

### 3. 不能在 Controller 中直接使用 Dao

三層式架構中，各層的分層是很明確的，其中就有一項潛規則，即是「Controller 層不能直接使用 Dao 層」的 class

![intelliJ20](https://raw.githubusercontent.com/AoaoSeal/blog/main/intelliJ20.png)

### 4. Dao 層只能執行 sql 語法，不能添加商業邏輯

 Dao 層的功能，是負責去「和資料庫溝通」的，所以在 Dao 這個 class 裡面，只能夠去執行 sql 語法，去存取資料庫中的數據，一切複雜的商業邏輯處理，就通通回到 Service 層進行



# 補充Spring Boot常用註解

### 1. **控制層註解**

- **`@RestController`**：結合了 `@Controller` 和 `@ResponseBody`，用於建立 RESTful API。這個註解使所有方法的返回值都直接以 JSON 格式返回。
- **`@RequestMapping`**：用於設定 URL 路徑和 HTTP 方法（如 `GET`、`POST` 等）。可以搭配 `@GetMapping`、`@PostMapping` 等更具體的 HTTP 方法註解。
- **`@PathVariable`**：用於從 URL 中提取變數，並將其作為方法參數。這在處理帶有動態參數的路由時特別有用，例如 `/students/{id}` 可以提取學生的 `id`。

### 2. **依賴注入與組件掃描**

- **`@Autowired`**：讓 Spring 自動將符合條件的 Bean 注入到被標註的欄位、建構子或方法中，實現依賴注入。
- **`@Component`**、**`@Service`**、**`@Repository`**：這些註解將類別標記為 Spring 容器管理的 Bean，並會被自動掃描和註冊。它們有著不同的語意，分別適用於一般組件、業務邏輯層和資料存取層。

### 3. **配置相關**

- **`@Configuration`**：用於定義組態類別，標記此類別包含一組 Bean 定義。
- **`@Bean`**：在 `@Configuration` 類別中使用，定義一個方法，讓其返回的物件成為一個 Spring 管理的 Bean。
- **`@Value`**：從設定檔中注入單個屬性值，例如 `@Value("${server.port}")`。

### 4. **初始化與生命周期**

- **`@PostConstruct`**：在 Bean 初始化後立即執行，用於進行必要的初始化操作。
- **`@PreDestroy`**：在 Bean 銷毀前執行，通常用於清理資源。

### 5. **AOP（面向切面編程）**

- **`@Transactional`**：標記方法或類別，表示其內部操作應該在交易範圍內進行，自動管理資料庫的提交或回滾。
- **`@Aspect`**、**`@Before`**、**`@After`**、**`@Around`**：用於定義切面邏輯，實現橫切關注點，例如日誌或權限控制。

### 6. **JPA（Java Persistence API）相關**

- **`@Entity`**：將類別標記為 JPA 實體（Entity），表示其對應到資料庫中的一張表。
- **`@Id`**：指定實體類中的主鍵欄位。
- **`@GeneratedValue`**：指定主鍵欄位的生成策略，如自增等。
- **`@Column`**：對應資料庫中的欄位，可以指定名稱、長度等屬性。

### 7. **其他常用註解**

- **`@EnableAutoConfiguration`**：啟用 Spring Boot 的自動配置，根據依賴自動加載相關的配置。
- **`@SpringBootApplication`**：包含了 `@Configuration`、`@EnableAutoConfiguration` 和 `@ComponentScan`，是 Spring Boot 應用程式的主要入口註解。
- **`@Scheduled`**：用於排程任務，定義定期執行的方法，例如每隔一段時間執行。