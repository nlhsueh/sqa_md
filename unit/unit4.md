# Chapter IV 軟體檢視

> 到了測試階段才突然重視起品質，為時已晚。

## 基本概念

我們可能較常聽到軟體測試- 而且對他的印象都是「執行、觀看是否有錯誤」。事實上那只能看到「冰山的一角」，因為程式的複雜度很高，每一次執行所到的環境、狀態都不同，結果也會有所不同，這次是對的，未必代表程式是對的。例如一個程式：
 
```java
 for (int = 1; i< max; i++) 
    ...
```    

對於有經驗的工程師而言，檢視程式碼時就會懷疑為什麼 i 會從 1 開始，進而找出這個錯誤。但動態執行剛好能彰顯這個錯誤的機會可能不高。事實上，靜態程式碼檢視已經被視為效率很高、很重要的除錯方法。可惜國人用的並不多，可能是因為認識不夠，或是在趕案子的過程中省略到它了。

<img src="img/inspection/Ice.png" width="500">
FIG: 動態測試只能看到冰山一角

#### 軟體檢視 Software inspection 

軟體檢視是透過觀看、檢視原始碼來找出程式的錯誤或異常。我特別強調「*異常}」，包含不一致的資料型態定義、不一致的撰寫風格、沒有使用組織的元件等都可以視為異常，那是動態執行所看不出的。

「檢視」不只可以運用於程式碼的檢視，也可以擴大到需求規格書、設計規格書、配置的資料、測試資料等。正如同我們前面所提到的，軟體的錯誤來源大宗並不是原始碼、而是規格書、設計等，如果我們能夠早一點發現這些錯誤，就可以避免更大的錯誤、降低整體的品質成本。

> {同儕審查是軟體產業的最佳實務作法。}{Inspections are a software industry best practice.}

相較於動態測試，靜態檢視具備以下優點：

- 一次的檢視可以找到多個錯誤、較根本的錯誤根源。
- 動態測試的一個錯誤可能遮蔽其他的錯誤，造成一些錯誤無法被找到。
- 一些領域知識、程式技巧的知識傳承，方便我們檢視錯誤。
- 可以找到原始文件、程式碼的異常，有助於日後的維護，而非僅是執行上的問題。



