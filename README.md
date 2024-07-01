# R 語言筆記

[TOC]

## 1.2 基本變數
- 宣告變數
    ```R
    a <- 1
    ```
- 資料型態
    - 數字
        ```R
        a <- 1
        ```
    - 字串
        ```R
        a <- "Hello"
        ```
    - 布林
        ```R
        a <- T
        ```
        ```R
        b <- F
        ```
        ```R
        c <- TRUE
        ```
        ```R
        d <- FALSE
        ```
- 輸出資料型態
    ```R
    mode(x)
    ```
- 輸出型態、資料的值
    ```R
    str(x)
    ```
- 輸出值的數量
    ```R
    length(x)
    ```
- 將資料型態轉為整數
    ```R
    as.integer(x)
    ```
- 根號
    ```R
    sqrt(x)
    ```
- 註解
    ```R
    # 加入井字號就是註解
    ```
- 給值符號
    ```R
    a <- 1
    ```
    ```R
    a = 1
    ```
- 顯示值
    ```R
    a
    ```
    ```R
    print(a)
    ```
## 1.3 向量
- 宣告向量
    ```R
    a <- c(元素1, 元素2 ,元素3, ...)
    ```
    e.x.
    ```R
    a <- c(1,3,5,2,4)
    ```
- 注意：同一向量內的資料型態需相同
- 取用向量中的值
    ```R
    a[索引值]
    ```
     e.x.
    ```R
    a[2]
    ```
    - 索引值從1開始
- 為各欄位命名
    ```R=
    麻將 <- c(1500, -800, 4000, -750, -1200, 1500) # 宣告向量名稱為「麻將」的向量
    射龍門 <- c(-1500, -800, 4000, -850, 1500, -250) # 宣告向量名稱為「射龍門」的向量
    除夕到初五的名稱 <- c("除夕", "初一", "初二", "初三", "初四", "初五") # 宣告向量名稱為「除夕到初五的名稱」的向量
    names(麻將) <- 除夕到初五的名稱 # 將向量「除夕到初五的名稱」中的值，對應到向量「麻將」中的值
    names(射龍門) <- 除夕到初五的名稱 # 將向量「除夕到初五的名稱」中的值，對應到向量「射龍門」中的值
    麻將 # 顯示向量「麻將」的值
    射龍門 # 顯示向量「射龍門」的值
    ```
- 存取連續的資料
    ```R
    a[3:5] # 存取向量 a 中，索引值 3～5 的資料
    ```
- 存取不連續資料
    ```R
    a[c(2,4,6)]
    ```
    ```R
    a[c("name2", "name4", "name6")]
    ```
- 計算加總
    ```R
    sum(向量名稱)
    ```
    e.x.
    ```R
    sum(射龍門)
    ```
- 計算平均
    ```R
    mean(向量名稱)
    ```
    e.x.
    ```R
    mean(射龍門)
    ```
## 1.3 矩陣
- 儲存相同資料
- 建立矩陣
    ```R
    matrix(1:9, nrow = 3, byrow = TRUE) # 矩陣的值為 1～9，列數為3，宣告一個以列為主的矩陣
    
    matrix(c(1,2,3), nrow = 3) # 1,2,3為向量，這樣也行
    ```
- 存取整欄（col）或整列（row）的資料
    ```R
    a[1,] # 存取第 1 row 的資料
    a[,2] # 存取第 2 col 的資料
    ```
- 為 col、row 命名
    ```R
    rownames(復仇票房紀錄矩陣) <- 電影名稱 #列
    colnames(復仇票房紀錄矩陣) <- 預算收入 #欄
    ```
## 1.3 資料框
- 建立資料框
    ```R
    資料框名稱 <- data.frame(向量1, 向量2, 向量3, ...)
    ```
    e.x.
    ```R=
    奇數 <- c(1,3,5)
    偶數 <- c(2,4,6)
    a <- data.frame(奇數,偶數)
    ```
    - 不同欄可儲存不同資料型態，長度要相同
    - 同欄的資料要相同(向量)，向量名稱可自動設定成欄的名字
