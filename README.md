# Linux各個目錄存放內容
- /：根目錄，所有檔案皆從根目錄開始，只有root使用者具該目錄的許可權
- /root：該目錄為系統管理員，也稱作超級許可權者的使用者主目錄
- /bin：存放著經常使用的命令
- /boot：系統啟動時必須讀取的檔案, 包括系統核心
- /home：存放普通使用者的家目錄，每個使用者都有自己的家目錄
- /etc：放置與系統設定、管理相關的檔案
- /usr：這是一個非常重要的目錄，使用者的應用程式和檔案都放在這個目錄下，類似與windows下的program files目錄
- /media：可用來做為光碟、軟碟片、隨身碟與其他分割區的自動掛載點
- /tmp：供全部使用者暫時放置檔案的目錄
- /var：系統執行時, 內容經常變動的資料或暫存檔(log file), 都會放置在這個目錄裡

# Linux背景知識-檔案命名原則、副檔名
- 區分英文字元的大小寫，基本以小寫為主
- 檔名長度至多256個字元，可包括字母、數字、"."、"_"和"-"
- 檔名不可使用的字元："?"、"*"、" "、"$"、"&"、"("、"/" 、".."
- .filename，檔名前面有小數點，為隱藏檔

# Linux指令-絕對/相對路徑的移動
- 絕對路徑：路徑的寫法『一定由根目錄 / 寫起』
- 相對路徑：路徑的寫法『不是由 / 寫起』，例如由 /usr/share/doc 要到 /usr/share/man 底下時，寫成： 『cd ../man』，相對路徑意指『相對於目前工作目錄的路徑！』
- 比較特殊的目錄
   - .：代表此層目錄
   - ..：代表上一層目錄
   - ：代表前一個工作目錄
   - ~：代表『目前使用者身分』所在的家目錄

# Linux指令
- cd：變換目錄
- pwd：顯示目前目錄所在位置
- ls：顯示目錄下所有檔案
- touch：建立檔案
- cp：複製
- cat：查看檔案內容
- vi：編輯檔案
- mkdir：建立一個新目錄
- mkdir-p：同時建立多個目錄
- rmdir：刪除一個裡面是空的目錄
- rm：刪除檔案
- rm-r：強制刪除
- mv：移動，重新命名

# Linux背景知識-使用者與群組
- 關於身份：
  - 身份分類：
    - user (owner)		
    - group			
    - others			
  - 群組 (group) 的主要用意：
    - 將帳號歸類，有助於類似專案開發；
    - 每個使用者均可加入多個群組。
- 關於身份類別：
  - 系統管理員： root
  - 一般帳號：
    - 系統帳號 (用於系統帳號的工作)
    - 一般使用者帳號 (用於一般使用者登入用。)