> {軟體檢視不是取代動態測試，兩只是互補的關係。

檢視雖然有效，但卻無法取代動態測試。許多異常是無法檢視出來的，例如系統效能的問題，牽涉到整體系統的環境配置，光是靜態的檢視沒有辦法看出異常; 系統功能是否執行正確也須透過執行才能知道。


> {軟體檢視是技術活動，也是社群活動（social activity）。

軟體開發的過程中如果都是冷冰冰的電腦行為，將沒有辦法建立其企業的品質文化。軟體檢視需要大量的人與人之間的互動，不斷的交換其品質的觀念與作法，相關人員將因此學習品質提昇的技巧，是建立品質文化很重要的活動。

### 前置條件

- 有正確明確的規格。
- 成員應該了解熟悉組織標準。
- 已完成（某版本）最終的程式碼 （如果是程式碼檢視）。
- 有準備查核表（checklist）。
- 管理者必須接受檢視在初期會增加成本。
- 管理者不該把檢視當成員工考核。

## 檢視方法

靜態檢視已經發展出很多的作法，以下幾個因素需要考慮：


- ***要不要印出來**？印出來看的會比較仔細，但有時間與環保問題。 Fagan 的 inspection 強調一定要印出文件，但隨著分散式的工作環境、環保、電子環境的成熟許多都透過系統來觀看文件。當然，印出文件來觀看仍有其獨特的效益。
- **會前會**？是否需要先有一個「檢視會議」之前的會議，講解專案的內容與檢視的重點。
- **誰是報告者**？程式的撰寫者或是其他人？由原工程師來報告是最簡便的方式，但有時候會有「球員兼裁判」或是「原作者的盲點」問題，由別人來報告可能更能凸顯問題。
- **檢視者事先的閱讀**？事先閱讀檢視可以加快檢視會議。
- **是否需要查核表**?有查核表才不會有遺漏，但有時也會被限制了項目。
- **誰當檢視者**? 一般而言會找公司內部較有經驗的工程師來進行檢驗，但有時會有同事間批判的問題。要養成「程式碼檢視提昇品質」的氛圍與文化，而不是批鬥大會。有時候也會找外面的專家來進行檢視，提供建議。
- **是否使用工具**？許多靜態檢視是可以透過工具來自動檢查的，例如「變數宣告卻未使用」。但多數時候需要人工，例如「資料結構設計是否合適」等。

IEEE-1028（審查與稽核標準）定義五種審查：Management review (管理審查)、Technical review (技術審查)、Inspection (檢視)、Walkthrough (走查)、Audit (稽核)。

\begin{table}[ht]
\begin{center}
    \begin{tabularx}{\columnwidth}{ | l | X | X |}
    \hline
    Type & 檢視 & 走查  \\ \hline
    形式 & formal & informal \\ \hline
    計畫 & 事先規劃角色成員 & 未計畫 \\ \hline
    導讀 & 導讀者 & 作者 \\ \hline
    記錄 & 記錄者 & 作者 \\ \hline
    主席 & 協調者 Moderator & 沒有      \\
    \hline
    \end{tabularx}
    FIG: 檢視與走查}
    \label{table:inspection}

\end{table}

> {軟體檢視沒有絕對的形式，依組織特性客製化很重要。

\myvideo{https://youtu.be/ocMraYgqHvg}{Code review example }


#### 流程 

比較完整的流程包含：計畫、會前會、個別準備、檢視會議、修改、再檢視。 
- 計畫。選擇是適當的人來參與檢視。
- 會前會。對專案做一說明，方便審查。
- 個別準備。各參與人員在正式會議之前先檢視目的物。
- 檢視會議。正式開始會議。
- 修改。依據建議修改文件或程式。主席會決議是否需要再檢視，或是由撰寫自行檢查、或交由特定人再檢查。
- 再檢視。依據上次的記錄進行再檢視。

FIG: 檢視的流程
<img src="img/inspection/InspectionFlow.png" width="500">


#### 角色

一般而言，在檢視的流程中，會包含以下的角色：
- 作者或擁有者, 產生文件或程式者; 負責修改文件或程式者。
- 檢視者: 找出文件或程式中不一致、錯誤、缺陷的地方的人。
- 報告者 : 負責報告/導讀文件或程式者。有時候會是作者本人。
- 記錄者: 負責記錄會議過程與結果者。
- 主席或協調者: 管理會議流程或協調會議進行者。

> 軟體檢視不會自己動起來-- 它需要資源的挹注。

在執行軟體檢視之前，企業需要先規劃其流程，並且制定此流程需要的輔助，例如程序書（procedure）、表單（form）、檢核表（checklist）、教育訓練、工具以及「時間」等。

> {軟體檢視的哲學簡單的說就是- 同事找到錯誤，絕對比顧客找到錯誤來的好。}{We prefer to have a peer, rather than a customer, find a defect.}

%The reuse domain and programming knowledge so reviewers are likely to have seen the types of error that commonly arise.

### 檢視的指引

- 人員的選擇與事先的準備	
	- 限制參與人員。
	- 事前做充分準備。
	- 將更多程式碼給評審員時，可能為了效率(Time boxing)就不會花費大量時間去評審，這樣一來效益就降低。
	- 針對每項工作產品發展相對的檢查清單。
	- 給審查員應有的審查工作時間與資源。	
	- 會議之前準備好所有相關材料
	- 在別人審查你的程式前，最好自我檢查。	
	

- 審查
	- 審查開始前，確保受審程式或文件作者先大致講解。
	- 審查軟體開發程序或所開發的產品，不是審查開發者個人。牢記批評或給建議很容易，但是真正執行是困難的。
	- 不要陷入辯論與反駁的口頭之爭。
	- 此為錯誤偵測而非問題解決會議。
	- 尊重每位參與者發表意見的權利與認真傾聽其意見。
	- 設定議程時間，並努力在預定議程時間內完成會議。
	- 審查的速度不宜過快，例如每次程式評審應少於 200–400 LOC/Hr (休息10分鐘)，依據不同的專案、技術有所不同。
	- 記錄會議中所有決議。
	- 處理後續的問題(Action item)並參與後續會議
				
以下幾節我們針對不同階段（需求規格階段、系統設計階段、系統開發階段）所進行的檢視做更詳細的描述。

## 規格檢視

規格的制定是開發流程一開始的步驟，如果這個步驟錯了，後面的矯正所需要的時間或成本就更大了。以下是一些系統規格檢視（或審查）重要的項目：

- **正確** Correct. Every requirement stated therein represents something required of the system to be built. 

- **不模稜兩可** Unambiguous. Every requirement stated therein has only one interpretation. 以下兩個系統的規格描述清楚嗎？	
	- 本系統將與會計系統整合
- **完整的** Complete. Everything that the software is supposed to do is included in the SRS.

<img src="img/inspection/completeSRS.png" width="500">

- **可驗證的** Verifiable. A SRS is verifiable iff every requirement state therein is verifiable; A requirement is verifiable iff There exists some finite cost effective process with which a person or machine can check that the actual as-built software product meets the requirement.

- **一致的** Consistent. no requirement stated therein is in conflict with other preceding documents, and no subset of requirements stated therein conflict.

<img src="img/inspection/correctSRS.png" width="500">

- **顧客能了解的** Understandable by customer. Customers can read and understand the specification. 

- **可回朔的** Traced. Establish the traceability between customer requirement and system requirement. An SRS is traced if the origin of each of its requirements is clear.

- **可追朔的** Traceable. In order to design or test any component of the software, it is necessary to know which requirements are (perhaps) being satisfied by the components
Techniques. 

<img src="img/inspection/tracedSRS.png" width="500">

- **設計獨立的** Design independent. It does not imply a specific software architecture or algorithm; No requirement in the SRS should limit the design to just one alternative.

- **簡潔的** Concise. 

- **有組織的** Organized. Requirements contained therein are easy to locate; Requirements are arranged so that requirements that are related are co-located.


規格又可以細分為需求規格與系統規格，比較嚴格的流程還可以區分需求規格檢視與系統規格檢視。

> When an SRS is  un-ambiguous, more verifiable, complete and consistent, it is not understandable by customers. 

寫規格書的一些建議：

- 結構化的方式來組織你的文件；
- 一致性的圖形符號和字眼；
- 說明或定義所有的縮寫；
- 文件必須包含目錄，如果能包含索引表、字彙表更好；
- 總是從讀者的角度來來觀看此文件：如果我對此系統不熟悉，我能了解此文件嗎？
- 當你在解釋一個結構（或架構），畫一張圖輔助說明吧；
- 畫架構圖時，應有文字輔以說明，圖內的專有名詞與文字應一致；
- 當你寫出一些數學式，用文字的方式解釋它；
- 當你定義了一些計算，至少用兩個例子說明它；
- 當你說「總是、所有、沒有任何、都不會」時，再想一下吧，真的如此嗎？
- 當你說「很明顯的，因此，很清楚的，顯然的」時，邏輯上真的如此嗎？
- 當你說「一些，有時候，通常，經常，大部分」時，請明確；
- 當你在列表後加上「等等、依此類推、類似」時，讀者真的能夠依此類推嗎？
-  當你說「處理（process）」，是如何被處理？
- 儘量不要使用被動式：此參數會被初始化，被誰初始化？
- 提到支援某軟體或協定時，說明是哪一個版本。

:question: 針對此 \href{https://drive.google.com/file/d/0B_Be8Sd_tsM7S0t6bE5KV1hGeWs/view?usp=sharing}{智慧校園服務系統- 軟體需求規格書}，透過上述的查核表檢查此規格是否合適。}

:question: 課堂練習：針對一個三角形判斷的系統，寫出其規格書。透過上述的查核表檢查此規格是否合適。}

%> {品質的最簡單、最困難與最有效果的作法：review, review, review!

## 設計檢視

圖 \ref{table:design_ck} 為一個簡約的設計查核表，檢查設計是滿足完整性、邏輯性、特殊情況的處理、方法呼叫、命名、與標準是否符合規範。

\begin{table}[ht]
\begin{center}
    \begin{tabularx}{\columnwidth}{ | l | X | l | l | }    \hline    
項目 		& 說明 & Pass?  & 備註\\ \hline \hline
%一般性 	& 是否完成每一個審查步驟。& & \\  \hline
完整性 	& 是否此設計規格，涵蓋所有相關需求描述、需求規格、高階設計規格。& & \\ \hline
邏輯性 	& 驗證數學公式、運算流程的正確性。& & \\ \hline
特殊情況& 檢查所有特殊狀況，是否處理所有不正確的輸入。& & \\ \hline
方法呼叫 & 檢查所有介面都精確的定義。& & \\ \hline
命名 		& 所有特別的名稱和型態都被清楚定義。& & \\ \hline
標準 		& 是否遵循所有相關組織標準。& & \\ \hline
    \end{tabularx}
    FIG: 簡易的設計檢核表}
    \label{table:design_ck}

\end{table}

更完整的檢核表如下。事實上，不同的組織可以依據其特性、需求、文化建立不同的檢核表。

- 對於以下的設計實體（design entity）是否以下的屬性都有適當描述？ 
	
	- 唯一的識別碼、代稱或名稱。	
	- 型態，例如資料庫、程式模組或檔案等。	
	- 目的。
	- 功能。%Function (summarizing what the component does) 
	- 相依性，與其他模組或是功能規格的關係。%Dependencies (possibly `none'; describing the requires or uses relationship) 
	- 介面，描述一個設計模組的程式介面。%Interface (provided by the design entity) 
	- 資料，內含的資料。%Data (information `hidden' inside) 
	

- 設計與需求的關係是否清楚描述？是否描述為何採取此設計架構？

- 是否此架構簡潔明瞭？
	
	- 是否符合高內聚力、低耦合度的原則？%No more than 7 loosely-coupled coherent high-level components. 
	- 低階的模組設計是否被高階的元件所聚合？亦即，設計是否具備階層式？%Lower-level components possibly clustered into high-level components (hierarchy). 
	- 使用標準的元件。%Using standard(ized) components. 
	- 是否直覺容易了解？可否有更精簡易懂的方案？%Is deviation from intuitively obvious solution motivated? 
	
	
- 此架構是否完整？
	
	- 是否包含所有需求？%Are all requirements covered? 
	- 檢查一些重要的需求，檢視此架構是否能夠符合。%Trace some critical requirements through the architecture (e.g. via use cases). 		
	
- 是否元件的描述正確且完整？	
	- 是否可以單獨的被建構？%Do they allow independent construction? 
	- 介面細節是否清楚？		
		- 副程式的種類、名稱、參數型態、回傳型態、前置條件、後置條件等。
		- 檔案名稱、格式、存取權。%File name, format, permissions. 
%		- Socket number and protocol. 
		- 共享變數、同步的單元。%Shared variables, synchronization primitives (locks). 
		- 可能採取的程式語言是否可以支援？%Have features of the target programming language been used where appropriate? 
		- 不必要的實作細節是否被描述了？%Have implementation details been avoided? (No details of internal classes.) 	
					
- 元件之間的關係是否有清楚的描述？最好是以圖形的方式描述清楚。

- 所提的解決方案是否可行？元件是否可被確實的實踐，並且與其他元件整合？%Can the components be implemented or 	

- 是否描述相關的架構角度 （architectural views）? 
	
	- **Logical** (Structural) view：邏輯的設計，例如透過類別圖來描述每個邏輯實體的功能。% (class diagram per component expresses functionality). 
	- **Process** view： 控制緒如何被設置、互動與結束。
	- **Physical** view：各程式實體如何被配置在電腦、網路、手機等計算單元上？可透過 deploy diagram 來描述。 
	- **Development** view：系統配置的角度。
			
- 是否考慮以下的設計議題並提出解決方案？	
	- Exception handling. 
	- Initialization and reset. 
	- Memory management. 
	- Security. 
	- Internationalization. 
	- Built-in help. 
	- Built-in test facilities. 
- 是否所有的數學式子及圖形都有清楚的文字解說？

### 設計模型檢核

當我們進行設計時，我們會採用一些設計模組，例如 DFD, UML, ER model 等。除了這些模型是「圖形視覺化」以外，另一個優點是這些模型有一定的規範，便於我們進行檢核。

DFD/ER model 是一個我們經常用來做系統設計的工具，設計完成後我們需要進行檢驗。

FIG: Data flow diagram
<img src="img/inspection/dfd.png" width="500">

\myvideo{https://youtu.be/ztZsEI6C-mI}{Data Flow Diagram example}

\myvideo{https://youtu.be/Ik85hZkyYPA}{DFD diagram 0}

- *External entities} must be people or systems that send information to or accept information form the system to be engineered.

- Data flows must always be *labelled with the data} they contain. Do not put verbs in the data flow description as this implies a process.

- Parent and child diagrams should be *consistent}. Do not show a data flow coming from or to an external entity on a level 1 DFD that isn’t shown on the context diagram (and vice versa).

- Check the *direction} of data flows to and from data stores.
- Make sure each process has at least one *input} and one *output}.
- Each data store should have *at least one input and one output} on the DFDs somewhere.
- Each process name should start with a *verb}.
- Where a process has only two data flows (one input and one output) then check it. Usually a data flow has been omitted.


