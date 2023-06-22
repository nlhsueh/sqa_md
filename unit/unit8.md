# Unit 8 系統測試

張翠山全身發抖，目光中如要噴出火來，指著殷素素道：``你……你騙得我好苦！”俞岱巖突然大叫一聲，身子從床板上躍起，砰的一響，摔了下來，四塊床板一齊壓斷，人卻暈了過去。殷素素拿起佩劍，倒轉劍柄，遞給張翠山，說道：``五哥，你我十年夫妻，蒙你憐愛，情義深重，我今日死而無怨，盼你一劍將我殺了，以全你武當七俠之義。”\footnote{改編自金庸「倚天屠龍記」}

張翠山接過劍來，一劍便要遞出，刺向妻子的胸膛，但霎時之間，十年來妻子對自己溫順體貼、柔情蜜意，種種好處登時都涌上心來，這一劍如何刺得下手？

他呆了一呆，突然大叫一聲，奔出房去。殷素素、宋遠橋等六人不知他要如何，一齊跟出。只見他急奔至廳，向張三豐跪倒在地，...

... 殷素素見丈夫為了自己而自殺身亡，突然間又見兒子無恙歸來，大悲之后，繼以大喜，問道：``孩兒，你沒說你義父的下落么？”無忌昂然道：``他便打死我，我也不說。”殷素素道：``好孩子，讓我抱抱你。”

... 她身子微微一顫，說道：``孩子，你爹爹既然死了，咱們只得把你義父的下落，說給人家聽了。”無忌急道：``不，不能！”殷素素道：“空聞大師，我只說給你一人聽，請你俯耳過來。``這一著大出眾人意料之外，盡感驚詫。空聞道：``善哉，善哉！女施主若能早說片刻，張五俠也不必喪生。”走到殷素素身旁，俯耳過去。殷素素嘴巴動了一會，卻沒發出一點聲音。空聞問道：``甚么？”殷素素道：``那金毛獅王謝遜，他是躲在……”``躲在”兩字之下，聲音又模糊之極，聽不出半點。空聞又問：``甚么？”殷素素道：``便是在那兒，你們少林派自己去找罷。”

空聞大急，道：``我沒聽見啊。”說著站直了身子，伸手搔頭，臉上盡是迷惘之色。

殷素素冷笑道：``我只能說得這般，你到了那邊，自會見到金毛獅王謝遜。”她抱著無忌，低聲道：``孩兒，你長大了之後，有兩件事不能相信，第一：女人的話，要提防女人騙你，越是好看的女人，越會騙人。第二：...。

> {工程師跟你說他測完了，可以上線了。不要相信他，你還要找他人做整體的系統測試

\end{itshape}

\end{comment}

系統測試考慮整體的測試，這時候的測試，著重在系統整體的操作、效能是否正常，符合預期。軟硬體的問題必須同時被考慮。

**System testing}{
A testing conducted on a complete, integrated system to evaluate the system's compliance with its specified requirements.}

## 使用案例測試

%在軟體開發的過程中，最困難的往往不是程式設計與實作的問題，而是需求的問題。如何正確的表達需求，是許多軟體工程急欲解決的問題。使用案例（use case）是一種擷取使用者的需求的方法，廣泛的應用在UML的方法論中。

單一的功能即便設計的再好，如果整體使用起來不正確或不順暢，一樣是不好或錯誤的系統。系統測試中首先我們要測試就是整體操作流程、使用的狀況與情境是否能夠真的幫助使用者達到他的目標; 而這些流程與操狀況應該在規格書中就已經定義好了，系統測試階段我們只是做確認而已。規格階段中我們定義「使用案例」，測試階段我們測試使用案例是否真的被實踐了。



### 使用案例}

#### 使用案例（Use Case）} 任何系統都不會單獨存在，在大部份的情形下，系統是設計來給人用的，而人「使用」的系統的「案例」(或說是情境)，就稱為使用案例。使用案例在整個系統發展中占了極重要的角色，它不僅可以在需求階段幫忙擷取與管理需求，同時也是分析、設計、實作甚至是測試階段的依據。

想像系統是一個黑盒子，外面有一些按鈕，我們並不知到黑盒子裡到底有什麼東西，只是知道按某些順序去按這些按鈕時會得到我們要的功能。就像台鐵的短程票自動購票系統，我們並不知道裡面的邏輯為何，不過我們使用它的情形是如此的：

- 使用者投下硬幣;
- 系統亮起所有可能的燈號，包括站名、火車等級及張數;
- 使用者選擇張數;
- 系統亮起所可能的燈號，包括站名、火車等級;
- 使用者選擇站名;
- 系統亮起所有可能的火車等級;
- 使用者選擇火車等級;
- 系統輸出車票級找零的零錢。


在系統「開發前」，使用案例則是使用者對系統的「期待」，或是「需求」; 在系統測試時，可以作為檢驗系統功能是否正確、使用是否流暢的依據; 在系統「完成後」，使用案例可以作為「使用說明」。上述的流程中單號是使用者對系統的輸入，而雙號都是系統對使用者的輸出，使用案例則在這些交互的溝通中建立。我們並沒有去描述系統內部的演算法，並不是那不重要，而是因為那不是系統需求擷取階段的重點。這個使用案例的描述，系統分析師可以了解使用者的需求，進而依照這個需求逐步的開發系統。

%使用案例不只有單純的文字敘述，相關的觀念還有角色使用者(actor)及使用案例圖(use case diagram)。

#### 使用者(Actor)} 在模組系統的使用案例前，我們必先知道系統的使用者，在UML稱為「Actor」。UML之所以把它稱之為Actor而非「user」的原因是使用系統的「物體」不一定是「人」，它也可能是另一個系統或外在設備。為了方便起見，本書仍將 Actor 譯成使用者。比方我們設計一個公司的薪水管理系統，與這個互動的外在物體除了會計人員以外，銀行系統也是其一。在這種情況下，會計人員與銀行系統都是使用者。另外要特別注意的是使用者是以使用系統的「角色」來定位的，而非個體。例如John在公司中同時是會計人員與公司員工，在薪水管理系統中我們找出的使用者是「會計人員」與「公司員工」兩個使用者，而非John一個人。

一般而言，我們可以將使用者分為三類：

- *主要使用者}(primary actor)：開發系統時很難一次就把所有的actor都找出來，所以通常是循序漸進的。一開始時我們先考慮「系統為何而設計」，「誰是這個系統的主要使用者？」，因此找出系統的主要actor。主actor是系統的直接使用者，也通常是使用最頻繁的使用者。
- *次要使用者}(secondary actor)：當主要使用者一一被指定出來後，另一類重要的使用者也不可以忽略：次要使用者(secondary user)。次要使用者雖然也會與系統作直接的互動，但它的目的是監督與維護系統的正常運作，系統設計的目的並不是給這一類的人使用的。
- *其他系統}：在薪資管理系統中，若我們要將薪資直接匯到某個銀行，對本系統而言，銀行系統並不是我們設計的範圍，但銀行系統卻須使用到本系統的資料輸出，所以銀行系統也是本系統的一個使用者。

建構系統的時候，最初從主要的使用者開始找起，當我們逐步找出系統的主要使用者和它所牽涉的使用案例後，系統類或設備類的使用者就後慢慢的浮現出來。