- 顯示部分資料
    - 顯示前幾筆資料（預設為前 6 筆資料）
        ```R
        head(a)
        ```
    - 顯示後幾筆資料（預設為後 6 筆資料）
        ```R
        tail(a)
        ```
- 顯示資料框資訊
  ```R
  str(a) 
  ```
  ex.
  ```R
  id<-c(1,2,3)
  age<-c(25,30,35)
  sex<-c("male","female","male")
  pay<-c(1000,1500,2000)
  資料<-data.frame(id,age,sex,pay)
  str(資料)
  
  >str(資料)
  'data.frame':	3 obs. of  4 variables:  #obs.資料總數(列數)，variables變數總數(欄數)
  $ id : num  1 2 3
  $ age: num  25 30 35
  $ sex: chr  "male" "female" "male"
  $ pay: num  1000 1500 2000
  > 
- 存取資料框中的資料
    - 存取單筆資料
        ```R
        a[3,1] # 存取第 3 列第 1 欄的資料
        ```
    - 連續的資料
        ```R
        a[1:2,2:3] # 存取[1,2], [1,3], [2,2], [2,3]
        ```
    - 也可使用欄位名稱(使用文字型態)，e.x.
        ```R
        a[1:3,"prelnterest"]
        ```
    - 整欄資料(向量)
        ```R
        資料框名稱$欄位名稱
        ```
        e.x.
        ```R
        InDFrame$nowInterest
        ```
    - 滿足條件
        ```R
        subset(資料框名稱, subset = 邏輯判斷式)
        ```
        e.x.
        ```R
        sunset(InDFrame, subset = nowInterest<200)
        ```
- 回傳由小到大的排列順序（回傳的值為索引值）
    ```R
    order(資料框名稱)
    sort(名稱)
    ```
    ex.
    ```R
    #回傳由小到大的排列順序
    smallToBig<-c(100,1000,10)
    order(smallToBig)
    
    > smallToBig<-c(100,1000,10)
    > order(smallToBig)
    [1] 3 1 2

    #還原
    smallToBig[order(smallToBig)] #order(smallToBig)為索引值3,1,2
    
    > smallToBig[order(smallToBig)]
    [1]   10  100 1000
- 顯示編輯界面
    ```R
    edit(資料框名稱)
    ```
## 1.3 列表
- 建立列表
    ```R
    ListName <- list(obj_1, obj2, obj3, ...)
    ```
    - 可以放各種資料型態、資料結構
- 加入項目名稱
    - 方法一
        ```R
        ListName <- list(name1 = comp1, name2 = comp2, name3 = comp3, ...)
        ```
     - 方法二
        ```R
        StudentList <- list(StudentId, StudentSex, StudentName)
        names(StudentList) <- c("學生證號碼", "學生性別", "學生姓名")
        #names()也可提取欄位名稱(5.1)
        ```
- 新增資料
    ```R
        StudentList <- c(StudentList, comp1, comp2, ..., compN)
    ```
    - 可使用向量新增，再丟回原本的列表
## 1.4 流程控制-條件判斷
- 選擇判斷 if else
    ```R
    if(condition)express 
    
    # 若 condition 的條件為真，則執行 express
    ```
    ```R
    if(condition){
        express1
    }eles{
        express2
    }
    
    # 若 condition 的條件成立，執行 express1;不成立，執行 express2
    ```
    ```R
    ifelse(condition, a, b)
    
    # 若 condition 的條件成立，執行 a;不成立，執行 b
    ```
    ```R
    if(condition1){
        express1
    }eles if(condition2){
        express2
    }else{
        express3
    }
    
    # 若 condition1 的條件成立，執行 express1;不成立，執行 else if(condition2)。
    # 若 condition2 的條件成立，執行 express2;不成立，執行 express3。
    ```
- 選擇判斷 switch()
    ```R
    switch(指定第幾行或"那個名稱的程式碼",
        第一行:執行A,
        第二行:執行B,
        ...
        第N行:執行N
        )
    ```
    ex 1.
    ```R
    > switch(2,
    +     1+2,
    +     3*3,
    +     4^4
    + )
    
    [1] 9
    ```
    ex 2.
    ```R
    > switch("caseA",
    +     caseA=1+2,
    +     caseB=3*3,
    +     caseC=4^4
    + )
    
    [1] 3
    ```
    