這只是 DFD 的檢核表，如果組織採用的是其他的設計模型，就應該建立其相關的檢核表。

\RefEx{ex:OnlineTest}

> {經驗老道的工程師或許可以不需要檢核表而進行檢核，但在那之前，檢核表是必須的。

## 程式碼檢視

程式碼檢視 Code inspection。

- 資料錯誤 Data faults。變數在應用時有無產生異常。
  
- 變數未初始化就使用 Variables used before initialization
- 變數宣告但不曾使用 Variables declared but never used
- 變數被指定兩次值，但過程中未被使用 Variables assigned twice but never used between assignments
- 超過陣列範圍的使用 Possible array bound violations 
- 沒有宣告的變數 Undeclared variables

- 控制錯誤 Control faults 
  
- 無法到達的程式碼 Unreachable code
- 輸入輸出錯誤 Input/output faults 
- 變數值印出兩次，但中間沒有新的給定值。Variables output twice with no intervening assignment


- 介面錯誤 Interface faults 
  
- 參數型態不吻合 Parameter type mismatches
- 參數個數錯誤 Parameter number mismatches
- 功能的結果回傳卻沒有使用 Non-usage of the results of functions
- 不曾被呼叫的功能與方法 Uncalled functions and procedures

- 編碼規範
	
	- 命名規範
	- 介面整合規範
	- 資料查詢規範
	- 安全編碼規範
	

FIG: 遭透了的變數命名
<img src="img/inspection/NameStandard.png" width="500">

\href{http://www.java-success.com/30-java-code-review-checklist-items/}{Java code review checklist}

> {好的程式本身就是最好的註解。加程式註解前想想：如何改善程式碼讓我不需要加這個註解？改善程式碼並加上註解讓你的程式更清楚。}{Good code is its own best documentation. As you're about to add a comment, ask yourself, "How can I improve the code so that this comment isn't needed? Improve the code and then document it to make it even clearer. -- Steve McConnell}

### 程式臭味檢視

程式碼審查時也會針對程式碼臭味進行檢驗，並提出一些重整的建議。以下是部分 Folwer 提出的程式臭味 \cite{fowler2009refactoring}：


- *重複的程式碼 Duplicated Code}。重複的程式碼應該抽出來集中在一個類別（或元件）中，需要的時候再去繼承或呼叫。重複的程式碼的維護性很低：我們常常改了這個忘了改另一個。

- *冗長的方法 Long Method}。一個1000 行的程式碼好不好看得懂？好不好維護？一個方法通常代表一個處理的流程或演算法，大到某個程度後我們就必須要學會「抽象」- 把部分的流程抽象到另一個方法裡。