%在UML中，使用者的表示法如圖3.1：
% 圖3.1　Actor

#### 建立使用者的技巧} 在建立使用者時我們可以考慮以下的問題：

- 哪些人是系統的主要使用者？
- 哪些人可以利用這個系統來協助完成他們的工作？
- 哪些人是系統的次要使用者？例如協助維護此系統與管理此系統？
- 這個系統會和其他的軟硬體互動嗎？

例如在圖書館裡系統中，我們可以找出以下幾個使用者：

- 主要使用者：圖書租借者：查詢書籍資料、預借書籍、取消預借。
- 次要使用者：圖書管理員：負責管理書籍的外借、歸還。
- 其他：與租借者資訊相關的系統，例如學校的學生學籍資料系統。

#### 使用者的一般化關係} 所謂的一般化（generalization），指的是「是一種」（is a kind of）的關係。例如 Manager 是一種 Employee，Engineer 是一種 Employee。將 Manager, Engineer, 與 Technician 歸納為 Employee 的過程稱為一般化，而反方向的，將 Employee 分成 Manager, Engineer, 與 Technician 稱之為「特殊化」(Specialization)。利用一般化關係可以大大的降低使用者方面的模組複雜程度。

%使用案例 (Use Case)

當我們找出系統的使用者後，接下來要思考的就是系統的功能為何？我們可以使用使用案例來幫助分析師擷取系統的功能。使用案例是一段使用者使用系統的完整過程描述。當然，在系統尚未完成前，這樣的過程是分析師與需求提供者「想像」及討論出來的。在描述使用案例時要注意我們是站在使用者的角度來看「系統要作什麼」而非系統「如何」作，也就是說，我們是在站在系統外來看系統的行為（outside view），而非看系統內部行為（inside view）。

使用案例是使用者使用系統的完整流程，但如何去描述這個流程呢？我們建議透過一連串的*事件流}（flow of events）來描述。這些事件流至少必須包括使用案例如何啟動、如何結束、在什麼情況下和使用者互動以及和使用者交換些什麼資料。在媒體管理系統中，我們定義了一個「查詢並預借」的使用案例，它的*基本案例} （basic course）如下：

```
*使用案例：查詢並預借媒體 (故事性的使用案例表達方式)} 

基本案例 Basic Course)\\
當*租借者}點選「查詢並預借」後即進入本使用案例。*系統}顯示可能的查詢方式，例如直接輸入媒體代號、輸入關鍵字、或要求列出所有媒體。*租借者}在要求列出所有媒體後，*系統}列出所有的媒體，包括它的媒體名稱、媒體數量、目前租借狀況等媒體特性，此外，每個媒體旁有一個「預借」的控制鍵。*租借者}在按下預借的控制鍵後，系統檢查使用者可否借此媒體，若可以，則顯現租借成功的訊息。

```

我們特別把使用者和系統標粗顯示，你可以發現使用案例所描述的都是簡單的「使用者要求了什麼，系統回應了什麼」的事件流，而沒有複雜的實作細節。圖 \ref{table:use_case} 的*對話式表達方式}更容易看出使用案例的精神。

\begin{table}[h]
\begin{center}
FIG: 對話式的使用案例}
\begin{tabularx}{.9\columnwidth}{X | *3X }
\hline
使用者動作          & 系統動作                                              \\ \hline \hline
1. 點選「查詢並預借媒體」 & 2. 顯示可能的查詢方式，例如直接輸入媒體代號、輸入關鍵字、或要求列出所有媒體           \\ \hline
3. 要求列出所有媒體    & 4. 系統列出所有媒體，包含媒體名稱、媒體數量、租借狀況等媒體特性。媒體旁有一個「預借」的控制鍵。 \\ \hline
5. 按下預借的控制鍵,   & 6. 系統檢查使用者可否借此媒體，若可以，則顯現租借成功的訊息。                  \\ \hline
\end{tabularx}
\label{table:use_case}

\end{table}

\begin{figure}[h]
\begin{center}
\includegraphics[width=.8\columnwidth]{./SQA/use_case_test.png}
FIG: 使用案例測試}
\label{fig:use_case_test}

<img src="" width="500">

#### 替代案例} 圖 \ref{fig:use_case_test} 步驟 6 中描述使用者可以成功的租借此媒體的最基本案例，而不去考慮其他的案例或是租借失敗的處理方式，這是希望使用案例在建構時能*按部就班}的來：「先考慮成功個案，再考慮其他可能案例與失敗案例的情形與處理方式」。一個使用案例除了一個一般狀況外，還可能有數個替代情境(alternative course)。以下就是一個例外狀況的描述：


- *書已外借}。當使用者按下預借的控制鍵後，系統檢查並發現該媒體已外借或預借。若已外借，則使用者的預借排在上一個預借者的後面。
- *原租借者再預借}。欲租借者預借之媒體若為本身目前所租借，則系統檢查是否有人預借，若有則不得預借；若無，則雖可預借，但若他人將來預借時，本身的預借取消。

%建立使用案例的技巧
%1.	利用劇本和使用者溝通以確定功能是否正確。
%2.	針對一個較複雜的劇本仔細的討論以了解使用者對系統的使用習慣與要求。
%3.	當使用者對畫面的要求很重視時，或不是很了解他要的畫面呈現為何時，可以做一些假想畫面來輔助需求的擷取。

> {描述情境就像是述說故事一樣。一個好的系統需要一個好的故事。

#### 使用案例測試} 依據使用案例所描述的情境來進行測試

- 找出使用案例，包含基本案例與替代路徑; 
- 建立可以完成基本案例的環境與資料，進行測試; 
- 選擇一個替代案例，建立可以執行的環境與資料，進行測試;
- 重複執行以上步驟，以加強涵蓋度。


以圖 \ref{fig:use_case_test} 為例，我們可能建立以下的測試腳本：

- basic flow ($BF$); 
- $BF$, Alternative Flow ($AF_1$);
- $BF$, $AF_1$, $AF_2$;
- $BF$, $AF_3$;
- $BF$, $AF_3$, $AF_1$, $AF_2$;
- $BF$, $AF_3$, $AF_4$.

\ifWide \clearpage \fi
%```
%「KK 商場」是國內數一數二的電子商務平台，會員可以在商場內進行上架、買賣與退貨等服務。請針對「物品購買」設計使用案例，並列出可能的替代案例，並規劃其測試案例。
%```

:question: 隨著自動駕駛的技術成熟，以後自用車也可以很方便租用出去給他人使用。請規劃一些未來的用車情境（使用案例），包含 actor, use case, basic flow, alternative flow。}

## 可用性測試}

拿出你的 iphone 手機，操作 77-38.5, 看看答案是多少？疑，是 0? 你能說明為什麼嗎？


### Neilsen 檢測法}

Neilsen 檢驗法是一種專家檢驗法，包含以下的檢測項目：與真實世界的對應、使用者擁有控制權
一致的風格、錯誤預防、易於識別、優雅簡潔的設計、清楚的錯誤處理、適當的說明文件、清楚的系統狀態、適當的說明文件等。


