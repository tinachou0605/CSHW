# 正規表達法 
![image](https://user-images.githubusercontent.com/91866934/148968171-ac67bda8-d7bf-463a-bdaa-997ac22f2e13.png)
![image](https://user-images.githubusercontent.com/91866934/148968366-a598f51b-0703-4305-ad11-f68891b72841.png)
![image](https://user-images.githubusercontent.com/91866934/148968450-8764b3a5-1df8-46ea-bef6-64a874d44eb2.png)
- . 點
  - 點可代替所有可能的字元（字母、數字或符號）
- ? 問號
  - 比對前一個字串或是不比對
- \* 星號
  - 比對前一個字串零次或是多次
- \- 破折號
  - 一數到另一數  
-  \+ 加號 
    -  跟星號相似，差別在於至少要與前一個字比對一次或以上
- | 直線
  - 或者
- ^ 插入符號 和 $ 錢字符號
  - ^插入符號是比對前開頭，$錢字符號則是比對結尾
- \ 反斜線
  - 將任何特殊字元，恢復成一般字元
- () 括號
  - 把想找的相關字詞放入括號內，可依照括號裡的字元排序找到可能的結果
- [] 中括號 
  - 任意比對字串內的每個項目

# grep參數
- -i → 忽略大小寫
- -n → 顯示匹配行及行號
- -r → 遞歸顯示目錄
- -c → 只輸出匹配行的計數
- -v → 只列出不符合的內容
- --color=never|always|auto → 顏色顯示
- -A → 多顯示匹配行的後幾行
- -B → 多顯示匹配行的前幾行
- -C → 多顯示匹配行的前後幾行
# grep + 正規表達法
- 開頭結尾
  - a開頭 → ls | grep “^a”
  - a或b結尾 → ls | grep “[ab]$”
- 出現次數
  - a開頭，出現0次以上 → ls | grep “^a*”
  - a開頭，出現零次或一次 → ls | grep “^a?”
  - a開頭，出現一次以上 → ls | grep “^a+”
- 多種組合
  - 含有ab或cd → ls | grep “ab\|cd”
  - 含有ab開頭或cd結尾 → ls | grep “^ab\|cd$”
# WC 文字處理工具
- wc → 計算指定檔案內容的換行數、字數與位元組數
  - -l → 只計算換行數
  - -w → 只計算字數
  - -c → 只計算位元組數
  - -m → 只計算字元數
  - -L → 計算最常行的長度
# Cut 文字處理工具
- cut → 逐行擷取部分字元或欄位資料
  - -b → 輸出的指定範圍以bytes作為單位
  - -c → 輸出的指定範圍以字元數量作為單位
  - -d → 指定分隔字元，default為tab作為分隔
  - -f → 輸出的指定範圍(每筆data的第幾column作為區分)
  - -s → 若該行無分隔字元則不顯示
# Paste 文字處理工具
- paste → 將每個文件以列對列的方式，一列一列加以合併
# Diff 文字處理工具
- diff → 比較文件的內容，特別是兩版本不同的同份文件
  - -y → 以並列方式顯示文件的異同之處
  - -W → 使用-y參數時，指定欄寬
  - -C → 前後輸出格式
  - -u → 統一格式輸出
# 文字處理工具
- &gt; → 覆蓋原有檔案
- &gt;&gt; → 追加檔案，不覆蓋繼續寫
# Sort 文字處理工具
- sort → 處理各種文字資料的排序問題
  - -f → 忽略大小寫
  - -u → 去除重複資料
  - -r → 反向排序
  - -t → 指定欄位的分隔字元(default=blank or tab)
  - -k → 指定欄位的編號
  - -n → 依照實際數值的大小排序
  - -h → 對有單位的數值排序
  - -M → 依照月份排序
# Uniq 文字處理工具
- uniq → 將連續重複文字刪除
  - -c → 計算文字行重複次數
  - -D → 只輸出有重複的文字行
  - -d → 將重複行刪掉
  - -u → 只輸出沒有重複的文字行
  - -f → 指定要跳過的欄位
  - -s → 跳過每一行開頭幾個字元
  - -w → 只比較每一行開頭幾個字元
  - -i → 忽略大小寫
# Tr 文字處理工具
- tr → 替換或刪除操作的字串轉換
  - -c → 用set1中字符集的補集替換此字符集，且字符集需符合ASCII
  - -d → 刪除檔案中所有在set1中出現的字元
  - -s → 刪除檔案中重複且set1中出現的字元，只保留一個
# Join 文字處理工具
- join → 將兩個文件中，指定欄位內容相同的行連接起來
  - -1 → 連接filename1指定的欄位
  - -2 → 連接filename2指定的欄位
  - -t → 使用欄位的分隔符號
  - -i → 忽略大小寫
  - -o → 按指定的格式顯示結果
  - -a → 除顯示結果，原檔案的其他行也顯示

# awk 文字分析工具
- 常用在對文字和資料進行分析處理
- 檔案逐行的讀入
- 以空格為預設分隔符號
# awk 語法 
- 常用引數
  - -F 指定分隔符(可是字串或正規表達法)，預設是空白(space)
  - -f 從指令碼檔案(awk script)中讀取awk命令
  - -v var=value賦值變數，將外部變數遞給awk
- awk 參數
  - 0 → 當前record(列、橫行)
  - $1~$n → 當前record的第N個欄位
  - FS → 輸入field直欄分隔符（-F相同作用）預設空格
  - RS → 輸入record(列、橫行)分割符，預設換行符
  - NF → 欄位個數
  - NR → record數，就是行號，預設從1開始
  - OFS → 輸出欄位分隔符，預設空格
  - ORS → 輸出resord分割符，預設換行符 
# awk 算術運算子
![image](https://user-images.githubusercontent.com/91866934/148987559-872a0168-f2dc-4846-8808-9530df457d95.png)
# awk 關係運算子
![image](https://user-images.githubusercontent.com/91866934/148987585-6fc1ac67-14d2-4f9c-8cb2-e2421aae60b6.png)
# awk 邏輯運算子
![image](https://user-images.githubusercontent.com/91866934/148987647-b9f3fcf1-9190-4b69-ab6d-84172b090383.png)
# awk 正則運算子
![image](https://user-images.githubusercontent.com/91866934/148987692-67791f09-ed94-4adb-9135-def2a8108f07.png)
# awk 賦值運算子
![image](https://user-images.githubusercontent.com/91866934/148987995-a76fc612-dd91-4b4d-a88e-ba87c13b90e4.png)

# sed 文字分析工具
- 「stream editor 」的縮寫，顧名思義是進行串流 (stream) 的編輯
- 字串取代、複製、刪除的功能
- 自動化的修改文字檔

- Sed指令
  - option：以 - 符號開頭的功能，如 -n、-r、-i，可省略
  - n1,n2：代表開始行數和結尾行數，一個代表指定的這行，不輸入代表每行都會執行command
  - command：進行的動作，如s, a, c, d, i
  - pattern：給command使用的參數
  - replacement：當使用s指令時會使用
  - flag：當使用s指令時會使用
- Sed語法-常用選項
  - option:
    - -n : 沉默模式，只有經過sed處理的那行才會被印出
    - -e : 直接在命令模式編輯，預設
    - -f : 直接將sed動作寫在一個檔案內，-f file會直接執行file裡面的動作
    - -i : 修改檔案
- Sed語法-常用指令
  - command:
    - a : 新增，在下一行插入字串，未指定行數的話，則是在每一行之後插入字串
    - c : 取代，  取代指定行數的內容
    - d : 刪除，後面通常不接任何東西 
    - i : 插入，在指定行數的前一行插入字串
    - p : 印出，只印出受影響的行，常搭配-n使用
    - s : 搜尋、取代，最常用的指令，可搭配正規表達式使用，將搜尋的內容進行取代
- Sed語法-常用旗幟
  - flag:
    - g : 全部取代
    - [0-9] : 每行第幾次出現
    - I : 忽略大小寫
    - w : 把符合的結果寫入檔案
# Grep, Awk, Sed比較
- grep：文字搜尋工具
  - 可用正規表達法，找出匹配的內容
- sed ：是一種線上編輯器
  - 它一次處理一行內容，可搭配正規表達法
  - 主要用來自動編輯一個或多個檔案，簡化對檔案的反覆操作
  - 用於行間的內容操作,如增刪改,查詢替換
- awk：文字分析工具
  - 逐行的讀入，可搭配正規表達法
  - 主要用在對文字和資料進行分析處理，以空格為預設分隔符號
  - 同時也是程式語言
  - 用於處理有欄位規則的行內內容,並支援格式化輸出
# Git-版本控制
- 造成的困擾：
  - 當檔案備份過多時
    - 容易忘記每個檔案做了哪些變動，檔案之間的差異
  - 當多人共同編輯時
    - 在整合檔案或是不同人在進行反覆編輯時，容易導致原本的檔案被覆蓋掉
    - 修改到別人的程式碼
# Git-版本控制的特點
- 版本儲存
  - 儲存檔案的重要資訊，EX：編輯者、時間、版本相關資訊
- 共同編輯
  - 可藉由repository和共同編輯者分享資料，不會因為兩人同時編輯，導致先進行編輯的人的內容被覆蓋掉
- 儲存空間
  - git並不是記錄版本差異，而是記錄檔案內容的快照，使git體積小、速度快
# Git 連結帳號至Github 
- $ git config --global user.name “Your Name”
- $ git config --global user.email “your@gmail.com”
# Git 指令
- 初始化專案：git init
- 單一檔案加入索引(暫存區)：git add <檔案名稱>
- 所有檔案加入索引(暫存區)：git add .
- 觀看當前狀態：git status
- 提交版本：git commit -m “修改紀錄”
- 瀏覽歷史紀錄：git log
- 取消追蹤檔案：git rm –cached <檔案名稱>
- 取消commit：git reset --mixed HEAD^
- 連接遠端數據庫：git remote add origin <remote網址>
- 將本地資料推到remote端：git push -u origin master
- 將遠端資料拉回來：git fetch
- 將拉回的資料和本地資料合併：git merge
- git pull = git fetch + git merge
# Git-使用方法
- 新增Working directory(工作目錄)
  - 建立資料夾(ex：mkdir cs6_git)
  - 移動到資料夾：$ cd cs6_git
  - 將專案資料夾建立成git repository：$ git init (初始化資料夾)
  - 新增檔案(ex：index.html)
  - 查看資料夾內檔案變化：$ git status
- 進入Staging area(暫存區)
  - 將新增或變更的檔案加入追蹤：$ git add index.html
  - 查看資料夾內檔案變化：$ git status
  - 再新增一個檔案(ex：README.md)
  - 查看資料夾內檔案的變化：$ git status
  - 將所有的檔案加入追蹤：$ git add --all
- 進入Local repository(本地數據庫)
  - 將檔案移入本地repo，提交新版本：$ git commit -m “First release of Hello”
  - 使用$ git status觀察：$ git status
  - 查看新增的版本(歷史紀錄)：$ git log
# Git- 取消追蹤檔案
- 檔案從Staging area(暫存區)退回Working directory工作目錄
  - 修改index.html：vi index.html
  - 查看狀態：$ git status
  - 將檔案加入索引：$ git add index.html
  - 查看狀態：$ git status
  - 取消追蹤檔案：$ git rm –cached index.html
  - 查看狀態：$ git status
# Git- 取消commit
- 將commit拆掉
  - 新增檔案：vi hello.py
  - 將檔案加入索引：$ git add .
  - 提交版本：$ git commit -m “print method”
  - 查看歷史紀錄：$ git log
  - 取消commit：$ git reset --mixed HEAD^
  - 查看歷史紀錄：$ git log
  - 查看狀態：$ git status
# Git- Reset模式
- --mixed：預設模式，Commit 拆出來的檔案會留在工作目錄，但不會留在暫存區
- --soft：工作目錄跟暫存區的檔案都不會被丟掉
- --hard：工作目錄以及暫存區的檔案都會丟掉
# Git-使用方法
- 進入Remote repository(遠端數據庫)
  - 雲端跟本地端連動：$ git remote add origin <remote網址>
  - Push Local master(主幹)進入Remote：$ git push --set-upstream origin master
  - 回到Github查看
- Remote repository(遠端數據庫)
  - 到github上新增或編輯README.md
  - 把遠端東西拉回來：$ git fetch
  - 查看狀態：$ git status
  - 查看歷史紀錄：$ git log
  - 比較本地分支和遠端分之內容的不同：$ git diff origin/master
  - 將遠端和本地端的內容做合併：$ git merge origin/master
  - 查看狀態：$ git status
  - Pull下載更新：$ git pull origin