- *大類別 Large Class}。同理，一個大類別包含很多的屬性、方法讓程式員難以理解類別的責任，應該把責任做分割，交給另一個類別來做。

- *太長的參數列 Long Parameter List}。參數太多太長時（想像一下，10個參數），參數代表一個方法可以調整的靈活度，有其複雜度，太多的參數令人難以理解該方法的彈性。一樣，我們應該把部分的參數彙整起來，抽象成另一個物件類別。

- *發散變更 Divergent Change}：一個類別有太多的變更原因。一個類別最好能有一個專一的功能，也就是內聚力要高，方法之間是有關係的。這也表示不要炒大鍋菜一樣把不相關的功能都擠在一個類別內。

- *散彈槍手術 Shotgun Surgery}：一個變更，要改很多其他模組。想像一下一個「班級人數」的值散落在10 個模組裡，當這個人數值需要改變時，你需要翻箱倒櫃的修改這十個模組。如果這個值是放在一個設定檔中，模組啟動時去讀這個檔就好了，哪麼你的修改就會少很多。

- *依戀情結 Feature Envy}：一個計算要取好多其他類別的值。一個內聚力強的類別其計算會用到該類別的屬性，例如一個 Circle 的物件，有一個 area() 的方法來計算他的面積會用到他內部的屬性 ridius，少許的引用其他類別的資料來運算當然也很正常，但如果過份的依賴大量其他的類別，那麼你的抽象化可能就出現了問題。是不是這個計算應該移到別的類別中？