- *清楚的系統狀態} Visibility of System Status: 透過在合理時間內的合適回饋，系統應該讓用戶了解目前的狀態。例如我們在下載一個大檔案，呈現一個「進度狀態」不斷的更新目前下載的比例可以讓使用者的確定目前系統是正常的、網路是流暢的。上述 iphone 77-38.5 並沒有錯誤，答案的確也是 38.5，但因為出現答案的 38.5 並沒有閃一下\footnote{這個問題約在2015 年已改善}，很容易讓使用者誤以為沒有按好 =，於是再按一次，就會出現 0。這也是一個介面設計上的問題。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.6\columnwidth]{./SystemTest/progress.png}

<img src="" width="500">

- *與真實世界的對應} Match Between System and the Real World: 該系統應該以使用者熟悉的語言、文字、詞彙與概念來呈現，而不是使用系統導向。工作導向。
%	 
%	- 用該*工作領域的慣用語}，而非技術導向的。用使用者習慣的用語。例如「購物車」	就是在電子商務中很習慣的用語。
%	- *一致性的}。不要用不同的名詞來指相同的事物或觀念。例如光是一個產品就有產品編碼、產品編號、產品 ID、產品識別碼、Product UID…，會讓使用者非常的困擾。
%	- 從*使用者}的角度：“您已購買了…” 比 “我已經賣給你…” 好
%	- *全名}比縮寫好
%
- *使用者擁有控制權} User Control and Freedom: 讓使用者有操作的控制權，而不是受制於系統。使用者時常以嘗試的心態來操作系統功能，他們需要一個明顯的「回復 undo」或「離開系統」來離開使用者不需要的狀態，這樣他才能無拘無束的程式這個系統，如果擔心按錯不能回復，使用者就會放棄該系統。

又例如瀏覽網頁，我們常常逛著逛著就進入很深的頁面，不知道如何回到之前的某個頁面。如果這時候有一個結構能夠清楚的指出你在這個網頁系統的哪個位置、如何快速的到其他頁面，系統使用起來就會方便很多-- 你擁有瀏覽的自由度。

%\begin{figure}[h!]
%\begin{center}
%\includegraphics[width=.6\columnwidth]{./SystemTest/consistentStyle.png}
%FIG: 一致風格}
%\label{fig:consistentUI}
%
%<img src="" width="500">


- *一致的風格} Consistency and Standards: 系統畫面、操作習慣應一致，使用者不應該猜測同一種動作是否使用不同的字彙、狀態或動作。

例如「Help」都在一個固定的位置、有固定意義的快速鍵、操作流程等。每個不同的平台也有其設計的標準，例如 iOS 與 Google Android 都有其介面設計規範，符合這些設計規範讓會讓使用者更快上手。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.6\columnwidth]{./SystemTest/consistentStyle.png}
%FIG: 一致風格}
%\label{fig:consistentUI}

<img src="" width="500">

- *錯誤預防} Error Prevention: 這是比錯誤訊息還要親切的設計，「預防」是發生問題最先要考慮的事情。不管是移除容易出錯的的條件，或是讓使用者確認他們接下來要做的行動皆是。

例如使用者要把一整個系統目錄刪除，你應該警告他後果。計劃書送出就不能悔改了，你要提示使用者這個訊息，請他再確認。白話一點就是「防呆」的設計。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.6\columnwidth]{./SystemTest/forceClose.png}
%FIG: 錯誤預防}
%\label{fig:error_prevent}

<img src="" width="500">

- *易於識別} Recognition Rather Than Recall: 盡量減少使用者需要記憶的事情、行動以及可見的選項。使用者不應該記憶太多步驟。系統使用說明應該在適合的地方表現的顯眼且可輕易使用。

最常見莫過於 icon 了，例如一把剪刀代表要把文字或物件剪下，這幾乎是系統的全球共識，即便在於多國語言也知道該功能的含意。又例如我們在訂票系統中用位置圖呈現你想購買的位置（而非座位10-20的文字表達）並用顏色呈現已售出的位置，都可以讓使用者易於識別。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.6\columnwidth]{./SystemTest/recognition.png}

<img src="" width="500">

- *有彈性及有效率的使用} Flexibility and Efficiency of Use: 應該有彈性讓「初用者」和「慣用者」都能方便使用。例如慣用者可以使用「快捷鍵」來提昇他們的使用速度; 允許使用者設定常做的動作; 畫面可以延伸等。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.6\columnwidth]{./SystemTest/shortCut.png}

<img src="" width="500">

例如一個計算機，多半的時候我們拿來坐簡單的加減乘除計算，少數的時候才會用的科學計算，在設計上我們預設呈現的簡易版的計算機，並提供按鍵讓他可以延伸為科學計算機，這就是設計上的彈性。

- *優雅簡潔的設計} Aesthetic and Minimalist Design: 對話框不應該包含無關緊要或很少用到的訊息。對話框的每一個額外的部份都會相對地降低主要資訊的顯眼程度。

- *清楚的錯誤處理} Help Users Recognize, Diagnose, and Recover from Errors: 錯誤訊息應該以敘述文字呈現，而不是錯誤代碼，並且精確地指出問題以及提出建設性的解決方案。

要避免把系統內部的錯誤訊息呈現給使用者看，雖然那對開發者除錯有幫助。使用者要知道的是「發生了什麼事」？我哪裡做錯了？能補救嗎？怎麼做？現在網頁系統的使用者註冊常常要使用者輸入一大堆的資料：姓名、住址、帳號、密碼、興趣等等，每一個都有其限制，例如帳號必須是 email, 密碼必須英文數字都有且最少八碼，當使用者不滿足這樣的限制時，你不能告訴他「資料錯誤，請重新輸入」，你要明確的告訴他：「你的密碼設定錯誤」。

- *適當的說明文件} Help and Documentation: 即使是最好的系統也不能沒有說明文件，系統也需要提供幫助與說明文件。說明的資訊應該很容易被找到。


> {不懂電腦的人，往往是最好的測試者。

\ifWide \clearpage \fi

:question: 在前述的自動駕駛例子中，我們需要一個網頁系統來提供預約汽車的功能，請設計此系統畫面，描述其互動，並檢驗是否通過 Neilsen 的檢驗項目。}

:question: 針對一個你常用的應用軟體（ 例如 line 或 選課系統），以 Neilsen 的方式檢視其符合程度：該軟體有哪些優缺點？該如何改善？}

### Hollway 檢測法}
就像是「在走道上隨意的找一個人來操作系統，觀察它的使用狀況」。這樣的目的是避掉在這個專案的相關人員-- 包含分析師、設計師、開發程式設計師、協助訪談的顧客、伴隨的測試人員等 -- 他們因為了解系統反而被「洗腦」了，把許多不便的設計給忽略了。


### A/B 檢測法}
對於一個使用設計（例如位置、色彩）採用AB兩種作法，觀察及分析其使用的狀況，選擇比較好的設計方法。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./SystemTest/ABTest.png}
FIG: AB Test}
\label{fig:ABTest}

<img src="" width="500">

## 效能測試}

\begin{figure}[t]
\begin{center}
\includegraphics[width=.8\columnwidth]{./SystemTest/workload.png}
FIG: 效能測試的三大因子}
\label{fig:workload}

<img src="" width="500">

### 種類與基本概念}

