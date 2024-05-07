---
title: Spark AR Studio 新手教學
date: 2021-02-03
slug: spark-ar-tutorial
description: Spark AR Studio 新手教學，介紹一些比較常用到的功能，以及一個小小的 project 實作
categories:
    - AInimal
image: https://i.imgur.com/ixYuWA2.png
---

# Spark AR Studio 新手教學

版本號：Spark AR Studio V125

---

## 介面介紹

![](https://i.imgur.com/q3Ws0Hc.png)

- Scene (左上)：所有在中央畫面上出現的**物件**都可以在這裡被選取
- Assets (左下)：使用或沒使用到的**素材**
- Properties (右側)：所選取物件的**屬性** (大小、位置


#### 左側垂直工具列：
- Workspace：一些被隱藏的工作區域
- Video：選擇手機模擬器出現的人，或使用電腦鏡頭
- Test on device：會把測試連結傳到登入的帳號
- Upload and Export：上傳 Spark AR Hub 跟匯出專案檔

#### 中央畫面：左鍵選取物件、按住右鍵拖拉改變視角、滾輪縮放
- 上方三個按鈕：分別代表移動所選取物件的位置、角度、大小

---

## 物件 (Object) 介紹


![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fac0009d3-8c37-43fd-b4f7-d251c809f0f6%2FUntitled.png?table=block&id=6671696d-9c7e-4a95-8e9a-3b8b8ee673de&width=3070&userId=7af45ef0-62e9-49d2-a2aa-35ff33d00963&cache=v2)

> 新增物件：Scene 跟 Assets 中間有個 **＋Add Object**，或是在你想加東西的地方按右鍵新增 (注意物件的層級)

### faceTracker

用來偵測臉部的物件，可以在它下方加**子物件** (ex：臉部裝飾、平面、3D 物件) 來達到讓東西跟著臉部一起動的效果，因此大多數 IG 濾鏡都會用到它。

### Face Mesh

類似於面具的物件，大多會放在 faceTracker 之下，可以用來做**美肌效果 (retouch)**、化妝、臉部彩繪等。

### Plane

一個平面，放在 faceTracker 之下可以用來做隨機選擇器的平面，或擺放任何需要跟著頭部動作的圖片。

---

## 物件的外觀 —— Material & Texture

新增一個物件在濾鏡中是**不會顯示任何東西的**，儘管在 Spark AR Studio 中會有黑白底作為提示，可是實際上那會是透明的！

我們需要給物件一層皮，也就是 **Material** (素材)

但 Material 預設會是灰色的，也不太可能是我們要的結果。因此我們還需要將我們想要的圖片貼上，也就是 **Texture** (質地)

雙擊剛剛做的 material0 進去，右側版面看到 Shader Properties > Texture，選擇 New Texture 並匯入要用到的圖片檔。

![](https://i.imgur.com/IP8522Z.png)

> Material 與 Texture 都會放在左下方工作區，建議要將他個別命名，不然當東西一多起來看縮圖會看到眼睛脫窗

---

## 測試及上傳 Spark AR Hub

![](https://i.imgur.com/hvz9Cn2.png)


中間那個按鈕可以讓你先在手機上測試，而下面的按鈕就是上傳 Spark AR Hub 了。

[Spark AR Hub](https://www.facebook.com/sparkarhub/dashboard/) 是管理該帳號內所有濾鏡的平台，提交審查動作必須在那裡完成。此外，那裡還可以編輯濾鏡資訊、觀看使用次數等，可以自己去看看還有什麼可以操作的地方。

提交審查所需要的東西有：

- 濾鏡名稱及 icon
- 範例影片
- 濾鏡發佈排程
- 類別、關鍵字 (選填)

然後注意他有一堆[**規範**](https://sparkar.facebook.com/ar-studio/learn/publishing/spark-ar-review-policies)，如果不小心違反了就得重新提交審查，有夠麻煩= =

---

## 濾鏡實作 —— *成大競爭力*

![](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2c321cc4-a19d-4f0f-a1c9-bf9509a07db1%2FScreenshot_20210203_050415_com.facebook.orca.jpg?table=block&id=be135b7f-23ce-4375-9b70-cd87c3ce15b3&width=3070&userId=7af45ef0-62e9-49d2-a2aa-35ff33d00963&cache=v2 =200x)
> 「遠見」率先公布「2021企業最愛大學生排行榜」，成大創下此一調查的七連霸，台大蟬聯亞軍，第三、四、五名分別為台科大、清大、交...


[**👉 素材下載區 👈**](https://drive.google.com/drive/folders/1XyUKFDRKYmZ-fr-apdZToJfSgVRYauqL?usp=sharing)
 

可以先想想這個濾鏡大概用了什麼物件再下去做，圖片中可以看到臉上有兩個印章、頭上有字、美肌，且都會跟著頭部轉動

- 臉上的印章 → faceMesh
- 美肌 → faceMesh
- 頭上的字 → plane
- 跟著頭轉 → faceTracker

根據上面觀察，這個濾鏡的架構如下 (注意縮排的關係)：

```
- faceTracker
    - faceMesh (美肌)
    - faceMesh (印章)
    - plane (文字)
```

事不宜遲，那就先加個 [faceTracker](https://hackmd.io/@kuouu/ar-note1#faceTracker) 到 Scene 裡面吧！

----

### 美肌 (retouch)

新增完 faceTracker 之後，我們先來做濾鏡幾乎必備的美肌 (retouch) 吧！

右鍵點擊 faceTracker 並新增一個 **[faceMesh](https://hackmd.io/@kuouu/ar-note1#Face-Mesh)**，並在 faceMesh 中新增一個 **material** ，並雙擊進入 material0 中。

material 中最上方應該會有一個屬性叫做 Shader Type，選擇 **Retouching**

如果需要，下方的 Skin Smoothing 可以調整美肌強度。

![](https://cdn-images-1.medium.com/v2/resize:fit:1600/0*jBobFjUXeb7Q506o)

那我們就完成第一步了，耶！😆

----

### 印章 (臉部彩繪)

接下來處理印章的部分，但其實跟上方 *[物件的外觀 —— Material & Texture](https://hackmd.io/@kuouu/ar-note1#%E7%89%A9%E4%BB%B6%E7%9A%84%E5%A4%96%E8%A7%80-%E2%80%94%E2%80%94-Material-amp-Texture)* 提到的一樣，按照**新增 faceMesh → 新增 material → 匯入圖片檔**即可完成。

但電腦儲存的圖片都是平面且為四邊形，臉卻是立體且不規則的，這樣直接匯入圖片沒問題嗎？

於是官方提供了兩種圖片給我們做臉部彩繪的參考 (其實還有分男女，所以是 4 種)：

![](https://i.imgur.com/ixYuWA2.png)


這次我們使用左邊的來處理，打開你任何可以編輯圖片的軟體，然後開始在你的臉上作畫，儲存完就可以安心的把圖片匯入了！

阿然後記得把底圖給隱藏或刪除R

於是我們完成了印章，也就是臉部彩繪的部分，接下來把文字放進來就完成了！

----

### 文字 (plane、位置大小調整)

新增物件跟上面印章的操作很像，就差在新增不同種類的東西而已，這次我們要新增的是一個[平面 (plane)](https://hackmd.io/@kuouu/ar-note1#Plane)，然後按照上面提到的流程將圖片匯入

這時候你會發現：他的大小跟位置都不是我要的！

點擊 Scene 中的 plane0 之後，調整方法可以有兩種：

![](https://i.imgur.com/60DiZmb.png)


1. 點擊正中央工作區的正上方三個按鈕，由左至右分別是調位置、角度、大小，利用物件上的箭頭來改變他的值。
2. 右側工作區有個 Transformations 的屬性，由上至下分別代表位置、大小、角度。


第一個方法調比較直觀，第二個則是能調的比較細微。

調完之後濾鏡基本上是完成了，測試確定沒問題之後點擊上傳 Spark AR Hub 等他審查過了之後就大功告成啦，恭喜你！

----

[**👉 濾鏡成品（要用手機開啟） 👈**](https://www.instagram.com/ar/173414257514001/)

---

## 參考資料及素材來源

- [印章產生器](https://yz.mofans.net/)
- [線上手寫字體產生器](https://www.texttopng.com/chinese/handwritten/handwritten/index.php)
- [Face Assets](https://sparkar.facebook.com/micro_site/url/?click_creative_path[0]=button&click_from_context_menu=true&country=TW&destination=https%3A%2F%2Flookaside.facebook.com%2Fdevelopers%2Fresources%2F%3Fid%3DFace-reference-assets-classic.zip&event_type=click&last_nav_impression_id=04CTtwONeKt4HB0eo&max_percent_page_viewed=100&max_viewport_height_px=722&max_viewport_width_px=1536&orig_http_referrer=https%3A%2F%2Fwww.google.com%2F&orig_request_uri=https%3A%2F%2Fsparkar.facebook.com%2Far-studio%2Flearn%2Farticles%2Fpeople-tracking%2Fface-reference-assets%2F&region=apac&scrolled=false&session_id=1jpRfljyH6iQoz6eF&site=spark_ar&extra_data[creative_detail]=button&extra_data[create_type]=button&extra_data[create_type_detail]=button) (點擊即下載)