- *資料泥團 Data Clumps}：常常會一起出現的資料卻沒有抽象呈一個類別型態。例如說住址，有一群的城市、街道、ZIP code、號等字串出現，為什麼不把它抽象成 Address 的類別呢？

- *基本型別偏執 Primitive Obsession}：不用小類別，堅持用基本型別。例如「錢」的這個變數，你可能會用 int money 來代表，又發現需要描述是哪個國家的幣值，所以又加了一個變數 String country。這會讓程式碼變得凌亂難懂，其實我們可以宣告一個小類別 Money，裡面包含這兩個屬性。

- *Switch 敘述句}：太多的 switch case, 不會用多型。Switch 有一個缺點，當你要新增一個 case 選項時，你需要修改程式碼。如果我們本來就預期會有 case 的改變，那麼就用多型吧，至少可以不在修改程式的情況下，透過擴充來完成彈性的設計。

- *冗員類別 Lazy Class}：沒什麼功能的類別。

- *不實用的一般性 Speculative Generality}: 預留的太多不實用的擴充點。為了滿足「擴充性上的彈性」，我們常常會把程式寫的複雜些 \footnote{可以看看 design pattern 的書}，但是仔細想一想，是不是這些擴充真的需要？還是為了設計而設計。

- *暫時欄位 Temporary Field}: 有一些暫時欄位只對某些特殊的方法或特殊時機才會用到，令人難以了解他的意義。例如為了不想傳太多參數就把某些值以 instance variable 的方式寫在類別內。