一般而言效能測試（performance testing）可以分為負載測試（load testing）與壓力測試（stress testing）。前者在於測試系統是否能夠承受特定的負載，例如說是100,000 同時上線，這個工作量是取決於該應用系統的特性。例如預估一個購物網站的使用人數。後者是測試系統的極限，看看系統到什麼階段後承受不住，開始發生回應遲緩或是系統當機的狀況。

%Normally I find quite a bit of ambiguity when people talk about performance tests, some restrict it to response time whereas some use it to cover a gamut of things they are testing or measuring. In this post, I will put across few thoughts on contrasting between them. Ideally a lot depends on what you are trying to measure. The terms that you will frequently hear in this arena are – Response Time, Latency, Throughput, Load, Scalability, Stress, Robustness, etc. I will try explaining these terms below also throwing some light on how can you measure them.

一些在效能測試常遇到的名詞：
 
- *回應時間（Response time）}。系統處理一個請求（request）所需要的時間。回應時間對大多數的系統都非常重要，例如電子商務系統，根據統計使用者能夠忍受的時間大約是8 秒鐘，超過這個時間，使用者離開系統或是放棄購買的比例大幅度的提升。
%Response Time – Amount of time system takes to process a request after it has received one. For instance you have API and you want to find how much time that API takes to execute once invoked, you are in fact measuring response time. So how do we measure them? Simple use a StopWatch (System.Diagnostics) – start it before calling API & stop it after API returns. The duration arrived here is quite small so a preferred practice is to call that API in sequential loops say 1000 times, or pass variable load to the API if possible (input/output varies from KBs/MBs/GBs e.g. returning customer array of varied lengths).

-  *網路延遲（Latency）}。當我們送出一個請求，除了伺服器處理的時間以外，還有網路傳送的時間，當你的網路狀況不好時系統的使用是很不方便的，但卻不能怪罪系統的演算法或是架構，必須從網路的架構來改善，或是建立一些代理伺服器來解決這些問題。
%Latency – In simplest terms this is Remote Response time. For instance, you want to invoke a web service or access a web page. Apart from the processing time that is needed on the server to process your request, there is a delay involved for your request to reach to server. While referring to Latency, it’s that delay we are talking about. This becomes a big issue for a remote data center which is hosting your service/page. Imagine your data center in US, and accessing it from India. If ignored, latency can trigger your SLA’s. Though it’s quite difficult to improve latency it’s important to measure it. How we measure Latency? There are some network simulation tools out there that can help you – one such tool can be found here.

- *吞吐量（Throughput）}。表示你應用程式每秒可以處理的交易量。吞吐量也可以說是工作量（workload），表示你的系統可以處理多少的請求而不發生錯誤。
%Throughput – transactions per second your application can handle (motivation / result of load testing). A typical enterprise application will have lots of users performing lots of different transactions. You should ensure that your application meets the required capacity of enterprise before it hits production. Load testing is the solution for that. Strategy here is to pick up a mix of transactions (frequent, critical, and intensive) and see how many pass successfully in an acceptable time frame governed by your SLAs. How to measure it? You normally require a high end professional tool here like Visual Studio Team System (Load Testing feature). Of course, you can try to simulate load through your custom made applications /code but my experience says custom code are good to test for response times; whereas writing custom code for load testing is too much of work. A good load testing tool like VSTS allows you to pick a mix of transactions, simulate network latency, incorporate user think times, test iterations, etc. I would also strongly recommend this testing to be as close as possible to real world with live data.

- *延展性 Scalability}。當系統效能發生問題時，我們通常會升級我們的機器設備，延展性考慮的就是升級或增加硬體時系統的反應。要注意並不是加硬體就能解決問題，例如瓶頸在資料庫，你多了一個硬體加裝資料庫卻會造成兩個資料庫的不一致，這時候系統是延展不開的。延展性可以分為垂直延展（vertically up）或水平延展（horizontally out），前者表示採用較好的機器（better machine），後者表示更多的機器（more machines），例如我們增加機器後在前面增加網路負載平衡器（network load balance; NLB）。

%Scalability – is the measure of how your system responds when additional hardware is added. Does it take new increased load by making use of added resources? This becomes quite important while taking into consideration the growth projections for your application in future. Here we have two options – scale vertically/up (better machine) or horizontally/out (more machines), latter is usually more preferred one. A challenge to scale out is to ensure that your design doesn’t have any server affinity, so that a Load balancer can adjust load across servers. Measuring scalability can be done with help of load balancing tools with a software/hardware NLB in place ensuring system is able to take on new load without any issues. One can monitor performance counters to see whether actual request load has been balanced/shared across servers (I plan to cover NLB in a future post).

%Stress testing – Many people confuse this or relate it to load testing. My take which I have found easy to explain is, if you find yourself running tests for more than 24 hours you are doing a stress test (precise would be your production time i.e. duration before you take your machine offline for a patch, etc.). Motivation behind stress test is to find out how easily your system can recover from over loaded (stressed) conditions. Does it limp back to normalcy or gives up completely? Robustness an attribute that is measured as part of stress testing relates to long running systems with almost negligible down time. A simple example here could be memory leak. Does your system release memory after working at peak loads? Another, what happens if a disk fails due to constant heavy I/O load? Does your system lose data? Finding and addressing such concerns is motivation behind stress testing.


\ifWide \clearpage \fi
#### 效能測試並不便宜}

- 工具不便宜;
- 準備資料是花時間的;
- 設定基礎建設（或測試環境）是花時間的，例如你的系統系統是建置在大型主機，你可能很難有經費在買一台一樣的機器來做為測試;
- 執行測試的時候，需要暫停其他資源的使用;
- 需要其他技術人員，例如資料庫管理師、網管人員、程式人員、測試人員等都需要一起參與。

\ifWide \clearpage \fi
#### 效能測試也不容易}

- 軟體必須是最後版本。如果不是那測試就會失準，小小的程式碼修改可能會影響很大效能。
- 模擬是不容易的。除了預估工作量以外，我們也需要預估使用者的操作行為，例如在線上考試系統，測驗題的思考時間應該考慮進去，才能做精準的預估。也要考慮哪些需要模擬，哪些不用？例如檔案的上下傳需不需要？他所考驗的是系統效能還是網路頻寬？
- 分析是不容易的。當系統效能出現問題時，我們如何知道瓶頸在哪裡？記憶體？CPU？網路？或甚至於是測試軟體本身的問題。
- 如何溝通。如何管理者報告測試的結果？說服他們買機器？如何說服程式工程師改程式？

#### When to do performance test?} 什麼時候應該開始進行壓力測試呢？雖然壓力測試是系統測試的一環，但也應該盡可能的提早開始進行。如果在開發階段我們就發現模組的問題就可以提早改善（如果效能瓶頸在某個模組）。另一方面，壓力測試所需要的環境準備與技術的學習都是很繁瑣的。當系統無法通過壓力測試時我會進行系統的調教，再重新測試，所以他會重複地進行。當然前提是硬體環境已經準備好安裝好，網路及其他的環境也都可以運作，應用程式的功能也已經開發完成，安裝完成且可以運作。

### 度量}

以下列出一些常用度量：

每小時的數量：

- 每小時平均的 session 數量
- 每小時最大的 session 數量
- 每小時平均的 page 觀看數量
- 每小時處理的 byte 數量

