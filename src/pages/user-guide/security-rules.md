---
title: 安全相關的規則
url: /user-guide/security-rules/
---
 

｛實例｝品質模組有三種不同種類的規則：可靠性（錯誤），脆弱性（安全），以及維護性（程式碼異味）規則。但是用其他方法區分，只會有兩種種類：安全規則，以及其他剩餘的規則。這兩個種類在他們所擷取到的東西沒有太大的區別，而是在他們的出處以及加註在他們之上的標準。 

## 對安全性相關規則的期望 
要清楚，｛實例｝語言外掛程式中實施的規則大部分標準都非常嚴格：不准有錯誤。對於一般的規則，你應該可以確信回報給你的任何問題確實是一個問題。 

但是對於安全相關的規則，事情就會以一點不同了。例如，很多安全引導訴說「敏感」資料該如何被處理（例如：不做紀錄，不在未加密的情況下儲存，諸如此類。）但是由於要想在一個規則中分辨哪個資料是敏感資料與否實在不太可能，我們選擇要維持零誤報標準並且不實作安全相關的規則，抑或是以不同的標準實作安全相關的規則。 

這就是為何安全相關的規則會投射出一個與你所習慣的更為寬廣的網。這個做法是該規則會標記任何有嫌疑的東西，並將它留給人工安全審查員來剔除誤報並發送真實問題進行補救。 

安全疑慮熱點是一個特種的議題，它可以辨識出需要被檢視的敏感程式碼區域，確定他是否包含脆弱的程式碼。 更多資訊請見 [安全疑慮熱點](/user-guide/security-hotspots/)。

## 安全相關的規則從何而來？
大多數的安全相關規則源自於已經被建立的標準：[CWE](http://cwe.mitre.org/), [SANS Top 25](http://www.sans.org/top25-software-errors/)，以及 [OWASP Top 10](https://www.owasp.org/index.php/Top_10-2017_Top_10). 欲找到與這些標準相關的任何規則，你可以利用不論標籤或者文字作為搜尋條件。這些規則所相關的標準都會被列在規則描述底部的 **查看** 區塊。 

### CWE
CWE 代表通用缺陷列表。根據 CWE [常見問題](http://cwe.mitre.org/about/faq.html#A.1)：

>通用缺陷列表 ( CWE™ ) 是一個通用軟體弱點的正式清單或字典，軟體弱點在軟體的結構、設計、程式碼或實作會導致可利用的安全漏洞。 CWE 的創造是為了做為一個描述軟體安全弱點的共同語言；作為一個瞄準這些弱點的軟體安全工具的標準量尺；以及作為通用弱點辨識、緩和、以及預防的基準。 

CWE 是弱點描述的層次結構。結構中最低階層的是叫做「弱點基礎」，描述著一個細微的弱點。在弱點基礎之上，是弱點定義與類別。一般來說，規則會連接著弱點基礎或弱點定義。 

工具如果符合特定要求，即可被認證為與 [CWE 兼容](http://cwe.mitre.org/compatible/)。 要求如下：

* 必須能夠利用 CWE 的辨識符號搜尋 CWE 相關規則。要在｛實例｝平台上進行此操作，只需要在規則頁面上的搜索文字框中刪除刪除 CWE 辨識符號（例如 CWE - 595 ）並進行搜尋。 
* 規則必須準確的連接到與她們相關的 CWE 物件，如欲看到 CWE 全圖對應的｛實例｝規則，請參照規則描述底部的「查看」區塊。
*  你必須要能夠辨識議題中與 CWE 相關的部分。要在｛實例｝平台上進行此操作，請參照相關的規則。 
* 產品文件必須包含一份 CWE 與 CWE 兼容性的描述。 
* 你所支援的 CWE 版本必須列出。｛實例｝語言外掛程式支援 2.8 版本。 
* 除了可以根據 CWE 辨識碼搜尋規則，你也可以利用「CWE」規則標籤進行搜尋。

要看到 CWE 物件覆蓋了哪些語言，請參照底下的連結： 
* [C](https://rules.sonarsource.com/c/tag/cwe)/[C++](https://rules.sonarsource.com/cpp/tag/cwe)
* [Java](https://rules.sonarsource.com/java/tag/cwe) 
* [Objective-C](https://rules.sonarsource.com/objective-c/tag/cwe)
 

### SANS Top 25

[SANS Top 25](http://www.sans.org/top25-software-errors/) 列表是由[SANS 組織](http://www.sans.org/). 當今的 SANS 列表被分為三種種類：元件之間不安全的互動、危險的資源管理、漏洞百出的防禦。 

SANS 所使用的標籤與其所對應的種類： SANS 不安全的前 25 名、 SANS 危險的前 25 名、 SANS 有漏洞的前 25 名。 

要找到關於 SANS 前 25 名的規則，你可以對類別進行文字搜尋，或者對相關的 CWE 物件，或者是進行規則標籤的搜尋。 

### OWASP Top 10
OWASP 代表開放式網頁應用程式安全專案。根據它的官方網站，他表示： 

> 一家全球性的 [501(c)(3)](http://www.irs.gov/Charities-&-Non-Profits/Charitable-Organizations/Exemption-Requirements-Section-501(c)(3)-Organizations) 非營利慈善組織，致力於改善軟體的安全性。我們的使命是要讓軟體的安全性 [可見](https://www.owasp.org/index.php/Category:OWASP_Video)，以便讓全世界的 [個體與組織](https://www.owasp.org/index.php/Industry:Citations) 可以對真正的軟體安全風險做出明智的決定。 

[OWASP Top 10](https://www.owasp.org/index.php/Top_10-2017_Top_10) 是一個列出廣泛種類弱點的列表，每一個種類可以映射到許多獨立的規則。 

OWASP Top 10 所使用的標籤所對應的弱點分類： owasp-a1，owasp-a2，owasp-a3，owasp-a4，owasp-a5，owasp-a6，owasp-a7，owasp-a8，owasp-a9，owasp-a10。 

要找到關於 OWASP Top 10 的規則，你可以對類別進行文字搜索，或者進行規則標籤搜尋。 
