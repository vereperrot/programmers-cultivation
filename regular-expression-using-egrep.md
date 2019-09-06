# 正規表示法使用egrep指令
## 介紹
egrep用來搜尋檔案內是否包含某字串，本文主要做Windows下面的egrep使用介紹。可以在sourceforge[下載unxutils](https://sourceforge.net/projects/unxutils/)。

## 安裝
安裝UnxUtils，下面的安裝步驟在Windows10專業版中進行
1. 解壓縮UnxUtils.zip。
2. 將資料夾UnxUtils移動到D:\Program Files。
3. 我的電腦圖示按右鍵，選擇屬性，開啟系統視窗。
4. 點擊進階系統設定。
5. 按**環境變數...**按鈕。
6. 編輯Path系統變數，新增D:\Program Files\UnxUtils\usr\local\wbin。
7. 之後在命令提示行中就可下egrep指令。

## 教學

egrep指令格式為Usage: **egrep [OPTION]... PATTERN [FILE] ...**，PATTERN是要輸入正規表示法的地方，**...**表示可以有多個[OPTION]或[FILE]。可以下**egrep --help**取得更詳細的指令說明。

* -n 列出搜尋的字串在檔案的第幾行。
* -c 列出該檔案有幾行匹配。

Windows命令行用空白字元來區隔指令與參數，雙引號的作用是把雙引號內包刮的內容當字串處理，並忽略掉雙引號。

		D:\UnxUtils\usr\local\wbin>egrep -n "gr[ea]y" *.txt
		out.txt:1:grey one
		text.txt:1:grey line

如果雙引號內包刮的內容是變數，則會讀取變數的內容在做處理。

		D:\UnxUtils\usr\local\wbin>set tmp="gr[ea]y"

		D:\UnxUtils\usr\local\wbin>egrep -n "%tmp%" *.txt
		out.txt:1:grey one
		text.txt:1:grey line
    
如果用單引號，單純視為單引號字元。

		D:\UnxUtils\usr\local\wbin>egrep -n 'greyone' *.txt
    
PATTERN 要包含空白字元，如按下面的指令下會有錯誤。它會將'grey視為PATTERN，line'視為FILE。因為Windows命令行用空白字元來區隔指令與參數。
    
    D:\UnxUtils\usr\local\wbin>egrep -n 'grey line' *.txt
    egrep: line': No such file or directory
    
## 參考
- [Mastering Regular Expressions Jeffrey E. F. Friedl - 深入介紹正規表示法的觀念](https://www.amazon.com/Mastering-Regular-Expressions-Jeffrey-Friedl/dp/0596528124)
    - [Jeffrey-Friedl web site](http://regex.info/)

[贊助作者](https://paypal.me/vereperrot/10USD)，感謝支持。