每 session：

- 平均（最大） session 長度
- 平均（最大）每個 session 瀏覽的 page 數量

每個 page 平均的停留時間。

每個請求平均的等待時間。

比值（ratio）

- 新用戶與回頭用戶的比值（new users vs. returning users）
- 不同類型使用者的比值。

最

- 最長被拜訪的網頁（page）
- 每小時最尖峰的數量為何
- 每單位時間最多同時上線的數量

### 虛擬使用者}

透過負載產生器（load generator）來產生負載，進行測試。

\begin{figure}[h]
\begin{center}
\includegraphics[width=.85\columnwidth]{./SystemTest/performanceTesting.png}
FIG: 使用虛擬使用者進行壓力測試}
\label{fig:virtualUsers}

<img src="" width="500">

\begin{figure}[h]
\begin{center}
\includegraphics[width=.85\columnwidth]{./SystemTest/loadGenerator.png}
FIG: 多台的負載產生器}
\label{fig:loadGenerator}

<img src="" width="500">


\begin{figure}[h]
\begin{center}
\includegraphics[width=.85\columnwidth]{./SystemTest/performanceTestingProcess.png}
FIG: Record and replay}
\label{fig:virtualUsers}

<img src="" width="500">

效能測試可以分為三個階段實施：規劃階段、測試階段與分析階段。

### 規劃階段}

在規劃階段主要有以下的任務

- 定義測試的目標。大家對測試的期望是什麼，是在現有環境下了解可以的負載，還是滿足某個負載所需要的環境？還是了解超過負荷下系統的表現？
- 收集測試需求。需要什麼環境與設備？依據市場需求或是過去的經驗推估工作流量與反應時間; 
- 需要的產出物與交付物; 
- 決定要執行哪些測試，決定測試日期;
- 決定工作流量（workload）;
- 決定要收集與分析哪些效能度量？例如回應時間、單位時間的處理量等。
- 決定要用哪個工具來模擬流量; 
- 撰寫測試計畫，設計使用者情境與建立測試腳本。

#### 使用輪廓（Usage Profile）} 工作流量要設為多少？通常需要做一些預估與分析，例如在一個教學管理平台，我們要先預估在一般情況下會有哪些主要的使用情境，這些使用情境所佔的比率又是多少？

```java
= 使用輪廓 =
老師：上傳檔案，5%
老師：瀏覽及回覆討論區，5%
學生：下載檔案，10%
學生：參與考試，10%
學生：瀏覽及回覆討論區，70%
```

為什麼我們會知道這樣的輪廓？可能依據過去的系統的紀錄、可能依據推測。一個教學管理平台非常的複雜，可以操作的情境可以上百個，但我們不太需要每一個都列出來，僅列出重要、有代表性的即可。例如瀏覽及回覆討論區和瀏覽成績、瀏覽近期活動所能帶來的流量差異不大，所以我們可以一個情境來代替。檔案的上傳與下載可能造成較大的網路流量，所以獨立出來測試。參與考試由於過程中會不斷的寫資料庫，可能造成資料庫忙碌，故測試之。

> {預測或分析系統的使用輪廓（Usage Profile），再依據使用輪廓來設計效能測試時的工作流量（Workload）。

工作流量可以由兩個方面來計算，其一是使用者角度（user-specific），其二是應用程式角度（application-specific）。前者從多少使用者上線、他們的操作行為來定義流量，後者則從技術的角度，例如多少個點擊、多少的運輸量（byte）來定義流量。

工作流量有以下的計算方式：

%https://www.nosegraze.com/sessions-users-pageviews/

- *拜訪（Visits）} 不同的使用者在一段期間進入該系統的次數。拜訪代表的是「個別拜訪（individual visit）」，同一個人在這段時間內進入多次只能算
一次拜訪。越多的獨立拜訪表示越多的顧客光顧，對於電子商務也特別的意義。

- *會話（Session）} 相較於 Visit代表多少「人」瀏覽網站，Session 代表多少「人次」。Session 的數目表示使用者使用系統的功能的次數。一個使用者進入系統後，通常會瀏覽幾個頁面來達成他所想要的目的，如果他靜止過久（通常是 30 分鐘），我們就認為是另一個 Session。

%和拜訪很類似，Session 比較偏向技術名詞。當瀏覽器連接到伺服器後後，伺服器會給瀏覽器一個 session ID，以記錄使用這的狀態\footnote{HTTP 是屬於非狀態 stateless 的運作方式。}，少了這個 session ID，我們瀏覽網站時就會不斷的詢問你的帳號密碼，太不方便了。當你一段時間不使用該網頁，伺服器便會把這個 session ID 拋棄，你就需要再重新登入了。

- *頁面瀏覽（Page views）} 通常使用者進入一個系統（開始了一個 Session），會有多次的頁面瀏覽來滿足他的需求。例如經歷登入頁、商品瀏覽頁、訂單頁、信用卡填寫頁、確定送出頁等。平均瀏覽頁對電子商務是有意義的，可以使用者對系統的興趣程度，對於我們進行壓力測試規劃也有幫助，我們才知道給系統多少的「工作量」。Page views 通常也稱為網頁請求（request）。

- *點擊（Hits）}一個網頁瀏覽會引發多個「點擊 Hit」，包含文字、圖片、JavaScrip、CSS 等檔案。



:question: 
KK 網路商城開幕第一個月內湧入五萬個不同的人拜訪，其中八成的人註冊進入成為會員。非會員該月僅有一次拜訪，且僅拜訪首頁，而每名會員該月平均拜訪三次，其中四成有購物行為。有購物行為的每次拜訪約需 10 個頁面瀏覽，無購物行為則 3 個頁面瀏覽。\\
問：本月有多少 Visit, Session, Page view?}

%visit = 50,000
%session= 50,000 * 0.2 + 50,000 * 0.8 * 3 = 10,000 + 120,000 = 130,000
%page view = 10,000*1  + 40,000 * 0.4*10 + 40,000*0.6*3 = 10,000+16,000+72,000=98,000 page views


\ifWide \clearpage \fi

%如果你的應用程式是無狀態的（Stateless），就像 HTTP 一樣，這表示你的伺服器不會儲存太多使用者的資料、佔用太多的記憶體空間。所以你有興趣的是尖峰時段的每秒有多少的點擊、觀看等問題。

%如果你的應用程式是有狀態的（stateful），或是某些背景作業會因為新的 session 而啟動，那麼你關注的可能是系統可以有多少的「同時使用者」（concurrent users）。


\ifWide \clearpage \fi
:question: 
KK商場是國內數一數二的電子商務平台，會員可以在商場內進行上架、買賣與退貨等服務。考量到可能的效能問題，預計進行效能測試，請規劃使用輪廓，並依據輪廓規劃工作流量。
}

\ifWide \clearpage \fi

#### 如何產生工作流量} 

- *硬體密集 Hardware intensive} 我們可以透過硬體的產生這些工作流量，但這樣花費的成本太高了，除了軟硬體以外，還需要很多的操作人員。對於大規模的壓力測試而言，這樣的方法是不實用的。
- *軟體密集 Software intensive} 用軟體來模擬大量的工作流量是比較常見的方法，軟體工具模擬不同的 protocol 所發送與接受的封包。即使是一個人也可以產生數百數千的模擬工作量，有極大的方便度與彈性。