- *過度的訊息串 Message Chains}：$a.getB().getC().getD()$ ... 當訊息串過長時可能是功能封裝的有問題，可能要考慮直接的訊息傳遞。

- *過度的中間人 Middle Man}：太多的方法都是透過委託來進行，該類別的方法封裝要考慮改寫。

- *狎暱關係 Inappropriate Intimacy}：類別間的過於親密的屬性存取，可以考慮分開來以 delegation 的方式來進行。例如不適當的宣告子類別，讓子類別任意存取父類別的資料。


%## 程式碼檢視工具 (lab)}


## FindBugs (lab)
馬里蘭大學的研究成果，可以對 Java 的程式碼做靜態的檢測，處理超過200 個錯誤，分為以下種類：

- 正確性問題 Correctness：無窮迴圈，讀取空值（未曾寫入過）。
- 不好的寫法 Bad practice：沒有關閉檔案或是不處理例外。
- 效能的改善。
- 多執行敘的問題。
- Dodgy 問題：沒有使用的變數或沒有檢查的 cast。

安裝方法：在 Eclipse >> Help >> Eclipse Marketplace >> 輸入 FindBugs 就可以找到該外掛，安裝後重新啟動，可以在 Preference >> Java >> FindBugs 下做一些設定，例如錯誤的敏感度與種類等。

