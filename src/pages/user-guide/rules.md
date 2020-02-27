---
title: 規則
url: /user-guide/rules/
---
## 簡介
在｛實例｝中，分析器提供了在程式碼執行上的規則來產生問題。其規則有四種： 
* 程式碼異味（可維護性 域）
* 錯誤（可靠性 域）
* 漏洞（安全 域）
* 安全疑慮熱點（安全 域）

對於程式碼異味與錯誤，我們期望的是零錯誤回報，至少這是我們的目標，這樣一來開發人員就不用懷疑是否需要修復。 

對於漏洞，目標是要上80%以上的議題為正確回報。 

安全性熱點規則吸引安全性敏感的程式碼的注意，在開發人員審查之後，預計超過80%的問題會被迅速的解決為「已審查」。

規則頁面是可以發現所有 已存在的規則 或 基於所提供的模板創建新規則 的入口 

## 規則

在預設條件下，當你進入菜單頂端的「規則」項目時，您將看到由 <!-- sonarqube --> 安裝在｛實例｝上的 <!-- /sonarqube --> 分析器帶來的 <!-- sonarcloud --> SonarCloud 上所有可用的 <!-- /sonarcloud -->。 您可以基於左側的選項面板縮小搜尋的準則： 
* **語言** ： 規則所適用的語言。
* **種類** ： 錯誤、漏洞、程式碼異味或安全疑慮熱點規則。 
* **標記** ： 為了分類與幫助您可以更容易地發現，為規則增加標籤是可行的。 
* **儲存庫** ： 提供規則給｛實例｝的引擎／分析器。
* **預設嚴重程度** ： 規則的嚴重原始程度  --- 與提供此規則的分析器所規定的一致。
* **狀態** ： 規則可以三種不同的狀態：
  * **測試** ： 該規則近期才被實施，並且我們尚未從使用者得到足夠的回饋，因此可能會存在一些錯誤的正確回報與錯誤的錯誤回報。 
  * **不推薦使用** ： 該規則不應該再被使用由於一個相似，但又更加的有力與準確的規則存在。 
  * **預備**: 該規則已經可以被應用在生產中。 
* **可用自** ： 當一個規則初次被加入｛實例｝中。這對列出上次實例插件的更新是很實用的。 
* **模板** ： 展示允許創造客製化規則的模板（稍後此頁會敘述） 
* **品質設定檔** ： 從一個特定的設定檔中引入或排除。 

如果一個品質設定檔被選定，您也可以檢視它的啟用嚴重程度以及它是否被繼承。更多資訊請看品質設定檔文件。 

## 詳細規則

欲看到一個規則的詳細規定，你可以選擇點選它，或者使用右箭頭的按鈕。隨著基本的規則資料，你也能夠看到是否有任何設定檔是啟用的以及它產生了多少開放問題。 

以下的動作只有在擁有正確的權限下才可進行（管理品質設定檔與門檻）： 

* **增加／移除 標籤** ： 
  * 增加標籤在現有的規則上，或建立新的標籤，是可行的（只要在文字框輸  入時輸入一個新的名字即可）。 
  * 注意有些規則具有無法移除的內建標籤，他們的來源是提供規則的的插件。 
* **擴充描述** ： 
  * 你可以擴充規則敘述來讓使用者知道你的組織是如何使用一個特定的規則或給予一個規則更深層的敘述。 
  * 注意，被擴充的敘述將會被當成正常的規則詳細敘述提供給非管理員使用者使用。 

<!-- sonarqube -->
## 規則模板與客製化規則 

規則模板是由插件所提供，作為用戶在｛實例｝中定義自己的客製化規則的基礎。欲找到模板，從模板下拉選單中選擇 **僅顯示模板** 畫面： 

![Rule templates.](/images/rule-templates.png)

若要從模板建立一個客製化規則請點選「客製化規則」標題旁邊的 **建立按鈕** 並填入以下資訊： 
* 名稱
* 金鑰（自動建議）
* 描述（支援 Markdown 格式）
* 預設危險程度
* 狀態
* 模板指定的參數

透過點擊「客製化規則」區域裡的連結，你可以從一個模板導航至被它所定義的客製化規則的詳細內容。 

![Rule template details.](/images/rule-template-details.png)

### 客製化規則
你除了可以編輯或刪除以外，客製化規則跟一般的規則一樣：

![Custom rules.](/images/rules-custom.png)

**注意 ：** 當你刪除一個客製化規則，它並不是實際上從｛實例｝中移除實例，而是它的狀態被設成「被移除」而已。這允許與此規則相關當前的或是舊的議題被正確的顯示在｛實例｝中直到他被完全的移除。 

## 擴充程式設計的規則

客製化程式設計規則是可以增加的。 詳情與教學請見 [增加程式設計規則](/extend/adding-coding-rules/)。
<!-- /sonarqube -->

## 規則種類與嚴重性 

### 規則是如何被分類的？

｛實例｝品質模型將規則分為四個類別 ： 錯誤、漏洞、安全熱點，以及程式碼異味。規則基於以下問題的答案被指派到各類別去。 

**是否這條關於程式碼的規則很明顯是錯的或者是有很大的可能為錯誤？ **  
如果答案為「是」，那他就是屬於錯誤規則。   
如果不是...

**是否這條關於程式碼的規則會被駭客利用？ **  
如果答案為「是」，那他就是屬於漏洞規則。   
如果不是...

**是否這條關於程式碼的錯誤對於安全性是敏感的？**  
如果答案為「是」，那他就是屬於安全疑慮熱點規則。  
如果不是...

**是否這個規則不屬於一個錯誤抑或是漏洞？ **  
如果答案為「是」，那他就是屬於程式碼異味規則。 

## 嚴重程度如何分配？ 
分配嚴重程度給規則前，我們問更進一步的系列問題。第一個基本上是： 

**最糟糕的情況可能是甚麼？**

在回答這個問題時，我們試著考慮莫非定律而非預測最糟狀況。 

然後我們評估最糟的狀況的影響與可能性是高或低（_參見底下如何確定嚴重性和可能性_），然後將答案插入真值表：

|          | 影響                    | 可能性                  |
| -------- | ---------------------- | ---------------------- |
| 封鎖者    | ![](/images/check.svg) | ![](/images/check.svg) |
| 最嚴重影響 | ![](/images/check.svg) | ![](/images/cross.svg) |
| 主要影響   | ![](/images/cross.svg) | ![](/images/check.svg) |
| 次要影響   | ![](/images/cross.svg) | ![](/images/cross.svg) |

## 嚴重性與可能性是如何定義的？
欲分析一條規則的嚴重性，我們從最糟的事情開始 （請見上文 _嚴重度如何分配？_） 並詢問各類別特定的問題： 

### 錯誤
影響: **最糟的狀況能否造成應用程式崩潰或損毀已儲存的資料？**

可能性: **最嚴重可能發生甚麼事情？**

### 漏洞
影響: **最糟的狀況的利用會不會對你的資產或你的用戶造成嚴重影響？**

可能性: **駭客能利用最糟的狀況的可能性有多大？**

### 安全疑慮熱點 
安全疑慮熱點沒有被分配嚴重性因為在對它審查之前不知道是否確實有潛在的漏洞。 