- 四捨五入
    ```R
    round(數字, 所取捨的小數位數)
    ```
    ex.
    ```R
    round(73.3333, 2) = 7.33
    ```
## 1.4 流程控制-迴圈控制
- 迴圈控制 for()
    ```R
    for(i in x){
        每次要重複執行的程式
     }

    # i 表示迴圈執行到第幾次
    # x 表示迴圈需要執行的次數(1:9)
    # i 最多執行 x 次    
    ```
    - 執行次數明確
- 迴圈控制 while()
    ```R
    while(condition){
        每次要重複執行的程式
    }
    ```
    - 執行次數不明確
- 無條件捨去小數
    ```R
    floor()
    ``` 
- repeat 迴圈
    ```R
    x <- 1
    repeat{
        print(x)
    }
    
    # 無窮迴圈，可按 Ctrl+C 結束
    ```
    - 循環判斷、離開迴圈都需要自行編輯在{}中
- break 與 next
    - 在 for、while、repeat 中，功能為跳離迴圈
    - break 直接跳離迴圈 
    ```R
    x <- 1:10
    for(i in x){
        if(i == 6){
            print("i==6")
            break
        }
        print(i)    
    }
    x
    
    [1] 1
    [1] 2
    [1] 3
    [1] 4
    [1] 5
    [1] "i==6"
    > x
    [1]  1  2  3  4  5  6  7  8  9 10
    ```
     - next 執行下一個敘述
     ```R
     x <- 1:10
     for(i in x){
         if(i == 6){
            next
         }
         print(i)  
     }
     x
     
     [1] 1
     [1] 2
     [1] 3
     [1] 4
     [1] 5
     [1] 7
     [1] 8
     [1] 9
     [1] 10
     > x
     [1]  1  2  3  4  5  6  7  8  9 10
     ```
## 1.5 自訂函數撰寫
- 自訂函數
    ```R
    functionName <- function(參數1, 參數2, ..., 參數n){
        函數執行的程式
        return(輸出) #將結果回傳functionName
    }
    ```
    ex.
    ```R
    cube <- function(x){
        result <- x^3
        return(result)
    }
    cube(2)
    [1] 8
    
## 1.5 自訂函數撰寫-亂數函數
- 隨機抽樣 sample 函數
```R
sample(範圍, size = 數量, replace = 是否重複) 
```
ex.
```R
> sample(1:10, size = 2) # replace 預設為 FALSE(不重複)

[1] 3 5 
```

- rep()
    - 宣告大陣列的時候很麻煩
    ```R
    c(NA, NA, NA, ...) # 要打一千次
    #NA表示沒有任何值
    ```
    - 使用 rep()
    ```R
    rep(重複的物件, times = 次數)
    ```
    ex.
    ```R
    > x <- rep(NA,times = 3)
    + x
    
    [1] NA NA NA
    ```


## 補充 邏輯運算子


| 邏輯判斷  | 說明 |
| ------   | ----   |
| >        | 大於    |
| <        | 小於    |
| >=       | 大於等於 |
| <=       | 小於等於 |
| ==       | 相等    |
| !=       | 不相等  |
| !a       | 不等於a |
| a \| b   | a或b    |
| a & b    | a且b    |
## 1.6 資料輸入與輸出
- CSV 檔
    - 用純文字形式儲存表格資料，以逗號分隔表中的各欄位
    
- 檢查檔案存放位置 
    ```R
    getwd()
    ```

- 存取 CSV 檔
    ```R
    data <- read.csv("file.csv", header = T, sep = ",", fileEncoding = "Big5") 
    # 讀取檔案 file.csv，將標題(資料開頭)變成變數，分割字元為","，fileEncoding 用不同編碼方式讀取
    ```
    
- 尋找資料
    ```R
    a <- subset(data, condition <- 日期 == "110/11/23") 
    # 索取日期欄位為"110/11/23"的資料，condition 存放條件，condition 為變數名，可自訂
    ```
    
- 最大值、最小值、平均值
    - 最大值
    ```R
    a <- subset(data, condition <- 收盤指數 == max(data$收盤指數)) 
    # 找到收盤指數的最大值，condition 存放條件，condition 為變數名，可自訂
    #(資料框名稱$選擇欄位)
    ```
    - 最小值
    ```R
    a <- subset(data, condition <- 收盤指數 == min(data$收盤指數)) 
    # 找到收盤指數的最小值，condition 存放條件，condition 為變數名，可自訂
    ```
    - 平均值
    ```R
    a <- mean(data$收盤指數) # 找到收盤指數的平均值
    ```
- 文字型態轉換成數值型態
    ```R
    as.numeric() #as轉換
    ```
- 偵測是否有NA值
    ```R
    is.na() #is判斷
    ```
## 1.7 基本繪圖
- 折線圖
    ```R
    plot(data$收盤指數, type = "l", col = "blue", lty = 2, main = "四月份收盤指數", xlab = "X", ylab = "Y")
    #type設定線條種類,l為線,p為點
    #col設定線條顏色，預設黑色
    #lty設定線條效果，2為虛線，1為實線
    #m, x, y設定名稱