#### 工具的選擇} 是否能夠模擬使用者的行為; 是否提供腳本的錄製; 是否提供使用者思考的時間，是否提供HTTPS, AJAX, Cookies 等功能; 是否提供驗證的功能; 是否可模擬不同的瀏覽器; 是否提供各種不同的報表功能，包含統計分析圖表等; 是否與伺服器的監控器做整合。

#### 購買或自建？} 商用軟體可能很昂貴，學習也是一個很大的問題，也可能不符合你的需求。如果是自己來開發，成本通常也不低（需要開發成本），好處是可以貼近你的需求。不論是購買或自建，都應該儘早進行。

另外的一個選擇是透過「應用服務提供商」（Application Service Provider）來產生流量。由ASP來提供流量的好處是不需要花費很多的資源來模擬流量，那是需要軟硬體的建置購買成本的（只為了很久才一次的壓力測試是不划算的）。ASP 還可以在全球設定不同的地方，不同的網路環境速度，也大大的提升模擬的真實性。


### 測試階段}

測試階段就是依據規劃階段的規劃來進行測試資料與腳本的準備，把規劃階段裡面所設計的工作量轉換為工具內的參數，然後進行測試。

這個階段最重要的這是對於工具的熟悉。為了要讓測試腳本有效地被利用，我們甚至要應用程式撰寫的觀念來撰寫測試腳本，例如 JMeter 就有提供 regular expression 的方式來截取回應資料的部分內容，例如 session 的 ID 等等。

上線時間（ramp up）與下線時間（cool down）在這個階段必須被設定。所謂的啟動時間就是所有的工作量完全啟動所需要的時間。例如我們模擬一分鐘內一千個使用者上線，執行若干個功能後在兩分鐘內陸續離開，這一分鐘就稱為上線時間，兩分鐘就成為下線時間。

測試的執行可能需要很多次。

%Setting up the test suite parameter
%Number of threads and socket used to simulate users
%Test-run schedule and duration
%Demographic and geographic segmentation of simulated users
%Request delay factors
%Ramp up speed
%Cool down speed
%Server metric to collect
%Load target such as failed transaction threshold, response time threshold, and so on 


### 分析階段}

這個階段主要：（1）分析結果；（2）改變系統（包含硬體環境、軟體程式等）來改善效能；（3）設計測試，重新測試。

分析效能不是一件容易的事，必須對系統、網路、程式、環境都有一定的技術知識。也必須知道哪些因素可能會影響測試的結果，必要的時候必須反覆的測試來確認你的懷疑（是記憶體不足的問題嗎？）。


回應時間圖（Response Time Graph）是最常見的圖表，反應出不同工作量時的反應時間。當回應時間明顯變長，達到我們所無法接受的點時，該工作量稱為飽和點（saturation point），圖 \ref{fig:responseTimeGraph} 450 人即為該系統的飽和點。

\ifWide \clearpage \fi

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./SystemTest/responseTimeGraph.png}
FIG: Response Time Graph}
\label{fig:responseTimeGraph}

<img src="" width="500">

圖 \ref{fig:cpuGraph} 除了呈現回應時間外，亦呈現 CPU 的使用率。可以看得出，當回應時間加大時，CPU 的使用率也急遽的加大，達到80%的使用率，增加 CPU 的工作效能或許是解決問的方法之一。

\ifWide \clearpage \fi

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./SystemTest/CPUUtilization.png}
FIG: R/T vs. CPU Utilization}
\label{fig:cpuGraph}

<img src="" width="500">

一般而言需要進行多次測試，確保系統測試的結論不是偶然的，在統計上有一定的正確性。圖 \ref{fig:report95} 是針對某一個頁面進行五次的測試，一般而言，若超過 1/5 差異很大，則代表系統環境或程式是有問題的，應在檢驗。若某次測試的 95 percentile value 超過其他測試的最大或做小，表示其差異是大的。

\ifWide \clearpage \fi

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./SystemTest/report95.png}
FIG: Response Time Graph}
\label{fig:report95}

<img src="" width="500">


參考資料：\href{https://msdn.microsoft.com/en-us/library/bb924371(d=printer).aspx}{Performance Testing Guidance for Web Applications}

```
$\omega$ 系統將從 B 系統更換為 M 系統，為了確保系統效能正常，將進行效能測試。如果你是負責此系統的專案經理，專案計畫應該注意什麼？
%該如何進行效能測試？(1) 時程與工作項目該如何分配？(2) 人員與設備該注意什麼？(3) 該如何進行效能測試？是否有工具可以協助？
```


## JMeter 壓力測試 (lab)}

### 安裝}
為了要完成這個練習，我們先利用 Tomcat 來架設一個網站，Tomcat 是用 Java 所開發的一個網頁伺服器，其安裝流程如下：

- 安裝 \href{http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html}{Java JDK}。

- 下載 \href{http://tomcat.apache.org/}{Tomcat}。

- 設定環境變數 JAVA\_HOME 與 CLASSPATH與 TOMCAT\_HOME。

- 啟動 Tomcat，執行 startup.bat。\href{http://localhost:8080}{http://localhost:8080} 檢驗看看是否正確。

- 執行 /examples/jsp/num/numguess.jsp，看看是否正常。


%Count, GuessGame 及一些細部的講義等都放在 \href{https://sky.fcu.edu.tw/navigate/s/1254DCEF73A64742A033798C6E76C68FXSY}{\underline{nlh JMeter}} 中，請先下載。Tomcat 伺服器安裝完成啟動後，接著安裝 JMeter 壓力測試工具，其安裝非常簡單：

安裝 JMeter：

- 下載 \href{http://jmeter.apache.org/}{JMeter} 及解壓縮。
- 啟動。執行 bin 下的 ApacheJMeter.jar。


\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./JMeter/jmeter04.png}
FIG: JMeter 元件}
\label{fig:jmeter_menu}

<img src="" width="500">

Figure \ref{fig:jmeter_menu}中呈現JMeter 最主要的元件，包含


- 「執行緒 Thread」：表示模擬的人數，如果你要模擬100 人同時使用系統，thread 就設為 100。
- 「取樣 >> HTTP 要求」：模擬 HTTP 的請求訊息，也就是瀏覽網頁的模擬。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./JMeter/jmeter03.png}
FIG: JMeter HTTP request}
\label{fig:jmeter_http}

<img src="" width="500">

- 「設定元素 >> HTTP 要求預設值」。上述的 HTTP 要求會反覆的設定很多的要求，例如 IP, Port 等，可以透過 HTTP 要求預設值一次設定，就不需要設定那麼多次。
- 「接聽 >> 彙整報告」。用來呈現測試後的數據與其分析。

有了這些我們觀念，我們就可以做簡單的測試。

### 虛擬使用者}

\href{https://youtu.be/9Qw0i9fan5w}{JMeter part 1 影片解說}

```
*Lab: HTTP 請求。} numguess 為一個簡易的猜數字程式。請利用 JMeter 設計一個測試案例模擬一個使用者進入 numberguess 程式的行為。
```

執行步驟：


- 測試計畫按右鍵 >> 新增 >> Threads (users) >> 執行緒群組
- 設定 執行緒群組 的屬性
	
	- 執行緒數量：模擬多少使用者同時進入測試。現階段請設定一人。
	- 啟動延遲：幾秒內使用者完全進入系統。如果 100 人 10 秒，則平均一秒有 10 人進入。現階段請設定一秒。
	- 迴圈測試：反覆測試幾次。
	- 新增 取樣 >> HTTP 要求（圖 \ref{fig:number_guess01}）。
- 新增 接聽 >> 檢視結果樹。
- 執行。


\begin{figure}[h!]
\begin{center}
\includegraphics[width=.7\columnwidth]{./JMeter/NumberGuess01.png}
FIG: 建立一個 HTTP request}
\label{fig:number_guess01}

<img src="" width="500">


\ifWide \clearpage \fi

```
*Lab: 資料驗證}。承上例，已知最後的數字落在 0-100 之間，若我們輸入 -100 系統會出現 higher 的內容; 若輸入 200 會輸出 lower 的內容。請設計測試案例確定系統具備這樣的行為。
```


- 先在網頁上按右鍵 >> 觀看程式碼，找出輸入值的變數名稱。此範例為 guess。
- 修改剛剛的 HTTP request 為一個 post 訊息，加上參數 guess = 200。
- 在 HTML 請求下方加上一個「驗證回覆」，「測試用樣式」加上 lower 的字串。表示回傳的內容中，應該包含 lower。
- 重複上述步驟，檢測 guess = -100 的情況。
- 執行，接著觀察「檢視結果樹」。你也可以故意把 lower 和 higher 對調，看看「檢視結果樹」會有什麼呈現。
- 使用「接聽>>驗證結果」，觀察測試結果。
- 你可以在 HTTP 請求前加上 「HTTP 要求預設值」，讓建立測試案例 時更容易且更有修改彈性。
- 再加上「接聽 >> 檢視表格結果」，練習運用其他格式的結果。


\begin{figure}[h!]
\begin{center}
\includegraphics[width=.7\columnwidth]{./JMeter/NumberGuess02.png}
FIG: HTTP Post}
\label{fig:number_guess02}

