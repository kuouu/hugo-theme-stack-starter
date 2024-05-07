---
title: CMU Cloud Computing 修課心得
date: 2024-05-06
slug: cmucc
image: https://hackmd.io/_uploads/BkeM-EIfR.jpg
categories:
    - CMU
---

# CMU Cloud Computing 修課心得

在第二學期修了傳說中的 CMU 神課，從以前一直就很好奇到底有多神、神在哪。在確定要修之前也查了蠻多人的修課心得，回饋主要分為兩派

- 支持派：學到很多、業界實用性很高
- 反對派：學得太雜太淺、花太多時間做繁瑣的工作

但 SV 校區能修的好課也不多，因此最後還是決定修了。

### 評分標準

[詳細課程大綱](https://www.cs.cmu.edu/~msakr/15619-s24/index.html)

|Type| Number| Weight|
|-|-|-|
|Content Checkpoint Quizzes| 10 out of 11| 20%|
|Projects 15-319 |5 out of 6 for 15-319|80%|
|Projects 15-619|5 out of 6 + Team for 15-619|60% + 20%|
|Total Grade|| 100%|

15-319 是大學部的課程， 15-619 則是研究所版本，差別僅在於 team project 以及學分數，而 MSSE 這個 Program 可以接受我們修大學部的版本。此外，這堂課的 workload 會因 team project 而變大許多，如果不打算花太多時間在修課方面，修 undergrad 是完全 ok 的。

### 教學方式

我覺得這堂課的授課方式對我來說真的是太新奇了，因此完全值得特別提出來講。這堂課程是完全遠端的，地理範圍橫跨 4 個校區（Pittsburgh, Sillicon Valley, Qatar, Rwanda），修課學生有兩百多人，助教共 16 位。沒有特定的上課時間，給予學生在時間上很大的彈性，學習方式主要是透過做 project，基本上照著提供的 writeup 就可以完成（但通常非常長）。

因為涉及很多不同的領域，對於沒有基礎的人會提供 primer 讓你熟悉基礎知識，但我認為這也是讓人詬病的地方。primer 通常都講得很淺，看完也不一定會，通常還是要做完 project 才會有點概念這個工具到底在幹嘛。project 則是會給你 starter code，避免你花太多時間在一些小細節上，這個做法同時也讓整個 project 變成很像是填空題的形式，有很多細節必須自己花時間去深入了解。

---

## Individual Project

project 主要使用 Java 跟 Python，不會也沒什麼關係，跟上面說的一樣主要是填空，程式邏輯跟該 project 相關的知識點才是做不做得出來的關鍵。

### [p0] Getting Started with Cloud Computing - Data Analytics using a Wikipedia Dataset

不算分。讓學生熟悉整個 project 的繳交流程，以及 cloud 的基礎操作。大致上分成幾個部分：

- 用 GUI console 在 AWS, GCP, Azure 創建資源，並且登入部署基本的網站
- 用 terraform 創建資源
- 用 Java 做資料前處理以及基本的單元測試＆測試驅動開發
- 用 python / pandas / jupyter notebook 做資料分析 
- 用 grep / awk 做資料分析

### [p1] Elasticity - Horizontal Scaling and Advanced Resource Scaling

![image](https://hackmd.io/_uploads/rkFQYf8GC.png)

三個 task：
- 用 python 或 java 做 ec2 的水平擴充
- 根據 loading 做到 auto scaling
- 改成用 terraform 做

如同上圖所示，如果機器開太少讓他超載，就會導致有些請求沒有辦法被處理，但開太多又會讓算力被閒置，換句話說就是浪費錢。這個作業就是在練習達到某個平衡，他要你能夠處理高峰時期的請求，同時又不能開太多機器，並且要維持一定的服務水平，評分依據如下：

| Performance Target | Threshold          | Score Calculation                            | Score                   |
|--------------------|--------------------|----------------------------------------------|-------------------------|
| Instance Hours     | 220 <= x <= 280    | $score_{ih} = (280 - x) * 100 / (280 - 220)$     | $min(score_{ih}, 100)$      |
| Average RPS        | 7 <= x <= 12       | $score_{avgrps} = (x - 7) * 100 / (12 - 7)$      | $min(score_{avgrps}, 100)$  |
| Max RPS            | x < 35             | $score_{maxrps} = -5$                            | $min(score_{maxrps}, 0)$    |

$$
Total\ score =  \frac{(score_{ih} + score_{avgrps}) \times 40}{2 \times 100} + score_{maxrps} 
$$

這次比較蠻麻煩的點是 task 2 每提交一次，就要等約 50 分鐘才會有結果（當然如果覺得有問題也可以自己提前結束）。

### [p2] Containers: Docker and Kubernetes - Linux Containers

![image](https://hackmd.io/_uploads/SkDcFfUfA.png)

使用 Docker 將服務容器化，並且部署到 Google Kubernetes Engine (GKE) 跟 Azure Kubernetes Service (AKS) 上，最後還要做 CI/CD 將整個流程自動化。這個 project 說大不大說小不小，全部做完花的時間並沒有很多，但是對這個主題有興趣的人，可以花很多時間在他的細節上。舉例來說，我們要容器化的服務是用 Java Spring Boot 寫的，其中還有用到 Redis Pub/Sub、STOMP 之類的技術，以及這個 micro-service 的架構是基於什麼理由選擇的，這些都蠻值得花時間去探討。

我做完這個 project 之後馬上把它寫到履歷上，後來就拿到了兩個相關的面試，代表這些技術還算是當前蠻熱門的。

### [P3.1] Cloud Storage - SQL and NoSQL

note: P3.1 跟 P3.2 都只有一個禮拜能做，但內容都不多（又或者是說很水）

對於 SQL 跟 NoSQL 的小練習，分別使用 MySQL、MongoDB 跟 Redis。基本上指令都給好了，真正要想的地方很少，無腦就可以做完。

### [P3.2] Cloud Storage - Heterogeneous Storage on the Cloud

![image](https://hackmd.io/_uploads/HJHKTGLfC.png)

部屬一個類似臉書的應用程式，其中的不同資料分別會用到不同種類的資料庫，最後還會把他串起來，成品大概長這樣：

![image](https://hackmd.io/_uploads/S1WxAf8G0.png)

其實我覺得主題還挺有意思的，現在的網站真的都是資訊爆量的狀況，對於不同的資料都有適合的存儲方式，如果有遵守最佳實踐的話，小小一個請求可能會像扇形那樣擴展開來，像後端的不同微服務去做連結。

![image](https://hackmd.io/_uploads/BJg2AMUfA.png)

但其實這個 project 的工作量跟 P3.1 差不多，如果有興趣的話還是得要自己去深入研究。

### [P4] Iterative Processing with Spark

學期後半來到了資料處理的部分，這個 project 是將簡化的推特資料處理過後做成 PageRank 的推薦系統，強制使用 spark + scala 來做。資料總共 10G，這裡使用 Azure 的 HDInsight 來開集群，一小時就要花 3 美金。

我認為算是在這邊學到蠻多的，畢竟之前處理資料的時候就是寫一個 python 然後讓他在那邊跑，從來沒有想過也可以用分散式運算來加速整個過程。這個工具除了介面有點舊之外，整體算是非常的完善。此外，這邊會跟小考那邊的閱讀部分關聯性蠻大的，有些背景知識我沒有好好去讀，在實際遇到問題的時候真的完全不知道該怎麼解決。

然後這個 project 的 writeup 問題十分之多，讓我花很多時間在根本不應該花時間的地方，我真是謝：）

### [Make-up] Functions as a Service

學期間突然出現的一個補救方案，教無伺服器運算，但我因為太忙 drop 掉了

### [P5] Stream Processing with Kafka and Samza

因為太忙 drop 掉了

### [P6] Machine Learning on the Cloud

![image](https://hackmd.io/_uploads/ryevEQIMR.png)

做了一個紐約市叫車價格預測 app，用 Google 的 Vertex AI 來做機器學習，使用 XGBoost 這個模型。雖然我大學有修過機器學習，但我幾乎都還給教授了。這裡也沒有很多的著墨，starter code 裡面已經完成了大部分，我們幾乎就是負責調參。我覺得算是對於現在大型的機器學習模型該如何訓練跟部署在雲端也是有點概念，但也僅止於淺嚐而已。

---

## Reading & Quiz

每週一次小考，在時間範圍內自己決定時間考，開始之後倒數計時兩小時寫。每次小考約有 10~20 篇的文章要讀，掃過大概要花 1~2 小時。主題很廣，跟 project 有一點點關聯，但也沒有說不會就做不出來。小考也不會難到很誇張，但是如果想要拿滿分的話，之前沒有學過相關內容的話，會需要蠻多時間消化的。

比較好的做法是每天看一點，嘗試完全理解閱讀內容，照理來說小考不會是問題。但我是沒有認識的人這樣真的做啦：）

內容包含：
- Introduction to Cloud Computing
    - Cloud Computing Overview
    - Economics, Benefits, Risks, Challenges and Solutions
- Cloud Infrastructure
    - Data Center Trends
    - Data Center Components
    - Cloud Management
    - Cloud Software Deployment Considerations
- Cloud Storage
    - Cloud Storage
    - Case Studies: Distributed File Systems
    - Case Studies: NoSQL Databases
    - Case Studies: Cloud Object Storage
- Distributed Programming and Analytics Engines for the Cloud
    - Introduction to Distributed Programming for the Cloud
    - Distributed Analytics Engines for the Cloud: MapReduce
    - Distributed Analytics Engines for the Cloud: Spark
    - Distributed Analytics Engines for the Cloud: GraphLab
    - Message Queues and Stream Processing
- Virtualizing Resources for the Cloud
    - Introduction and Motivation
    - Virtualization
    - Resource Virtualization - CPU
    - Resource Virtualization - Memory
    - Resource Virtualization – I/O
    - Case Study
    - Storage and Network Virtualization

---

## Team Project: High Performance Web Service

![image](https://hackmd.io/_uploads/BJzCtGIzC.png)

### Phase 1

總共要做 3 個 web service，分別是：

- blockchain 
- QRcode 
- Recommendation System

三個其實沒有什麼關聯，但在 Phase 2 跟 Phase 3 live test 的時候會同時向三個服務發送請求，在這個階段就是讓服務能夠正確跑起來，並且在預算內達到一定的 Request Per Second (RPS)。

這個階段比較像是讓我們去測哪個 web framework 跟 programming language 比較快，還有把整個服務串起來而已。

### Phase 2

第二階段對於 twitter service 的要求會再提高，並且加入了 live test。所謂 live test 就是老師會在同一時段向所有組別的服務發送請求，然後如果你在這個時段服務爆了，或是出任何問題的話，就直接會反映在你的成績上。然後這邊每小時的預算也要算好，如果在 live test 上每個小時花超過 0.7 鎂就會依比例扣分。

### Phase 3

第三階段則是讓我們測試更現代化的部屬方式，我們從原先用 kops 轉換到 EKS 上，儲存方式也從自己部署 mysql 變成 AWS 上的各種資料儲存服務。

### 隊友

其實我覺得 team project 的體驗很大程度在於隊友上，我覺得我算是被 carry 的那個，雖然最後沒有拿下榜一，但也算是排名靠很前面了，況且在 Phase 1 我們進度幾乎是領先所有隊伍好幾個禮拜，學期中也收到了下學期的 TA 面試邀請。我也有聽說其他組不太好的狀況，像什麼消失的拉，去寫其他作業的拉。

期末問卷有問到「如果重來你會怎麼選擇隊員」，其實我到現在也很難給出一個明確的答案。學期初教授其實有發信說不推薦跟認識的人，似乎以歷屆的數據來說，這種組隊方式狀況都會不太好。我自己這個組算是亂找的，因為我原本是想跟認識的人一起，但後來出了一些誤會導致我必須另尋組員。就我的結果來說還算不錯，只是我真的很難去下結論說跟熟人組隊就會比較不好。

---

## 其他

### TA

我有個同屆的台灣同學因為第一學期就跑去修 CC，所以我修這堂課的這學期就一直狂問他。根據他的描述，其實 TA 也並不會對整個課程了解透徹，他是跟我說他在 Office Hour 的時候也是看著他去年的作業在回答的，每個 TA 都有負責的 project，你可能只會對那個 project 特別熟。

然後這個 TA 的工作量好像特別大，他每週好像都會報滿 20 個小時（國際學生兼職時數上限），學生又超多，問問題的論壇常常都是爆滿的狀況，然後有些問題水平我看了也覺得這些人到底怎麼上 CMU 的＝＝，好處就是可以認識 SCS 學院的教授，還有一些主校區的神人同學。

### Sail() & OLI platform

學期末有一個超長的問卷是針對課程內容以及這兩個平台去做詢問的，Sail() 是做 project 的網站， OLI 則是閱讀跟小考。好像這堂課的授課方式會這麼特別就是因為這算是一個電腦科學教育方面的研究吧，而這兩個平台就是輔助的工具，說不定之後會上市之類的，但我個人是認為以學生視角來說這兩個平台並沒有特別突出的點。

---

## 參考資料

- [CMU 的 M.S. Software Engineering 第二學期心得](https://medium.com/cloud-guru-%E7%9A%84%E5%BE%81%E9%80%94/cmu-%E7%9A%84-m-s-software-engineering-%E7%AC%AC%E4%BA%8C%E5%AD%B8%E6%9C%9F%E5%BF%83%E5%BE%97-44b1dddf9af9)
- [CMU的Cloud Computing這堂課](https://blog.heron.me/cloud-computing%E9%80%99%E5%A0%82%E8%AA%B2-101b31f9d306)
- [在CMU学习15319/619 Cloud Computing是种怎样的体验？](https://www.zhihu.com/question/30405519)