- 點圖
    ```R
    dotchart(data$最低指數, label = data$日期, pch = 4, color = "red", main = "四月份最低收盤指數", xlab = "指數", ylab = "日期")
    #label標示y軸
    #pch點圖符號選擇
    ```
- 長條圖
    ```R
    barplot(平均資料, col = c("1", "2", "3", "4"), beside = T, names.arg = c("平均開盤", "平均最高", "平均最低", "平均收盤"), main = "平均開盤最高最低收盤資料")
    #col顏色
    #beside = T長條圖不重疊
    #names.arg替長條命名
    ```
    ```R
    barplot(data$收盤指數-15000, main = "四月份收盤指數") #可設定基準值
    ```
- 圓餅圖
    ```R
    pie(data$最高指數, main = "最高指數")
    ```
- 盒型圖
    ```R
    boxplot(data$開盤指數, data$最高指數, data$最低指數, data$收盤指數, col = "10", border = "43")
    #直接放資料
    #col盒型顏色
    #border框線顏色
    ```

## 2.1 簡介網路常用基本程式語言
- HTML 超文件標示語言
    - 骨架
    - 格式
    ```
    <html>
    <title>HTML</title>
    <body>
        This is HTML!
    </body>
    </html>
    ```
- CSS
    - 外觀
    - 統一網站中的網頁格式
- 網絡爬蟲
    - readLines() 函數
    - 設變數儲存網址
    ```R
    url <- "https://www.imdb.com/title/tt4154756/"
    ```
    - 擷取 HTML 原始碼(讀入的原始碼為字串向量)
    ```R
    avengers <- readLines(url)
    ```
    - 顯示 HTML 原始碼的第 10 至 20 行
    ```R
    avengers[10:20]
    ```
## 2.2 網路爬蟲套件-Rvest1

