---
title: CMU-SV MSSE 第一學期心得
date: 2023-12-25
slug: cmusv-semester-1
image: https://upload.wikimedia.org/wikipedia/commons/d/d4/Carnegie_Mellon_West_Building_23_Front_Entrance.jpg
categories:
    - CMU
---

# CMU-SV MSSE 第一學期心得

![](https://sv.cmu.edu/_files/images/logos/cmusv.png)

### Program 簡介

program 全名為 Master of Science in Software Engineering，找工向 program，16 個月畢業，如果是春季入學的話不能實習，除非你先去其他學校半個學期

在收人方面我感覺托福 95+ 應該就夠了，背景我猜是看工作經歷，然後如果有網頁開發感覺更好（畢竟這邊必修主要都教這個），但也是有部分人沒有工作經驗。另外轉碼感覺也蠻友好的，很多大學都不是 CS 畢業的

MSSE 畢業所需學分數為 97，但每學期至少修滿 36 學分（== 3堂課），且每學期至多能選一堂遠距課程。（第一學期有一堂一學分的必修課叫做 intro to grad study）

![image](https://hackmd.io/_uploads/HytTKWAUT.png)

必修課總共有八堂，畢業條件是五堂，其中一堂可以用跟教授做 research 來抵免，或是有什麼特殊原因可以用其他選修來抵（需要提交申請，但聽說通常不會過）

三堂選修課可以選主校區的課，但選擇不多，如果很在意課程品質來這裡可能會很失望。

![image](https://hackmd.io/_uploads/ry0cFZAIT.png)

老師大概是上面這四位，其中 H 老師好像是這個 program 的老大的樣子吧，但他本人在匹茲堡校區。選課跟 research 的話大家都會推 Leo

（第二學期的我：SV 校區的課還是不要抱太大的期望🥲）

---

## 選課

### 18-652 Foundation of Software Engineering

這個 program 的必修中的必修，一定要在第一學期修完，不然很多必修都會擋這堂課。

基本上只有 SE 的學生選得到這堂課，但我覺得其他 program 應該也不會想修這堂課：）

#### Syllabus

https://docs.google.com/document/d/1en0Hlw9SL1zkjHdfYg3ewvW-xFNuyUzaTQ5bUlDYNAM/preview

#### Grading Rubric

| Component | Performance Criterion | Weight (%) |
| --- | --- | --- |
| Final Quiz | Individual | 20 |
| Pre-enrollment Assignment | Individual | 5 |
| Readiness Quizzes (Post-prep quizzes and In-class Q&As) | Individual | 10 |
| Collaboration Skills Training | Individual | 5 |
| SE Project Iteration 4 | Individual | 15 |
| SE Project Iterations 0, 1, and 2* | Team | 15 |
| SE Project Iterations 3 and 5* | Team | 15 |
| SE Project Presentation | Team | 10 |
| Show-and-Tell Presentation | Team | 5 |
| Total | - | 100 |
| Total with bonus points (max. 3 points) (awarded in general for exceptional class participation at the discretion of the faculty) | - | 103 |

#### 課程內容

- Software development methods
- Object-oriented technology
- Object-oriented analysis and design
- Requirements
- Software architecture
- Design patterns
- Software testing
- Technical development practices
- Code quality: code reviews and static analysis
- Software project planning and estimation

課程內容為所有跟軟體工程相關的知識，包含開發方法（scrum, kanban）、軟體架構、設計模式、軟體測試、品質管理...等，每個知識點都不會到太深。

上課的方式是先在家看預錄的影片（通常不超過半小時，目測大概是三到五年前錄的），看之前有個 pre-quiz 讓你對於接下來會講的內容有點概念，看完之後有個 post-quiz 驗收，並且會算到成績裡面。上課也會有課堂小考，並且針對影片內容做更深入的討論，但大部分的時間會做跟 group project 相關的活動與討論。

#### Group Project

課程透過網頁前後端開發來實踐上課的內容，技術規定後端使用 express.js，前端 "不能" 使用任何開發框架（React/Vue/Angular），其餘都可以自己決定。這個專案會有大約 4~5 人的團隊下去進行，是由老師透過一個小調查來隨機分組，每週都會跟 TA (scrum master) 有一個 meeting，個人覺得進度蠻緊湊，常聽說有組別會為了趕 deadline 而熬夜。

每次 iteration 都有約兩到三個 use case 要去做，時長大約是兩個禮拜。mid-iteration會驗收跟文件比較相關的內容（OOAD、RESTAPI 文件、流程圖），end-iteration 則是看 demo。每次 iteration 都會多加一些額外的需求，像是要加入單元測試、加入 CI/CD、使用第三方靜態分析工具並提升品質到多少等。

第四次迭代會需要每人自己提出要做的功能，而且內容必須包含前後端、CRUD 四種操作、要有兩個以上使用者的互動，所以不能說你在整個學期都只會做某方面的事情而已。第五次迭代則是要重構並且整合第四次迭代的所有功能，還有其中一個 use case 讓蠻多組別整個程式碼大重寫 -- 允許使用者更改使用者 id。因為很多人直接用使用者 id 來當作資料庫的 row unique id，在前四次迭代因為他的確是獨一無二的，因此都完全沒問題，但第五次迭代加入這個功能之後，除了要大改資料庫之外，因為到這個階段程式碼也不少了，常常牽一髮動全身，因此最後聽說蠻多組別在熬夜的。

#### 心得

常聽到有人抱怨說這堂課沒什麼用，但卻要花很多時間。但我認為這堂課名畢竟叫做「軟體工程」而非「網頁開發」，核心還是這些軟體工程相關的知識。這也反映到這個 program 比較偏找工向的特色，課程並非是這個 program 的重點（雖然依舊有一些主校區的神課可以選），如果想要在這裡學到一些硬知識底子還是有點困難的。

此外，學期初的分組將會決定這整個學期的學習體驗，有看到有些組別好到不行，也有吵架翻臉的。~~然後學期初的調查可以把自己寫的爛一點，可能比較容易配到大神（？~~

----

### 18-654 Software Testing and Verification

#### Grading Algorithm

| 15% | Project 1 |
| --- | --- |
| 15% | Labs |
| 30% | Assignments |
| 15% | Midterm Exam |
| 15% | Final Exam |
| 10% | Participation |
| 100% | TOTAL |

#### 心得

前半段教各式軟體測試方法，後半段教軟體驗證。主要使用 Java，軟體驗證用到 spin / promela。

兩次作業四次 Lab，Lab 允許兩個人一起寫。學期中還有一個大 project，是用課上教的方法應用在開源的專案上。如果 project 沒有堆到最後才在做的話，這堂課的作業應該都不會花到太多時間。

上課方式就是普通的講課，老師在主校區所以是用遠端連線的，沒來不會給 Zoom 連結，但也不點名。老師會很期待大家跟他互動，只是他講得沒有什麼起伏，大家也不知道聽不聽得懂，所以通常不太會有人理他😂

期中期末考試前老師會給考古，基本上做到熟就能拿到蠻高的分數，如果能透徹理解拿滿應該是沒問題的，班上平均應該有 90% 以上吧，認識的人都拿Ａ（學期成績 90+）。

我自己認為教的主題都還蠻有趣的，課程規劃的也很好。但我感覺課程的教材好像很久沒有更新了，promela 也不知道有沒有人在用，常常會有在用上古時期的工具的感覺。另外，因為作業比較偏向 Lab 的形式，個人覺得學得雖廣但有點淺。

----

### 18-656 Functional Programming in Practice

![上完這堂課覺得學期初老師給的這張圖完全沒有騙人騙人😅](https://hackmd.io/_uploads/Hk2pPEWYp.png)

學期前半介紹 functional programming 的基本概念跟 F# 基礎語法，接著兩週的 Domain Driven Design 工作坊做後續期末 project 的系統設計，後面是比較進階的的概念（ex: railway oriented programming, map reduce）

期末 project 是做一個加密貨幣套利的系統，全部都必須使用 F#，並且完全遵照 functional programming 的規範。後期會跟一些 Azure 的服務做串接，另外還有一些加分的串接項目（ex: 使用 Azure HDInsight、把系統做成分散式運算、部署）。

> 好像很多人聽到加密貨幣就覺得很潮，但除了 App 場景應用在加密貨幣上之外，其他完全沒有關聯。

對於微軟的開發生態系不熟悉的人在這邊可能會有點吃力，而且學了一個 F# 還真的不知道要幹嘛，到底有誰在用這個＝＝？此外，我也真的聽不太懂這個老師上課到底在教什麼，有可能是我英文太差的問題，但好像也蠻多人反映聽不懂的。

前半學期我除了上課之外鮮少會再額外花時間，所以我常常推坑別人說這堂很水。但後期做 project 又突然變得超肝，老師也有注意到這個問題，一直把作業需求改低，最後甚至還有因為測試的 API 老師那邊來不及開發所以不測的。因為是第一個學期開，所以發生這些還蠻可以理解的，後續就不知道會改成怎樣了。

---

## 生活

### 校園

SV 校區在 mountain view 的 NASA 園區，建築主要只有一棟樓，資源不多但其實學生也不多，會議室幾乎都借得到，自習的話這棟樓各個有桌椅的地方都還蠻合適的。此外還有咖啡機、冰箱、微波爐、各式餐具，如果找得到球友的話還有提供網球、籃球跟橄欖球可以到旁邊玩。但沒有圖書館、沒有餐廳。

裡面的學生來自三個 master program -- ECE SE, III SM, INI MITE，主要都是中國人跟亞洲人。

### 職涯服務

可以用學校的 Handshake 平台來預約，職涯顧問人很好很有耐心，但我覺得效果還是蠻有限的，如果完全沒有方向或是當作練英文還蠻合適的，也幾乎都預約的到。

此外，還有一個叫做 Peer Career Consultant（PCP）的學校組織，他們算是領時薪的學生，如果沒有同儕能幫忙互相看可以去找他們，而且他們常常就坐在大廳等人去問。

![](https://s3.amazonaws.com/handshake.production/app/public/assets/career_fairs/40983/original/Converge2023.png?1685122906)

職涯中心除了舉辦 Career Fair 之外，也會常常邀請校友來跟大家介紹自己的公司或一些求職技巧，但這就比較憑個人本事了，目前我認識的人當中還沒有聽到有人因此拿到面試的。

---

## 外部連結

### 學校資訊

- [CMU ECE MS Handbook（每年都會更新）](https://www.ece.cmu.edu/_files/academics/ms-sv-catalog-handbook.pdf)
- [MS-SE Program Orientation](https://drive.google.com/file/d/1lyi4UqW68tXxWm0VEVljh6uLpfHsAFEs/preview)
- [ECE Grad Program Overview](https://drive.google.com/file/d/1972yvKWyIHLEr1c1lSjdvp9eXgu4WWmH/preview)

### 相關社團

- [CMU TSS in Bay Area](https://www.facebook.com/groups/cmusvtaiwan/)
- [TSS in Pittsburgh](https://www.facebook.com/groups/tsstaiwan/)

### 課程資訊

- [CMU Schedule Of Classes](https://enr-apps.as.cmu.edu/open/SOC/SOCServlet/search)
- [Discord | @TurtleBot](https://discord.com/channels/@me/1095902258140561509)
- [CMU Courses](https://cmucourses.com/)
- [CMUSV 個別課程心得](https://docs.google.com/presentation/d/1r4Vv5UZMXRDcf2_79wko1yLAgIHQgNx1XxOJ5lKt92o/)

### 其他參考資料

- [CMUSV TSS Handbook](/@r1psPkx2S-a3PJEGheDl7g/SkpKlvvm9)
- [(2023) 进可攻退可守的找工神校：CMU-SV MSSE 第一学期体验](https://www.1point3acres.com/bbs/thread-959513-1-1.html)
- [(2021) CMU-SE-SV 就读体验及选课分享。很高兴可以看到，这里变得越来越好](https://www.1point3acres.com/bbs/thread-925407-1-1.html)
- [(2021) yet another CMU-SV-SE一年半的感受/选课/排雷](https://www.1point3acres.com/bbs/thread-754839-1-1.html)
- [(2021) CMU SE SV劝退指南 - 纠结中的新生必看](https://www.1point3acres.com/bbs/thread-750772-1-1.html)
- [(2021) CMU SESV劝退贴【续】](https://www.1point3acres.com/bbs/thread-752084-1-1.html)
- [(2020) CMU SESV 入学感受+劝退指南](https://www.1point3acres.com/bbs/thread-693086-1-1.html)
- [匹茲堡生存手冊](https://surviverse.org/)