# Linux指令-查看檔案目錄資訊
- ls -l：顯示目錄下的所有檔案詳細資訊
- ls -al：顯示目錄下的所有檔案(包含隱藏檔)詳細資訊
![image](https://user-images.githubusercontent.com/91866934/143665885-d564d3f1-fa5d-4769-a148-e8c5acbc0f8b.png)

# Linux指令-更改檔案或目錄權限
- chown可修改檔案或目錄的擁有者及群組
![image](https://user-images.githubusercontent.com/91866934/143666003-1238b546-9530-4ed5-a148-1b89bb83f581.png)

# Linux指令-更改使用者權限
- chmod可控制檔案如何被他人調用 
&rarr; chmod [-cfvR] [--help] [--version] mode file…
- mode許可權設定字串 
&rarr; [ugoa...][[+-=][rwxX]...][,...]
![image](https://user-images.githubusercontent.com/91866934/143666206-c97c74a1-cf38-48b8-9123-542c55b169b5.png)

# Linux指令-目錄權限
![image](https://user-images.githubusercontent.com/91866934/143666236-880a59b2-51a5-47ff-988b-33ada43cb1b3.png)

# Linux指令-更改使用者權限
- 檔案 file1.txt 設為所有人皆可讀取 :
  - chmod ugo+r file1.txt
  - chmod ugo+r file1.txt
- 將檔案 file1.txt 與 file2.txt 設為該檔案擁有者，與其所屬同一個群體者可寫入，但其他以外的人則不可寫入 :
  - chmod ug+w,o-w file1.txt file2.txt
- 將 ex1.py 設定為只有該檔案擁有者可以執行 :
  - chmod u+x ex1.py
- 將目前目錄下的所有檔案與子目錄皆設為任何人可讀取 :
  - chmod -R a+r *
  - chmod a=rwx file == chmod 777 file
  - chmod ug=rwx,o=x file ==  chmod 771 file

# Linux指令-編輯文檔
- nano
  - Ctrl C：顯示游標所在
  - Ctrl W：查詢命令，按下後會跳轉到末行的反白位置，輸入要查詢的內容在按enter及可。

# Linux指令-編輯文檔
- vi/vim(vim相當於vi的升級版)
  - 一般模式：可使用上下左右進行游標宜動、刪除字元及複製貼上檔案資料。
  - 編輯模式：編輯文字
    - i鍵即可進入編輯模式         
    - Esc鍵退出編輯模式

# Linux指令-編輯文檔
- vi/vim(vim相當於vi的升級版)
  - 命令列模式
![image](https://user-images.githubusercontent.com/91866934/143666460-8fbc54e2-280b-46ae-8f85-a69a04df7ea3.png)

# Linux指令-複製檔案或目錄
- cp：複製檔案或目錄
- 指令：cp  -參數  來源檔案   目標檔案
- 參數：
  - -a：相當於-pdr 的意思
  - -d：若來源檔為連結檔的屬性(link file)，則複製連結檔屬性而非檔案本身
  - -i：如果要複製過去的位置已經有相同檔案，會在覆蓋前詢問是否持續進行
  - -p：將檔案本身屬性(權限、所有者、時間)同時複製過去(一般用於備份居多)
  - -r：針對目錄下檔案做遞歸複製(整個目錄下每一個檔案複製到你想要的位置)
  - -s：複製成符號連結檔(symbolic link)(複製成捷徑檔)

# Linux背景知識-壓縮檔案
- 為什麼要壓縮檔案呢？
1. 備份資料的時候，方便整理。
2. 將檔案變小，節省電腦硬碟的空間。(但圖片、音訊、視訊等多媒體檔案壓縮率低，並不能有效節省空間)
3. 將無數個散亂的檔案打包成一個較小的檔案，亦方便資訊在網路上流通。(可將永久免費版之付費軟體輕鬆分享)
4. 壓縮檔案時，可以視情況進行加密。

# Linux背景知識-各壓縮的差別
- 考慮的因素
  - 壓縮率（compression ratio），能夠將檔案壓到多小。
  - 解壓縮所需的時間，也就是需要的 CPU 計算量。
  - 解壓縮所需的記憶體空間。
  - 相容性（compatibility），即解壓縮程式的普遍性，是不是大部分人都有辦法解壓縮這種格式？

# Linux指令-壓縮檔案
- gzip
  - 壓縮：gzip FileName
- 解壓縮：
  - gunzip FileName.gz
  - gzip -d FileName.gz
- xz
  - 壓縮：xz -z FileName
  - 解壓縮：xz -d FileName.xz
- tar.gz
  - 壓縮：tar -zcvf FileName.tar.gz DirName
  - 解壓縮：tar -zxvf FileName.tar.gz

# Linux指令-檔案搜尋
- find [path] [option] [action] filename
  - option
    - -size EX：找出大於500M的檔案→ -size +500M
    - -name EX：找出為照片的檔案→ -name "*.jpg"
    - -type EX：-type f→ 一般檔案;  -type d→ 一般目錄
    - -user EX：同時找兩個擁有者的檔案→-user user1 -o -user user2
- action -exec
  - ls
  - print
- which filename
  - -a：系統會顯示所有被找到的命令執行檔之完整路徑
  - -n<文件名長度>指定文件名長度，指定的長度必須大於或等於所有文件中最長的文件名。
  - -p<文件名長度>與-n参數相同，但此處的<文件名長度>包括了文件的路徑。
  - -w：指定輸出欄位的寬度。
  - -V：顯示版本訊息。

# Linux指令-檔案內容查閱
- cat  從第一行顯示檔案內容、形成新檔案
  - cat -n file1 > file2→把file1的檔案內容加上行號後輸入file2檔案
    - -n  → 由1開始對所有輸出的行數編號
    - &gt; → 將多個文件覆蓋到目標文件中
    - &gt;&gt; → 將多個文件追加到目標文件中，不覆蓋
- tac  從最後一行開始顯示
  - tac -r -s 'x\|[^x]' test.log→一個接著一個字符的反轉一個文件
    - -r→將分隔符作為基礎正規表達是處理
    - -s→使用String作為分隔符代替默認的換行符
- more 一頁一頁的顯示檔案內容
   - more +20 testfile→從第20行開始顯示testfile的文檔內容
     - ENTER：向下n行(default為1行)
     - Ctrl+F/SPACE：向下滾動一屏
     - Ctrl+B：返回上一屏
- less 與 more 類似，顯示檔案室允許用戶既可以向前又可以向後翻頁閱讀檔案
   - ps -ef |less→ps查看進程信息並通過less分頁顯示	
     - j→下一行
     - k→上一行
     - G→移動到最後一行
     - g→移動到第一行
- head 取出前面幾行(預設10行)
  - -n：後面接數字，代表幾行的意思
- tail 取出後面幾行(預設10行)
  - -n：後面接數字，代表幾行的意思
  - -n +20：只想列出20行以後的資料

# Linux背景知識-資料傳輸
- port
  -通訊埠號是 TCP/UDP 與上層通訊的通道，當 TCP/UDP 要傳送訊息時，會指定要由哪一個通訊埠號來接收。一些常用的服務會使用特定的埠號來等待要求的訊息。埠號是由 16 個位元所組成的號碼，0 ~ 255 為保留號碼，256 ~ 65535 則可自行設定。 
- TCP/IP
  - TCP/IP提供了點對點的連結機制，將資料應該如何封裝、定址、傳輸、路由以及在目的地如何接收，都加以標準化。它將軟體通信過程抽象化為四個抽象層，採取協議堆疊的方式，分別實作出不同通信協定。協定套組下的各種協議，依其功能不同，被分別歸屬到這四個階層之中，常被視為是簡化的七層OSI模型。
- 當瀏覽器輸入網址，發出一個 GET 請求時
1. TCP三向交握
2. 瀏覽器請求、資料傳輸、渲染畫面
3. TCP四次揮手，結束連線

# Linux指令-網路相關
- route
- netstat -r (MAC)
  - add : 新增一條路由規則
  - del : 刪除一條路由規則
  - -net : 目的地址是一個網路
  - -host : 目的地址是一個主機
  - target : 目的網路或主機
  - netmask : 目的地址的網路掩碼
  - gw : 路由資料包通過的閘道器
  - dev : 為路由指定的網路介面
- ping  <dr>  常用網路檢測工具，可藉由發送 ICMP ECHO_REQUEST 封包，檢查自己與特定設備之間的網路是否暢通，並同時測量網路連線的來回通訊延遲時間
  - -n：參數指定封包數
  - -t：持續監看網路是否正常
  - -4/-6：IPv4/IPv6
  - -c：指定Ping次數
  - -s：指定發送的數據字結數
  - -i：指定收發資訊間隔時間
- 影響網路速度的因素：
  - 延遲（Latency）：封包從來源端至目的端中間所花的時間
  - 頻寬（Bandwidth）：傳輸媒介的最大吞吐量
- 網路延遲（Latency）的組成元素:
  - propagation delay：封包在網路線上傳輸所花費的時間，與網路線上電子訊號跑的速度有關，這個時間就是距離除以訊號傳送速度所得到的數值。
  - transmission delay：網路卡將資料傳送到網路線上所花的時間，與網路設備的傳送速度有關。
  - nodal processing delay：路由器處理封包表頭、檢查位元資料錯誤與尋找配送路徑等所花費的時間。
  - queuing delay：路由器因為某些因素無法立刻將封包傳送到網路上，造成封包暫存在佇列中等待的時間。
- netstat
  -查看端口是否被占用：netstat -al grep 3306
  - 查看數據包統計信息：netstat -s
  - 查看路由信息：netstat -r