- 使用revst套件流程
    1. 用 library() 載入 rvest 套件 
    2. 輸入要捉取的網頁網址
    3. 將網頁原始碼捉下來，read_html()函數
        ```R
        read_html("連結")
        #讀取網頁原始碼
        ```
    3. 找到對應的CSS名稱
    4. 使用html_nodes()函數、CSS名稱分析網頁，選取需要的內容
        ```R
        html_nodes(捉取到的網頁資料, "對應的CSS標籤")
    6. 顯示結果，html_text()函數轉文字
- 特定字元取代
    ```R
    gsub("要被取代的字元", 被取代字元所在字串, replacement = "取代成的字元")
    ```
    - ex
    ```R
    stringA <- "AABB"
    stringA
    [1] "AABB"
    
    stringB <- gsub("A", stringA, replacement = "C")
    stringB
    [1] "CCBB"
    ```
    - 移除多餘空格
    ```R
    gsub("\\s+", text, replacement = "")
    #\\s+代表一個以上的空格
    ```
    
- CSS選擇器程式
    - Google Chrome F12 功能運用 
        1. 按F12
        2. 按左上角圖示 
    - 安裝 CSS 選擇器 Chrome 套件：SelectorGadget
        - 紅色不要，綠色要，黃色跟要的使用同樣的CSS名稱
        - 只能抓靜態資料，超連結時選擇不了
    - 安裝 rvest 套件
    ```R
    install.packages("rvest")
    ```
    - 擷取 Yahoo 關鍵字、頭條新聞標題
    ```R
    library(rvest) # 載入函式庫
    
    # 下載 Yahoo 首頁
    page.source <- read_html("https://tw.yahoo.com/")
    
    # 選出熱門關鍵字
    hot.keywords <- html_nodes(page.source, ".keywords .Whs-nw")
    html_text(hot.keywords)
    
    # 選出頭條新聞標題
    news.title <- html_nodes(page.source, ".Va-tt")
    html_text(news.title)
    ```
    - 除錯
        - 出現錯誤
        ```R
        Error in loadNamespace(i, c(lib.loc, .libPaths()), versionCheck = vI[[i]]):there is no package called 'stringi'
        ```
        - 安裝 stringi 套件
        ```R
        install.packages("stringi")
        ```
## 3.1 ggplot2套件介紹
- 圖層概念，用 + 將圖層結合
- 安裝 ggplot2套件
    ```R
    install.packages("ggplot2")
    ```
- ex
    ```R
    library(ggplot2)
    ggcars <- ggplot(cars, aes(x = speed, y = dist)) + geom_point()
    ggcars
    
    #用 library() 載入 ggplot2 套件
    #將 cars(資料框型態) 載入 ggplot()，aes()設定 X、Y 軸
    #用 geom_point() 繪製散佈圖
- geom_開頭函數可支援不同圖形(比內建的精緻)
    - 散佈圖
    ```R
    geom_point()
    ```
    - 直方圖
    ```R
    geom_histogram()
    ```
    - 盒型圖
    ```R
    geom_boxplot()
    ```
    - 線圖
    ```R
    geom_line()
    ```
    - 長條圖
    ```R
    geom_bar()
    ```
- 套件繪圖架構
    - 原始資料配合五大類圖層函數
    ```R
    ggplot()
    #資料結構為資料框
    ```  
    - 美學對應幾何圖案
    ```R
    aes, geom_
    #資料和圖形的相對關係
    ```
    - 統計轉換
    ```R
    stat
    #將資料轉換成各項統計量
    ```
    - 座標系統
    ```R
    coord
    #設定繪圖時的座標系統
    ```
    - 主題
    ```R
    theme
    #設定資料外的繪圖元件(座標軸、畫布格線、說明文字)
    ```
    - 繪圖面
    ```R
    facet
    #資料分散在多張子圖形時方便比較使用
    #用~選擇欄位做分類
    ```
## 3.2 ggmap 套件介紹
- ggmap 地圖套件
    - 專門用來繪製地圖的套件
    - 將統計資料和地圖結合，顯示需要的結果
## 4.1 機器學習介紹
- 讓電腦從資料中自動學習規則獲得規律，並對未知資料進行預測
- 機器學習流程
    1. 提供資料給電腦訓練
    2. 產生相應的規則
    3. 使用規則對資料進行預測
    4. 產生預測結果
- 機器學習分類
    - 監督式學習：有標準答案
        - 回歸分析
        - 統計分類：決策樹
    - 非監督式學習：沒有標準答案
        - 分群(聚類)k-means分群演算法 
## 4.2 監督式學習
- 建立決策樹
    1. 找根節點：找錯誤決策數量最少的
    2. 排序節點：錯誤決策數量由小到大，若數量相同則錯誤較平均的先
- 繪製決策樹範例
```R
library("rpart") #決策樹套件：建立決策樹
library("rattle") #rpart繪圖套件：畫出使用rpart套件得出的決策樹函數，包含plot()、text()
library("RColorBrewer") #資料探勘視窗套件，美化用
library("rpart.plot") #顏色套件，美化用

評估資料 <- read.csv("4.2_決策樹訓練資料評估新設店面.csv", header = T, sep = ",", fileEncoding = "Big5")
評估資料

評估資料樹 <- rpart(決定 ~ 城市規模 + 平均收入 + 教育程度 + 當地投資者, data = 評估資料,
                    method = "class",
                    control = rpart.control(minsplit = 5))
#rpart(被預測的變數 ~ 做預測的變數1(欄位名稱)+ 做預測的變數2 + ... + 做預測的變數n, data = 給決策數的資料, 
        method = 決策樹類型"class建立分類樹",
        control = 調整決策樹rpart.control對決策樹做相關設定高度、資料量(minsplit新節點所需資料量 = 5))
#另一寫法rpart(被預測的變數 ~ ., .代表被預測的變數外的所有變數

plot(評估資料樹) #繪製決策樹
text(評估資料樹) #插入標籤
fancyRpartPlot(評估資料樹) #美化
```
## 4.3 非監督式學習
- k-means 
    -  對資料進行分群，將相似的資料歸類在一起
    -  每一組稱為群集
    -  物以類聚