<img src="" width="500">

\ifWide \clearpage \fi


```
*Lab: 邏輯控制器}。承上例，應用邏輯控制器（if/while/loop）來設計一組測試案例，猜數字直到猜對為止。
```

\ifWide \clearpage \fi


```
*Lab: 壓力測試。}承上例，將執行緒改為 10 執行測試並觀察回應時間。逐步增加壓力比較系統的回應時間。
```


- 新增 「Summary report」接聽器。

由 Summary report 中可以看到回應的時間，其中取樣數表示測試的次數，平均、最小、最大分別表示回應的平均、最小與最大的毫秒數。如果太大超過系統能夠回覆的時間，錯誤率就會大於 0, 表示伺服器回傳 404 等錯誤訊息。


### 側錄操作行為}

上面的測試中我們都手動建立測試案例，這樣花不少時間，接下來我們介紹如何透過 record and replay 的方式來進行壓力測試。首先我們必須建立一個 proxy server 來側錄我們操作網路的行為。JMeter 裡面就有一個 proxy server, 我們先把它啟動起來，port 設為 8090。接著把瀏覽器的 proxy server 指向這個 port。當我們操作瀏覽器時，proxy server 會把行為錄製起來。下圖中的 (a) 表示瀏覽器直接與 server 要資料，(b) 表示通過 proxy server。

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{./JMeter/jmeter_recoder.png}
FIG: JMeter Recorder 架構。一般的瀏覽器是直接和伺服器溝通(a); JMeter 透過 Proxy 來側錄使用者的行為。}
\label{fig:jmeter_recorder}

<img src="" width="500">

\ifWide \clearpage \fi

```
*Lab: 錄製器}。延續 guess number 例子，但這次使用 Recorder 幫助建立測試案例。當建立 Recorder 之後,使用重播來執行測試案例。
```


- 新增 proxy server。在 JMeter  中的工作台新增一個「非測試元素>> HTTP 代理伺服器」。裡面的端口（port）設為 8090（不要與8080 衝突）。
- 把你的瀏覽器的 proxy server 設為 localhost 的 8090。
- 新增 「邏輯控制器 >> 錄製控制器」。就大功告成，當你操作瀏覽器時，錄製控制器就會不斷的有東西進來，表示錄到東西了。



\begin{figure}[h]
\begin{center}
\includegraphics[width=.8\columnwidth]{./JMeter/jmeter_recorder2.png}

<img src="" width="500">

```
*Lab: 錄製器 II}。連線到 Yahoo 奇摩，任意的操作一些行為並且錄製下來。加大壓力，並觀察其效能。
```

注意 Yahoo 奇摩的防火牆可能因為大量的「攻擊」而封鎖你的請求。另外現在許多網站都加上 SSL，JMeter proxy server 目前也支援憑證，瀏覽器必須先匯入憑證：(以 firefox 為例)


- 啟動 JMeter proxy server 後會產生暫時的憑證。
- 進階 >> 憑證 >> 檢視憑證清單 >> 匯入 >> 選擇 JMeter 所在的目錄 bin，加入 ApacheJMeterTemporaryRootCA.crt。
- 錄製時可以選擇部分檔案記錄下來，在 「要包含的樣式」中輸入：「.*\textbackslash.html」則僅記錄 .html 的檔案（regular expression）。也可以在 「除外的型式」中輸入「.*\textbackslash.gif」則不記錄 .gif 的檔案。


我們可以把設計好的 jmeter 測試檔存起來，你可以發現他是一個 XML 檔，描述著如何進行測試的流程與資料，我們稱之為 test script，各種不同的測試工具都有其不同的 test script 語法。

### Test script}

\begin{tiny}
```java
<?xml version="1.0" encoding="UTF-8"?>
<jmeterTestPlan version="1.2" properties="2.8" jmeter="2.13 r1665067">
  <hashTree>
    <HTTPSamplerProxy guiclass="HttpTestSampleGui" testclass="HTTPSamplerProxy" testname="HTTP 要求" enabled="true">
      <elementProp name="HTTPsampler.Arguments" elementType="Arguments" guiclass="HTTPArgumentsPanel" testclass="Arguments" testname="使用者自訂變數" enabled="true">
        <collectionProp name="Arguments.arguments"/>
      </elementProp>
      <stringProp name="HTTPSampler.domain"></stringProp>
      ...
      <stringProp name="HTTPSampler.path">/examples/jsp/jsp2/el/basic-arithmetic.jsp</stringProp>
      <stringProp name="HTTPSampler.method">GET</stringProp>
      ...
    </HTTPSamplerProxy>
    <hashTree/>
  </hashTree>
</jmeterTestPlan>
```
\end{tiny}

### 進階應用}

以下講解變數的應用、function 的呼叫、session 的應用、regular expression 的應用等。