FIG: FingBugs Preference}
<img src="img/bug/FindBugsPreference.png" width="500">

錯誤的嚴重性分為 1-20, 1 表示最嚴重。

- 很嚴重 scariest (rank 1-4)
- 可怕 scary (rank 5-9)
- 麻煩 troubling (rank 10-14)
- 注意 of concern (rank 15-20)

開發時，在該程式按右鍵可以找到該 FingBugs 的選項，點選就會出現找出來的 Bugs。

```
練習：透過 FindBugs 找出以下的錯誤

- \href{code/findbugs/FindBugsDemo1.java}{Lab 1}
- \href{code/findbugs/FindBugsDemo2.java}{Lab 2}
- \href{code/findbugs/FindBugsDemo3.java}{Lab 3}
```

See \href{http://findbugs.sourceforge.net/}{FindBugs web site}, 你可以在 [Find bug description] 一節中找到 FingBugs 可以偵測出的錯誤與其樣式。


FIG: FingBugs 的執行
<img src="img/bug/FindBugsRun.png" width="500">

## CheckStyle (lab)

CheckStyle 是 Eclipse 上一個可以檢查程式碼風格的外掛。

安裝方法：打開 Eclipse >> Help >> Eclipse Market place >> search "CheckStyle" >> install

see \href{http://eclipse-cs.sourceforge.net/#!/project-setup}{SET-UP}

> {自動化檢核工具只能輔助檢核，無法取代。

## 檢視的評估

一般而言，檢視可降低後續測試時間與增加測試品質，即降低錯誤數量(預測最終軟體仍然存在的錯誤量)。但如何評估檢視的效益？仍可透過量化方法加以統計分析以作為後續改良的依據：

- 缺失偵測效率(Error defection efficiency)：每個小時審查發現缺失的數量，每一頁或每一行(LOC)發現缺失的數量。
- 審查記錄上，特定型態(reqts/design/code)的錯誤偵測數量/所有測試方法找出的錯誤數量。
- 成本效用(Cost effectiveness): 由審查者找出錯誤的成本，與此錯誤若留到後面修復，測試、與除錯所花的成本，兩者的比率。
- 錯誤密度(Defect Density)：審查報告或錯誤報告中錯誤的數量，除以，預估程式的大小。
- Defect removal leverage (DRL)：針對兩個不同階段，每小時錯誤移除的比率。可比較出兩個不同階段，使用不同程序的相對效果。

為了計算這些度量，我們需要收集以下資訊：

- 審查項目的大小。
- 審查花費的時間。
- 缺失發現的數量。
- 缺失未發現，但在之後的再次審查、或測試、或使用者使用時出現的缺失數量。

\RefEx{ex:Evaluate}

> {A: 你每小時可以寫多 少行程式碼?B:你每千行 會產生多少個 Bug?


## BB 雄太軟體公司

江 Sir 打電話來：「雄太，我想我們要開會談一下」。

這讓雄太微微的感到不安。前陣子的 demo 很順利，難得看到江 Sir 這麼滿意一個系統。這也難怪，這個案子是 Tiger 做的，可以說是公司裡最強的工程師、兼具系統分析師、專案經理。

說起 Tiger，雄太就想起他那時候面試的情境，蓬頭垢面一副無精打采的樣子，面試很快就結束了- 沒有任何主管考慮他。後來輾轉知道「陳泰格」原來就是在網路上頂頂有名的 「Tiger Chen」，面試的時候無精打采是因為前一天趕系統一夜沒睡。經過一番討論，Tiger 還是進來了，而且表現的比預期的好。

會議一開始，江 Sir 開門見山：「雄太，這個系統功能我們是很滿意，介面、效能都比過去廠商做的好很多」。「是阿...」還沒等雄太往下說，江 Sir 接著說「但是，你知道我們公司的規定，對於外包廠商的程式碼必須進行 code review」。

雄太心裡頭震了一下，難道是程式碼寫的不好？不會吧，Tiger ㄟ。江 Sir 指揮著同仁把程式碼打上單槍，「你看... 前面都很棒，註解也很清楚... 我們的同仁看了以後大致都懂」。頁面不斷的往下滑，停住了，江 Sir 指著著解說：「你看」。

```java 
 // 什麼爛公司，需求是不會一次說清楚喔，改來改去！Shit!
```

有點尷尬，趕緊打個圓場：「哎呀，工程師偶而發洩一下，我請他們趕緊改掉」。江 Sir 沒多說什麼，把畫面繼續往下捲，停住。這下子雄太的臉綠了 ---

```java
 // 下面的程式碼不知道誰寫的，參數放 34 的時候就 ok，但 35 就會有錯。照理說應該是 35，不知道為什麼？
```

「嗯，... 這個可能是... 」雄太心裡頭罵髒話：「真糟糕！要交付之前怎麼沒修飾一下註解！！」

江 Sir 再往下滑，又停住 --- 

```java
 // 以下的程式碼恐怕有資安的疑慮，先這樣，以後有空再改。
```

雄太想，或許短時間不能驗收了。


## 練習



### 軟體檢視
- 關於軟體檢視（software inspection）以下何者為真？
	
	- 軟體檢視的成本較高，但可以有效的取代動態測試。
	- 軟體檢視的範圍侷限在程式碼檢視。 
	- 軟體檢視通常需要檢查表，而檢查表會依據檢查項目與作法有所不同。 
	- 軟體檢視除了可以檢查軟體的問題，也可以同時考核員工能力，是一舉數得的作法。
	

- 靜態測試的前置條件為何？


- 一般的軟體檢視的流程為何？

- 軟體檢視通常有哪些角色？


### 規格檢視}
- 以下不是一個好的系統規格應具備的特性 
	
	- 應該描述系統設計的架構 
	- 應該清楚不模糊 
	- 應該可以回朔到使用者需求 
	- 應該是可以測試的
	

- 設計檢視的項目不該具備以下項目？
	
	- 應包含所有需求 
	- 公開元件的介面介紹應該描述清楚 
	- 對於設計圖形與數學式應該清楚描述 
	- 應該包含架構的考量 
	- 應該採取單一且明確的角度來描述設計，比免從多個角度描述
	

- 一個好的系統規格，應該具備哪些特性？

- 系統規格中，可回朔（traced）與可追朔（traceable）的差別為何？



- 描述「三角形判斷系統」的規格，並以規格檢查表檢查是否通過。


### 設計檢視 

- 進行系統設計檢視時，檢視的項目有哪些？請列出三項。
- 針對「三角形判斷系統」進行設計，並以設計檢查表檢查是否通過。
- 針對過去執行過或是目前正在執行的專案（專題），設計一張「設計檢視」查核表。
- 針對一個簡易的「線上考試系統」設計 DFD，講義中的檢核表來來檢驗看看是否正確。

### 程式碼檢視

- 針對「三角形判斷系統」進行實作，並以程式碼檢視的方式查看是否通過。
- 撰寫一個 HelloWorld, 符合 Google coding style
- 同上，變更為 Sun coding style
- 撰寫一個方法，取得兩數的最大公因數，符合 Google coding style
- 同上，修改 Google coding style 存成 BearBig coding style
- 列出五個 Folwer 的程式臭味。

### 檢視的評估
- 「缺失到後面的階段，付出的成本越大」，為什麼我們知道這樣的現象？以工程的角度需要數據來收集計算比較。試說明需要收集哪些資料，如何計算。

### 綜合
-  :speech_balloon: 分為開發組與檢核組，針對一個線上考試系統的子系統「線上出題」，開發組規劃一個系統規格書，檢核組則設計檢核表，並進行檢核。