- k-means步驟
    1. 載入資料，決定分 K 群(K = 3)
    2. 隨機選 K 個點做群集中心點(群心/質心)
    3. 計算資料離哪個群心最近(直線距離)
    4. 將資料歸於最接近的群心
    5. 再次計算新的群心
- 範例
```R
客戶資料 <- read.csv("4.3_客戶區隔.csv", header = T, sep = ",", fileEncoding = "Big5")
客戶資料

客戶分群 <- kmeans(客戶資料, centers = 3, nstart = 10)
#kmeans(載入要分群的資料, centers = 分幾群, nstart = 重複執行次數，每次執行時質心隨機選取，預設為1)
客戶分群

plot(formula = 購買總價 ~ 客戶, data = 客戶資料, col = 客戶分群$cluster)
#plot(formula = y軸 ~ x軸, data = 指定輸入資料, col顏色 = 客戶分群$cluster用cluster欄位的資料當顏色)

points(客戶分群$center[, c('客戶', '購買總價')], col = 1:3, pch = 8, cex = 2)
#群心
#points(客戶分群$center[, c('客戶', '購買總價')選要用的資料]群心所在座標, col顏色 = 1:3, pch符號 = 8, cex大小 = 2)

```
- K-means顯示結果
```R
> 客戶分群 
#結構為list
K-means clustering with 3 clusters of sizes 6, 3, 3

#各群平均值(質心位置)
Cluster means: 
      客戶 客戶收入.千    交易數 購買總價
1 8.333333    42.50000  5.500000 143.3333
2 6.000000    72.00000  9.333333 483.3333
3 3.333333    74.66667 14.333333 866.6667

#客戶被分到第幾群
Clustering vector: 
 [1] 2 3 3 1 3 1 2 1 1 2 1 1

#群之間的距離平方占總體距離平方差的比率，愈大分群效果愈好
Within cluster sum of squares by cluster: 
[1] 39135.667  2583.333  7098.667
 (between_SS / total_SS =  95.6 %)

#分群結果數據
Available components:

[1] "cluster"      "centers"      "totss"        "withinss"     "tot.withinss"
[6] "betweenss"    "size"         "iter"         "ifault"      
> 
```
## 5.1 文字探勘
- 從文字中分析有用的資訊，找出潛在價值
- 步驟
    1. 建立語料庫
        收集文件、資料清理
    2. 產生詞彙文件矩陣TDM
        選擇詞袋，計算各單字詞會出現頻率
    3. 挖掘TDM找出模式
        使用資料探勘工具，例:分類、群集
- 詞彙文件矩陣TDM
    - 列為詞彙，欄為文件(段落)
    - 表格中為詞彙在文件中出現的次數