- \href{https://youtu.be/bys7SnCnYjo}{影片解說}
- \href{https://goo.gl/Jz6pQd}{範例檔}


## 相容性測試}

檢驗系統是相容於各種機器（IBM 360, HP 9000...）、環境、網路、作業系統（Linux, Window, ...）、資料庫（Oracle, SQL server, ...）、網頁伺服器（Apache, Tomcat, ...）、瀏覽器（IE, Chrome, Firefox）等。注意即使是同一個軟體因為版本不同也很可能是不相容的，例如再 IE6 可以運作的在 IE7 就不一定可以。

%To test the application's compatibility with the computing environment.
%Computing environment may contain the elements:
%Computing capacity of Hardware Platform (IBM 360, HP 9000, etc.)..
%Bandwidth handling capacity of networking hardware
%Compatibility of peripherals (Printer, DVD drive, etc.)
%Operating systems (Linux, Windows, etc.)
%Database (Oracle, SQL Server, MySQL, etc.)
%Other System Software (Web server, networking/ messaging tool, etc.)
%Browser compatibility

Browser compatibility testing

- requires that the web applications are tested on different web browsers
- Users have the same visual experience irrespective of the browsers through which they view the web application.
- In terms of functionality, the application must behave and respond the same way across different browsers.
- Carrier compatibility (Verizon, Sprint, Orange, O2, AirTel, etc.)
- Hardware (different phones)

認證測試（Certification testing）是一種比較特殊的相容性測試，主要是由產品的發行產商來測試，由他們來發行他們的產品是用在哪些機器上。例如微軟的 SQL server、Oracle 的 12c 版本是用在哪些機器上與作業系統上，他們都會進行詳盡的測試並公布在官網上，作為軟體公司購買或升級的參考。

## 安全性測試}
暫略

## 回復性測試}
暫略



%\ifEx \exerciseMargin \fi

\clearpage
## 練習

### 使用案例測試}

- 以下何者正確：
	
	- 使用案例案例的撰寫，通常是在整合測試結束，系統測試開始之時
	- 使用案例強調使用者操作的情境與順序
	- 對話式的使用案例是指必須有兩個人以上參與使用案例的設計，才能完整
	- 替代案例表示除了基本案例外的情境，兩者選一來做測試
	- 使用案例測試是一種系統測試
	

- 請用 ATM 提款的情境，透過對話式的使用案例來描述。


%	- Alpha testing 是指第一次系統測試，beta 是指第二次系統測試
%	- 提供快速鍵屬於「user control and freedom」
%	- 效能測試的三個重要因子：輸入端的壓力量、提供服務的環境資源、回應時間
%	- 回歸測試是指系統透過測試上線後，經過修改再次的測試

### 可用性測試}
- 說明三種可用性測試的方式。

- 以下各項與 Neilson 測試哪個準則有關？
	
	- 不同頁面資料儲存的按鈕樣式不同
	- 具備 undo  的功能
	- 一個畫面充斥過多的功能
	- 具備快捷鍵
	- 應用 icon 來表達功能
	- format 磁碟前提醒使用者再次確認
	- 僅告訴使用者密碼設定的強度不足
	

- 列出 Nielsen’s Usability Heuristics 的十個建議。

### 效能測試}

%:question: 
%利用 \href{https://www.google.com/intl/zh-TW/analytics/}{Google Analytics} 來統計你的應用程式的流量。
%}


- 關於效能測試，以下何整正確？
	
	- 其主要階段有三：規劃、測試、分析。
	- 使用輪廓（usage profile）是設計工作流量很重要的參考資料。
	- 頁面瀏覽（Page view）的次數表示某時間區段內拜訪網站的人次。
	- 產用軟體模擬的方式來進行壓力測試是目前常用的作法。
	- Ramp up 的時間，表示壓力測試時，使用者上線所需要的時間。
	- 壓力測試應與系統監控分開，如此才能做精準的測試。
	

- 關於網路行為的計量，以下何者正確？
	
	- Visit 越高，表示不同的使用者進入的次數越高。
	- Hit 越高，表示使用者越多
	- Page view/session 越高，表示使用者每次進入系統會瀏覽多個網頁
	- Session 代表人次，Visit 代表人數。
	

%- 關於壓力測試 (1) 可分為哪三個階段進行 (2) 工作量（workload）是一個很重要的壓力測試參數，一般而言可以有 server-based 與 user-based 的算法，請說明兩者的不同，並舉例說明 (3) 以 JMeter 為例，說明壓力測試工具提供哪些主要的功能？請至少說明五個功能 

- 效能測試可分為負載測試與壓力測試，說明其差異。

- 說明效能測試為何複雜。

- 效能測試的三個主要因子（key factor）為何？

- 針對一個線上考試系統，推測其使用輪廓（usage profile），並依據使用輪廓設計一個壓力測試的工作量（workload）。


- 你想出來創業，開一間效能測試的公司，協助各軟體公司進行效能測試。說明 1) 你公司的利基為何？2) 你的成本預估 3) 該如何進行？哪些議題是需要思考的？4) 如果想使用雲端架構來進行測試，該如何進行？


### JMeter}

- 關於 JMeter 以下和者正確
	
	- thread（執行緒）表示受測的系統是否開啟多工模式
	- 具備多個 listener，提供不同的測試報表
	- 提供方便的指令撰寫測試腳本，但不具備 record and replay 的功能
	- 是 github 所開發的 opensource
	


- 測試 Yahoo：
	
	- 建立一個 Recorder 擷取登入 Yahoo，以及在網站中進行各種活動的動作。
	- 檢視 Recorder，觀察哪些動作被記錄下來。
	- 用 HTTP Proxy 和正規表達式（Regular Expression），篩選出 .jpg 和 .gif 的檔 案。
	
- 自選一個網頁應用程式（可自行開發或找 open source）並安裝於本機或其他主機。安裝 JMeter 以進行測試，並分析結果。
	  
	- *設計劇本}。一個系統會有不同的使用情境; 不同的角色使用的情境不同，每一個情境的比重可能不同。劇本設計的越擬真越好。
	- *應用錄製器}。透過錄製後產生基本的劇本，再擴大為整體完整的劇本。
	- *使用監控軟體}。監控應用系統的各種狀態、監控模擬端的系統狀態、監控網路的狀態（如果發送端與服務端分開的話）。
	- *進行分析}。針對 JMeter 與監控系統所收集到的資料進行分析，分析在不同的壓力下系統的效能行為，進一步的歸納出系統的瓶頸、建議的使用狀況。
	- *包含資料庫之系統效能分析}。所選的應用程式系統包含資料庫的應用; 分析時能夠同時對資料庫、伺服器做出分析。

需要反覆不斷的壓力測試，分析不同壓力下系統的狀況。

### 綜合}

- 何謂系統測試？

- MTBF（mean time between failure） 用來檢測軟體的穩定度，說明其含意

- 回復測試（recoverability test）檢驗系統遇到問題時是否能夠回復到原來的狀態。如果要做到好的回復度，系統設計時要注意什麼？

- 為何需要相容性測試（compatibility test）?

- 以下系統應該特別針對哪些系統測試加強？
	
	- 數位照片網路沖洗系統
	- 台北捷運換幣系統
	- 自動提款機
	- 線上遊戲系統 – LOL
	- 大學聯考電腦自動閱卷系統
	- 監理所車輛管理系統	
	



> {如果你不了解自己所說的事物，即便你遣詞用字精準，也毫無意義。}{There is no sense in being precise when you don’t even know what you’re talking about. - John von Neumann}