- 文字雲範例
```R
library(tm)

speach <- readLines('JobsSpeech.txt') #載入演講稿
corpus <- VCorpus(VectorSource(speach))
#VCorpus()建立動態語料庫
#VectorSource(speach)轉成文字向量


#資料清理
corpusSW <- tm_map(corpus, stripWhitespace)
corpusTL <- tm_map(corpusSW, content_transformer(tolower))
corpusRN <- tm_map(corpusTL, removeNumbers)
corpusRP <- tm_map(corpusRN, removePunctuation)
corpusRW <- tm_map(corpusRP, removeWords, stopwords("english"))
corpusST <- tm_map(corpusRW, removeWords, c(stopwords("english"), "dont", "didnt"))
#tm_map(語料庫, 清除或轉換的指令)
#stripWhitespace刪除空白
#content_transformer(tolower)全部轉小寫，content_transformer(toupper)轉大寫
#removeNumbers刪除數字
#removePunctuation刪除標點符號
#removeWords移除指定詞彙
#stopwords("english")移除詞集，可用向量增加詞集

#建立TDM，將內容轉為矩陣結構
tdm <- TermDocumentMatrix(corpusST)
tdmMatrix <- as.matrix(tdm)
#TermDocumentMatrix(語料庫)將語料庫轉為詞彙文字矩陣

#按照單字出現次數由多到少排序
tdmSort <- sort(rowSums(tdmMatrix), decreasing = T)

#將結果用資料框表示
tdmdf <- data.frame(freq = tdmSort)
tdmdf

#用文字雲顯示
tdmdfwd <- data.frame(tdmdf, words = names(tdmSort))
#建立資料框，names()提取欄位名稱

#install.packages("wordcloud")
library(wordcloud)
wordcloud(tdmdfwd$words, tdmdfwd$freq, col = brewer.pal(8, "Set2"), min.freq = "10", random.order = F)
#wordcloud(文字, 頻率, 顏色, 最低頻率才能出現, F中間到外圍由多到少)

```
- TDM內部相關資訊
```R
> tdm <- TermDocumentMatrix(corpusRP)
> tdm
<<TermDocumentMatrix (terms: 680, documents: 38)>> #詞彙量680，文件38
Non-/sparse entries: 1236/24604 #有值/沒有值
Sparsity           : 95% #稀疏性，有值和沒值的格數比例，愈高愈稀疏
Maximal term length: 16 #最長詞彙長度
Weighting#權重      : term frequency (tf) #詞頻
```
- 互動式文字雲範例
```R
library(wordcloud2)

speach <- readLines('JobsSpeech.txt')
corpus <- VCorpus(VectorSource(speach))

corpusSW <- tm_map(corpus, stripWhitespace)
corpusTL <- tm_map(corpusSW, content_transformer(tolower))
corpusRN <- tm_map(corpusTL, removeNumbers)
corpusRP <- tm_map(corpusRN, removePunctuation)
corpusRW <- tm_map(corpusRP, removeWords, stopwords("english"))
corpusST <- tm_map(corpusRW, removeWords, c(stopwords("english"), "dont", "didnt"))

tdm <- TermDocumentMatrix(corpusST)
tdmMatrix <- as.matrix(tdm)

tdmSort <- sort(rowSums(tdmMatrix), decreasing = T)

tdmdf <- data.frame(word = names(tdmSort), freq = tdmSort)

wordcloud2(tdmdf, size = 0.5, shape = "cardioid", color = "pink")
#wordcloud2(載入資料, 大小, 圖案, 顏色)
#載入資料為資料框，要有詞彙和頻率
```
- magrittr:%>%管線運算子
    - 多個函數串聯使用，以資料流的方式處理資料
    - 優點:可不需設定過多變數，簡化同時保持可讀性
    - 前一個函數的輸出結果作為下一個函數的輸入結果
    ```R
    #法一
    tfSort <- table(segment(content, cutWord)) %>%
              sort(decreasing = T)
    #法二
    tfSort <- sort(table(segment(content, cutWord)), decreasing = T)
    ```
- 中文斷詞範例
```R
install.packages('jiebaR')
install.packages('magrittr')

library(jiebaR) #中文文字探勘斷詞套件
library(wordcloud2)
library(magrittr)

content <- readline("JobsSpeech_CT.txt")
content <- gsub("[0-9a-zA-Z]+?", "", content)#用正規表示式移除英文數字

#設定停止詞
cutWord <- worker(stop_word = "stopWords.txt") #設定斷詞工具
#worker(user = "專有名詞斷詞檔名", stop_word = "停止詞檔名")
#建立外部檔，格式UTF-8，第一隔空格

new_user_word(cutWord, c("老實說", "里德學院"))

tfSort <- table(segment(content, cutWord)) %>%
          sort(decreasing = T)
#segment(資料, 斷詞器)
#table()計算詞彙出現次數，並以詞彙命名欄位，資料型態為數值

wordcloud2(tfSort, size = 0.5, color = "pink")
```