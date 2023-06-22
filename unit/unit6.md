# Uni 6 白箱測試

白箱測試是只在知道程式的內部結構下進行的測試，其測試的目的是了解程式碼被測試的程度。

**White Box Testing}{A method of testing software that tests internal structures or workings of an application, as opposed to its functionality (i.e. black-box testing)}

## 測試涵蓋度

```java [numbers=left, frame=single]
input A,B,X 
if (A>1) and (B=0) then
  Y=A 
if (A=2) or (X>1) then
  Y=X 
print Y
```

%我們用流程圖來表示上述的程式：
%\begin{figure}[h]
%\begin{center}
%\includegraphics[width=2.5in]{img/sqa/coverage.png}
%FIG: Program graph}
%
%<img src="" width="500">

### 敘述涵蓋度
*設計測試案例，使每一條指令敘述至少執行一次}。輸入為 (A,B,X) = (2,0,3) 就可覆蓋所有可執行指令，結果會得到 3。即便所有的敘述都被執行了，此方法並不是很「嚴謹」的方法：如果我們犯了以下的錯誤：

- 行號 2 的AND改成OR，或是 
- 行號 3 Y=A改成其他的敘述 
- 行號 4 的X>1改成X>0，或是 

測試案例 (2,0,3) 並不能找出你犯的錯誤，這表示這組測試案例太弱了。事實上，敘述覆蓋準則是這幾個方法中最弱的一個，白箱測試至少要做到此測試。

### 分支涵蓋度
分支涵蓋度（branch coverage）又稱為決策涵蓋度（decision coverage）。其目標是設計測試案例使程式每個判斷取 *真分支和取假分支至少執行一次}。上述的例子有兩個 branch:


- (A>1) AND (B=0)
- (A=2) OR (X>1)

我們必須設計一些測試資料讓這兩個 branch 的真假都至少一次。
A,B,X若為(3,0,3)和(3,1,1)能使得 (A>1) AND (B=0)和(A=2) OR (X>1)這兩個布林運算式均能產生真和假的值。 

\begin{table}[h]
\begin{center}
FIG: 測試涵蓋表}
\begin{tabular}{|c|c|c|c|c|}
\hline
 & \multicolumn{2}{l|}{(A\textgreater1) AND (B=0)} & \multicolumn{2}{l|}{(A=2) OR (X\textgreater1)} \\ \hline
(A,B,X) & True & False & True & False \\ \hline
(3,0,3) & V &  & V &  \\ \hline
(3,1,1) &  & V &  & V \\ \hline
\end{tabular}

\end{table}

分支涵蓋度所找出來的測試案例會比敘述涵蓋度的多，也因此比較能找出程式的錯誤。但，很顯然的，也不可找出所有的錯誤。例如若我們將 (A>1)寫成(A>2)，涵蓋度一樣 100%，執行結果也一樣，我們就無法知道程式寫錯了。

:question: 針對任何程式，我們一定可以找到一群測試案例，使得分支涵蓋度為百分百？}

### 條件涵蓋度}

條件覆蓋（condition）和分支覆蓋類似，不過條件覆蓋是以某項條件為主，而決策涵蓋則以整個布林運算式為主。使程式中每個判斷的每個條件至少執行一次。例如 (A>1) AND (B=0) 運算式包含 A>1 和 B=0 兩條件。前述程式具有下列四條件 A>1、B=0、A=2、X>1。欲使這四個條件都能產生真與假的值，測試案例須包含以下八種案例：

```java
(1) A>1, (2) A<=1 
(3) B=0, (4) B<>0 
(5) A=2, (6) A<>2 
(7) X>1, (8) X<=1 
```

測試資料 (2,0,3) 滿足 (1)、(3)、(5)、(7)。(1,1,1) 滿足(2)、(4)、(6)、(8)。因此，測試案例 {(2,0,3), (1,1,1)} 便可達成這個目標。



*滿足條件涵蓋度的測試資料，一定滿足分支涵蓋度嗎}？看起來很像是這麼一回事，因為前者把條件從分支中分離出來做詳細的檢查了阿！但並非如此：

\begin{table}[h]
\begin{center}
\begin{tabular}{|c|c|c|c|}
\hline
 & p & q & p \& q \\ \hline
t1 & True & False & False \\ \hline
t2 & False & True & False \\ \hline
\end{tabular}

\end{table}

上表中的 測試案例 t1, t2 雖然可以是條件 p, q, 都有 true, false, 但 p\&q 這個分支的值卻都是 false 的。


### 分支與條件涵蓋度

如上節所言，條件覆蓋嚴密性通常比決策覆蓋高，*但非絕對}。例如 (1,0,3) 和 (2,1,1) 這組數據，雖然使上述四個條件均產生真與假的值，但並未使運算式 (A>1) AND (B=0) 和 (A=2) OR (X>1) 具有真與假的值。 因此，『分支與條件涵蓋度」設計足夠的測試案例，使判斷中每個條件的所有可能值至少執行一次，同時每個判斷的所有可能判斷結果至少執行一次。上例中， (2,0,3) 和 (1,1,1) 可達成此目標。

> 順著程式的邏輯來做測試無法檢驗功能，只能檢驗涵蓋度。


> 針對以下程式 (1) 設計一測試案例達到百分百敘述涵蓋度 (SC100); (2) 設計一測試案例達到百分百條件涵蓋度 (CC100)，但非百分百分支涵蓋度; (3) 設計一測試案例達到百分百分支涵蓋度 (BC100)，但非百分百條件涵蓋度 (!CC100)。請畫出 測試涵蓋表  來檢驗。

```java
read(X, Y)
if ((X>10) && (Y==1))
    X=1;
else if ((X-Y) < 2)
    X=2;
if (Y >10)
    X=3;
print X
```

要完成敘述涵蓋 (SC100) 是容易的，只要能夠讓 03, 05, 07 的敘述進入即可，因此我們設計 (X=11, Y=1) 及 (X=12, Y=11) 兩筆資料即可達到此涵蓋。

要完成 CC100 卻不 BC100，表示在複合條件上需要做處理，也就是 02 行的條件判斷。假設所有的條件分別是 c1, c2, c3, c4。我們讓這五個條件的 True False 都經歷過，但 b1 (c1\&\&c2) 只有經歷 True, False 其中一個，唯一可行的是 b1 只經過 False。因此測試案例如下：

\begin{table}[h]
\begin{tabular}{|l|l|l|l|l|l|l|}
\hline
X  & Y  & c1 & c2 & b1 & c3 & c4 \\ \hline
9  & 1  & F  & T  & *F}  & F  & F  \\ \hline
12 & 11 & T  & F  & *F}  & T  & T  \\ \hline
\end{tabular}
\end{table}

要完成 BC 卻不 CC，表示 b1 必須經歷 T/F，但 c1 或 c2 其中之一只經歷 T/F 其中一個。因此測試案例如下。其中 c1 只經歷 T, 而 b1 經歷 T/F。

\begin{center}
\begin{table}[h]
\begin{tabular}{|l|l|l|l|l|l|l|}
\hline
X  & Y  & c1 & c2 & b1 & c3 & c4 \\ \hline
13  & 1  & *T}  & T  & T  				& -  	& F  \\ \hline
12 & 11 & *T}  & F  & *F}  & T  & T  \\ \hline
12 & 2	  & *T}  & F  & *T}  & F  & F  \\ \hline
\end{tabular}
\end{table}


### 多重條件組合涵蓋度
多重條件組合涵蓋（multiple-condition combination coverage）的方法是從決策/條件涵蓋方法延伸，目標是使測試資料涵蓋每個布林運算式中各種條件組合。例如前述程式，第一個布林運算式有下列 4 種條件組合：

```java
(1) A>1，B=0  
(2) A>1，B<>0  
(3) A<=1，B=0  
(4) A<=1，B<>0  
```

第二個布林運算式也有下列4種條件組合：

```java
(5) A=2，X>1  
(6) A=2，X<=1  
(7) A<>2，X>1  
(8) A<>2，X<=1  
```

測試資料 (2,0,4) 滿足1、5。(2,1,1) 滿足 2、6。(1,0,2) 滿足3、7。(1,1,1) 滿足4、8。因此這四個測試資料所組合成的測試資料群便可涵蓋上述 8 種條件組合。 


FIG: 各種涵蓋度的關係

<img src="img/sqa/coverage3.png" width="500">

> Programmer 必須自己進行單元測試，配合 JUnit 及涵蓋度檢查工具的使用，檢查自己的測試是否足夠。


### 路徑涵蓋度

上述的幾種方法，涵蓋度都是以敘述、條件或是分支為單位，如果把「路徑」考量進去就會越複雜。例如上述的 (2,0,4), (2,1,1), (1,0,2), (1,1,1) 測試資料，雖然可以把所有的 敘述、條件、分支都涵蓋，但以路徑的角度來看，他只涵蓋了 a-c-e, a-b-e, a-b-d 等三個路徑（如圖 \ref{fig_path_coverage}): 

FIG: 路徑涵蓋度

<img src="img/whitebox/coverage.png" width="500">

```
(2,0,4): 走 a-c-e 
(2,1,1): 走 a-b-e  
(1,0,2): 走 a-b-e 
(1,1,1): 走 a-b-d  
```

也就是 a-c-d 這個路徑並沒有走過。如果我們要走過所有路徑的話，我們需要 $2^2=4$ 個路徑，這看起來不難，但如果有迴圈的話，假設走 20 遍，我們就需要 $4^{20} = 2^{40}=1.0995116e+12$，這已經失去測試的意義了。即便 a-c-d 這個路徑有其意義（或許 c 的動作可能會影響 d 的行為），但 all-path 的測試成本實在太高了。

圖 \ref{fig_coverage_relation} 統整了本節所講的涵蓋度的關係。最上方（路徑涵蓋度）是最嚴謹的，依序往下。分支涵蓋度與條件涵蓋度沒有絕對的關係，因此平行。分支涵蓋度百分百時，敘述涵蓋度也為百分百。值得一提的是，條件涵蓋度百分百時並不保證敘述涵蓋度為百分百。

## 測試涵蓋度工具 (lab)

- \href{http://eclemma.org/}{EclEmma}, EclEmma is a free Java code coverage tool for Eclipse, available under the Eclipse Public License.
- \href{http://eclemma.org/jacoco/}{JaCoCo}, JaCoCo is a free code coverage library for Java, which has been created by the EclEmma team based on the lessons learned from using and integration existing libraries for many years.


### Eclemma

\href{http://www.eclemma.org/}{\underline{EclEmma}} 是一個在 Eclipse 上的 Java 程式碼涵蓋工具外掛，與 JUnit 配合它可以檢驗還有哪些敘述還沒有被執行到、測試到。

安裝及使用步驟
  
- 在 Eclipse > Help > Install New Software > Add > \href{http://update.eclemma.org/}{\underline{http://update.eclemma.org/}};
- 安裝完後重新啟動 Eclipse，會看到 tool bar 上有一個多了一個 button，如 Figure \ref{fig:eclemma_icon};
- 撰寫程式及其相關的 JUnit 測試碼;
- 點擊 EclEmma，會執行 JUnit 並呈現涵蓋狀況。


FIG: Eclemma 圖示

<img src="img/sqa/Eclemma_icon.png" width="500">


圖 \ref{fig:eclemma_demo} 為EclEmma 跑出來的樣子：綠色表示該敘述有被完全執行、黃色表示部分、紅色表示尚未執行。Eclemma 採取的是*條件涵蓋度} conditional coverage，如果條件涵蓋度不為百分百，你會發現該行是標記為黃色。例如執行到 if (x>0) 這個指令，如果你的測試碼只有 x=10, 則該行就會標記為黃色，即便你的敘述涵蓋度已經是百分百。如果再加上 x=-10 的測試碼，則條件涵蓋度為百分百就回呈現綠色。使用時，你可以將游標移到程式碼左方的菱形上，它會出現你所檢核過的狀況。

FIG: Eclemma 程式碼涵蓋工具
<img src="img/sqa/Eclemma_demo.png" width="500">

```
*動手實驗：* 針對以下的程式（xAdd() 絕對值相加），撰寫 JUnit 測試碼。變化你的測試碼來觀察涵蓋度的變化\footnote{這個程式埋了一小錯誤}。

```java
public int xAdd(int x, int y)  {
   if (x<0 && y<0) 
      return -1*(x+y);
   if (x<0 & y<0) 
      return -1*(x+y);
   if (x< 0) 
      return -1*x+y;   
   if (y< 0) 
      return -1*x+y;         
   retrun x+y;      
}
```


> 一些工具使用上的注意事項：(1) 如果你的測試碼和程式碼放在同一個 src 目錄，你會發現測試涵蓋度的計算也會包含你的測試碼，你可以建立另一個 test\_src 的目錄來解決這個問題; (2) 使用 EclEmma 時，breakpoint 等除錯工具建議先 disable (3) 每次執行後清除EclEmma 的 session 會讓涵蓋度比較清楚些。


## 基本路徑測試


基本路徑測試（basis path testing） 白箱測試常見的方法，用以達成百分百敘述涵蓋度與分支涵蓋度。


> 輸入100個以下的學生人數之成績，成績限定在0～100分的範圍，計算所有學生成績的總和sum、有效輸入學生成績個數valid，以及平均成績 average。
輸入-999表示停止輸入。若valid=0，則 average=-999。


FIG: average() 程式碼
<img src="img/whitebox/average.png" width="500">

%
%```java 
%  public class Test {
%     int sum, valid, min=0, max=100, input, average;
%     public void average(int [] value) {
%(1)       input = valid=sum=0; 
%(2)(3)   while (value[input]!=-999  && input<100  ) {              
%(4)(5)       if  (value[input]>=min && value[input]<=max) {
%(6)                 valid++;
%                      sum = sum + value[input];
%                 } //end if
%(7)            input++;
%(8)        } // end while   
%(9)       if (valid >0) {
%(10)          average = sum/valid;
%            }
%            else { 
%(11)          average = -999;
%            } //end if
%       }//end average()
%  }//end class    
%```



#### Step 1. 繪製流程圖} 在這個階段，通常此方法會把所有的複合條件拆解成單一條件，例如 if (x \&\& y) 要拆成 if (x) .... if (y) ... 的結構。當我們把複合條件拆解後，基本路徑測試可以達到百分百條件涵蓋度。

#### Step 2. 計算迥圈複雜度} Cyclomatic Complexity 代表程式在條件判斷的複雜度，CC 越高，表示我們需要測試的路徑越多。計算方法為：

> CC(G) = 區域空間個數=邊的個數-節點個數+2=判斷節點個數 +1 

其中區域空間表示被區隔開的獨立空間，在圖 \ref{fig_program_graph} 中，例如點 2-3-9 所包覆的空間、9-11-10-12、4-7-5、5-7-6, 2-3-4-5-6-7-8 等及外部的空間等共六個區域空間。或是用判斷節點來計算：2,3,4,5,9 都是判斷節點，5+1 = 6 一樣是六個區域空間。

\ifWide \clearpage \fi
\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{img/sqa/basis_path.png}
FIG: *average()} 流程圖}
\label{fig_program_graph}

<img src="" width="500">

#### Step 3. 尋找基本路徑
找出一組基本獨立路徑，數量為 6。首先，任選一個路徑作為 path1, 接著建立 path 2 不要走 path1已經走過的路徑。依此類推。

```java
Pathl: 1-2-9-10-12
Path2: 1-2-9-11-12
Path3: 1-2-3-9-10-12
Path4: 1-2-3-4-7-8-2-…
Path5: 1-2-3-4-5-7-8-2-…
Path6: 1-2-3-4-5-6-7-8-2-…
```

路徑後省略(…)表示可接受任何路徑。迥圈複雜性為 6 表示獨立路徑最多就是 6, 所以你不需要再往下找下去，最多就是六個路徑。

#### Step 5. 設計測試案例} 
接著我們開始找相關的測試資料來滿足這些測試路徑。


- Path l 測試案例: 1-2-9-10-12。value(1) =-999，所以valid=0，無法進入10。path1不能被單獨測試，須為路徑4，5，6測試中的一部份。

- Path 2 測試案例: 1-2-9-11-12。Value(1)=-999。期望輸出:  average =-999; sum =0。

- Path 3 測試案例: 1-2-3-9-10-12。嘗試處理第101或更多的值,而其中前100個值應該是有效的。
期望輸出: average =-999。

- Path 4 測試案例: 1-2-3-4-7-8-2-…。Value(i) =有效輸入且 i<l00。Value(R) <最小值，R<=i，R是其中一個輸入索引。期望輸出:正確平均值和總數。

- Path 5 測試案例: 1-2-3-4-5-7-8-2-…。Value(i) =有效輸入i<l00。Value(R)>最大值R<=i，R是其中一個輸入索引。期望輸出:正確平均值和總數。

- Path 6 測試案例: 1-2-3-4-5-6-7-8-2- …。Value(i) =有效輸入i<l00。期望輸出:基於i個數值的正確平均數和總數。執行每個測試案例，並與期望輸出比較。完成所有測試案例後，保證程式中所有敘述都至少被執行一次。

由於基本路徑測試把 branch 內的 condition 都拆開來，且確保每一個 condition 的真假都有成立過，所以可以滿足分支涵蓋度與條件涵蓋度。
    
## 資料流測試}

%```java[number=left]
% read (x, y); 
% z=x+2; 
% if(z<y) 
%    w = x + 1;
% else 
%    y = y + 1;
% print (x, y, w, z);
%```

資料流測試（data flow testing）著眼在變數的定義與使用測試。從資料流的角度檢視程式是否異常的角度來進行測試案例的設計。從一個變數被定義到被使用的路徑應該測試，*開始有了「路徑」的概念}。


- (d) defined: 資料被定義、建立、初始化。當資料被給定新值、檔案被打開、或動態的分配空間等。
- (k) killed: 資料被刪除、釋放。
- (u) used: 資料被利用。又可分為 (c) calculation 計算利用; 又稱為 c-used。(p) predicate; 又稱為 p-used 判斷利用。

當變數出現在一個 assignment 敘述的右方，例如 m = x + 1; 對變數 x 而言此敘述為其 c-used，因為它被拿來計算利用了。若變數出現在一個判斷中，例如 x==2，則是其 p-used。

\begin{table}[h]
\begin{center}
\begin{tabular}{|l|c|c|c|}
\hline
  & Def & C-use   & P-use \\ \hline
1.  read (x, y); & x, y &         &       \\ \hline
2.  z = x+2; & z   & x       &       \\ \hline
3.  if (z<y) &     &         & z, y   \\ \hline
4.      \quad w = x + 1; & w   & x       &       \\ \hline
5.  else &     &         &       \\ \hline
6.      \quad y = y + 1;& y   & y       &       \\ \hline
7.  print (x, y, w, z); &     & x, y, z, w &       \\ \hline
\end{tabular}

\end{table}

%簡易路徑片段 Simple path segment：最多一個點被拜訪兩次，例如： (7,4,5,6,7) , (10,11,4,5,6,7,8,10,11,12)

%無迴圈簡易路徑片段 Loop-free path segment: 沒有點被拜訪兩次：例如： (4,5,6,7,8,10) 

%**def-use} pair}: 一個 def-use 對可以定義為 (x,d,u)，其中 x 是變數、d 是一個包含 x 定義的點、u 是一個使用 x 的點。而且 (1) d 到 u 存在一個路徑 (2) 路徑中沒有其他的 x 定義。

%x 的 du 路徑：1-2; 1-4; 1-7。y 的 du 路徑：1-3; 1-7; 6-7。z 的 du 路徑：2-3; 2-7。




- *全定義 (all def) 資料流測試}：對於所有的變數的定義，都應該有一個路徑從定義到使用（p-use 或 c-use）走過。%To achieve 100% All-definitions data flow coverage, At least one sub-path from each variable definition to some use of that definition (either p-use and c-use) must be executed. 

以上表的 x 為例，應該要有一組測試資料通過 (1,2)。其他的 def 還包含：y: (1,6), z: (2, 7), w: (4, 7), y: (6, 7)。

- *全計算利用 (all c-uses) 資料流測試}：對於所有變數的計算利用（c-use），都應該至少有一個路徑（從定義到計算使用）走過。%To achieve 100%  All-c-uses data flow coverage at least one sub-path from each variable definition to every c-use of that definition must be executed. 

以上表的 x 為例，應該要有一組測試資料通過 (1,2), (1,4), (1,7) 。


- *全判斷利用 (all p-uses) 資料流測試}:  對於所有變數的判斷利用（p-use），都應該至少有一個路徑（從定義到判斷利用）走過。%To achieve 100% All-p-uses data flow coverage At least one sub-path from each variable definition to every p-use of that definition must be executed. 

以上表的 x 為例，因為 x 沒有 p-use, 所以不用相關的測試案例。

- *全定義-使用 (all-du) 資料流測試}: 針對每一個變數，其每一個變數定義 (def) 到每一個變數利用 (use) 的 du 路徑，都有測試案例通過。這是資料流測試中最完備的一種測試策略，當然其花費的成本也最高。

以上表的 x 為例，應該要有一組測試資料通過 (1,2), (1,4), (1,7)。



\ifWide \clearpage \fi
\begin{figure}[h!]
\begin{center}
\includegraphics[width=.8\columnwidth]{img/whitebox/du_compare.png}
FIG: 各種資料流涵蓋度示意圖 (變數 Y)}
\label{fig:du_compare}

<img src="" width="500">


\ifWide \clearpage \fi
```
針對以下程式中的X, 設計測試案例使之達到 all-du 的百分百涵蓋度。
```java
read (X, Y)
if ((X>10) || (Y==1))
   X=1;
else if ((X+Y) > 10)
  X=2;
if (Y >10)
   X=3; 
print x
```
```

先列出所有的 X-def: 01, 03, 05, 07。所有的X-use：02, 04, 08。因為是 all-du 的涵蓋度，所以必須經過以下的 du pair: (01, 02), (01, 04), (01,08), (03, 04), (03, 08), (05, 07), (05, 08), (07, 08)。有些路徑是不可能通過的，例如 (03,04)。


- du$_{(01,02)}$: (11, 1)
- du$_{(01,04)}$: (9, 2)
- du$_{(01,08)}$: (9, -2)。注意這個測試案例不會通過 03, 05, 07 等 X-def。
- du$_{(03,04)}$: 無此可能。
- du$_{(03,08)}$: (11, 1)
- du$_{(05,07)}$: (9, 2)
- du$_{(07,08)}$: (2, 11)

所以我們可以設計測試案例 {(11,1), (9,2), (9,-2), (11,1), (2,11)} 來滿足這個需求。

### 資料流測試涵蓋度}

:question: 若分支涵蓋度為百分百，則資料流測試涵蓋度 $du$ 也會百分百嗎？}

\ifWide \clearpage \fi

以以下的例子做思考

```java [numbers=left]
 read (x, y);
 if (p)
    x++;
 else 
    print (y);
 if (q)
    print y;
 else
    y = x + 1;
  print (x, y);                 
```

當 (p,q) = (t,t), (f,f)  branch coverage 已經 100%，但 x 的 du path 並沒有通過(3, 9)。

### 工具}

- \href{https://github.com/saeg/ba-dua}{ba-dua}, ba-dua (Bitwise Algorithm - powered Definition-Use Association coverage) is an intra-procedural data-flow testing tool for Java programs.

## 變異測試}
變異測試是一個很有趣的方法，它並不是真的測試程式碼或系統規格，而是測試「測試資料。當我們的測試資料太少或是不夠尖銳時，它是無法找出程式的錯誤的。

%Mutation testing introduces faults into software by creating many different versions of the program.Each version has one very small change (which introduces a fault) compared to the actual implementation.
%The idea is to see if the test cases that were written can detect the new fault.Mutation testing is a way to measure the quality of a test suite.

\begin{figure}[t]
\begin{center}
\includegraphics[width=.5\columnwidth]{img/sqa/mutation.png}
FIG: Mutation}
\label{fig_mutation}

<img src="" width="500">

圖 \ref{fig_mutation} 說明變異測試的概念。T 為測試 P 的測試資料。我們將 P 做一些微幅修改後產生數個變異體（mutant）$P^{'}$, $P^{''}$, $P^{'''}$ 與 $P^{''''}$。如果 T 無法區分 $P$ 與變異體的輸出差異，則 T 無效，必須更換或是新增。


### 變異

所謂的變異指的是受測程式的微幅修改。例如把部分的 = 改成 != 或是 > 改成 <，如果*連這樣的錯誤測試資料都無法偵查處理，表示此資料是不夠的}。修改程式的運算元（operator）我們稱為 變異運算元（mutation operator），例如：


- 把某些判斷句換成 true, false, 或加上 not
- 把 + 換成 *, - 換成 /
- 把 > 換成 >=, == 或是 !=
- 把某些運算作為幅的修改，例如 x 變成 x+1, y 換成 y-1

例如，原程式為：

```java
int getMax(int x, int y) {
   int max;   
   if (x>y) max =x;
   else max = y;
   return max;
}
```

變異後的為：

```java
int getMax2(int x, int y) {
   int max;   
   if (x<y) max =x;
   else max = y;
   return max;
}
```

假設你只有一組測試資料 (1,1), 則在 getMax() 與 getMax2() 執行出來的結果都是一樣的，代表測試資料不足。

### 作法}


- 產生程式 $P$ 的變異群，$P^m=\left\{P_1, P_2, P_i, ... P_n\right\}$; 
- $T$ 為測試資料集合，$T = \left\{t_1, t_2, ... t_m\right\}$;  
- 用 $T$ 來測試 $P$ 及 $P^m$ 內的每個程式，當 $\exists t_i \in T, P(t_i) \neq P_j(t_i)$ 時，表示 $t_i$ 可以識別出兩者的差異，此時 $P_j$ 被移除，稱之為被刪除變異體（killed mutant），沒有被移除的稱之為存活變異體（alive mutant）。
- 如果剩下的 存活變異體 不是等價變異，則增加測試案例。
- 回到步驟 3，直到 存活變異體 為空。



\ifWide \clearpage \fi
:question: 考慮以下的程式 *P}。若我們有兩個變異 $P_1$ 是把 \&\&  改成 || , $P_2$ 是把 == 改成 != ，請問 test case (x=10, y=10) 能夠 kill 哪些變異？其所代表的涵意為何？}

```java
read(X, Y)
if ((X>=10) && (Y==1))
   X=1;
else if ((X-Y) < 2)
   X=2;
if (Y >10)
   X=3;
print X
```

\ifWide \clearpage \fi
測試案例 (10, 10) 對原來 $P$ 的測試 $P(10,10)$ 產出的結果為 X=2, $P_1(10,10)$ 為 X=1，輸出的結果不同了，表示此測試案例能夠偵測出不同，故刪除（kill）$P_1$。$P_2(10,10)$ 結果仍然為 X= 2 保持不變，無法刪除 $P_2$。因此我們必須再加入測試案例。

例如我們加入 (10,1) 的測試案例，$P(10, 1)$ 為 1, $P_2(10, 1)$ 為2, 兩者不同，這時候我們可以刪除 $P_2$, 因為所有的變異都被移除，所以測試案例 OK。

### 變異刪除率}

變異刪除率 (mutation score) 用來檢視測試資料的完整度。

\[ ms=K/(M–E) \]

其中 K 是被刪除變異體的個數，E 是等價變異體的個數，M 是變異的個數。

變異刪除率越高，表示測試案例越有效。

> {
在變異測試這個遊戲中，我們的目的就是- 盡所能的（設計測試資料以）刪除變異。

### 等價變異}

有些變異後程式碼的行為是一樣的，所以不論測試資料多麼好，也無法觀察出差異進而刪除，例如：

```java{numbers=none}
var a, b, c: integer;
begin
     if a < b then c:= a; 
end

以下為三個變異：
p1: if a <= b-1 then c := a; 
p2: if a +1 <= b then c:= a; 
p3: if a < b then c:= a + 0;
```

$p_1$, $p_2$, $p_3$ 這三個變異都是等價變異，任何資料都無法將之刪除。

\ifWide \clearpage \fi
:question: 針對以下程式 P 及其變異，回答 (1) 哪些是 被刪除變異體? (2) 這些這是案例有效嗎？變異刪除率為何？(3) 承2, 如果測試案例不有效，請新增測試案例。 }

\begin{figure}[h!]
\begin{center}
\includegraphics[width=.7\columnwidth]{img/whitebox/mutationTest.png}
\label{fig_mutation_test}

<img src="" width="500">


\ifWide \clearpage \fi

在實務上，變異測試需要搭配工具才能使用，因為一個程式所產生出的變異體需要很多，這需要自動化的產生，而比對變異體的執行結果與原程式是否相異也需要透過系統自動檢查，才能發揮此方法的效益。


- \href{http://pitest.org/}{PIT mutation test}

%\ifEx \exerciseMargin \fi

\ifEx \newpage \fi
## 練習
 
### 測試涵蓋度}
- 下列何者為真？
	
	- 條件涵蓋度 為 100% 則 敘述涵蓋度 也必為 100%?
	- 100% 分支涵蓋度 則 條件涵蓋度 也為 100%
	- 100% 分支涵蓋度 則 敘述涵蓋度 也為 100%
	- 100% 多重條件涵蓋度 則 100% 分支涵蓋度
	
	
- 路徑涵蓋度(a)、多重條件涵蓋度(b)、分支涵蓋度(c)、分支與條件涵蓋度(d)、 敘述涵蓋度(e) 的嚴謹程度順序為何，請由寬鬆至嚴謹排列？	
	
- 請寫出一個 Binary Search 的程式，並設計一些測試案例使得 
	
	- 100% 敘述涵蓋度 
	- 100% 分支涵蓋度
	- 100% 條件涵蓋度
	
```java [numbers=left]
int binary_search(int A[], int key, int imin, int imax) {
  while (imin < imax)    {
       int imid = (int)floor((imin+imax)/2.0);
       assert(imid < imax);
       if (A[imid] < key)
           imin = imid + 1;
       else
           imax = imid;
   }
   if ((imax == imin) && (A[imin] == key))
        return imin;
   else
        return KEY_NOT_FOUND;
}
```	

	
- \label{ex:wb:code01} 針對以下程式 
	
```java[caption=Sample Code, label=ex:list:sample]
read(X, Y)
if ((X>10) && (Y==1))
   X=1;
else if ((X-Y) < 2)
   X=2;
if (Y >10)
   X=3;
print X	
```

	
	- 設計一測試案例使得 敘述涵蓋度 (SC) 為100%; 
	- 設計一測試案例使得 條件涵蓋度 (CC) 為 100%, 但 分支涵蓋度 (BC) 不為 100% 
	- 設計一測試案例使得 CC=100% , BC<>100% 
	- 設計一測試案例使得 CC=BC=100%
		
	
- 針對以下程式，設計測試案例，以達到最佳的分支包含度。
```java
if (height > 2 || height <= 1) 
   return -1;
if (weight > 100 || weight <= 40) 
   return -2;
double BMI = weight /(height*height);
if (BMI > 120) return -3;
if (BMI < 15) return -4;
return BMI;
```	



### Eclemma

- 以下何者為真（多選）
	
	- Eclemma 需搭配 JUnit 一起使用;
	- 執行後受測碼會出現三種顏色，其中紅色表示程式沒有通過測試，必須除錯;
	- 在一個非判斷敘述中句出現黃色，表示該敘述沒有被執行過;
	- 在一個判斷敘述句中出現黃色，表示該判斷沒有達到百分百分支涵蓋度或條件涵蓋度;
	- 只要小心且充分的設計測試案例，一定可以達到受測碼全部綠色。
	

-  寫一個程式判斷三角形，並寫一點 JUnit 測試碼，執行測試時，改以 EclEmma 來測試此程式。EclEmma 會標示你沒有測試到的部份，這時候在加上 JUnit 測試碼，逐步提高測試率。

- 寫一個程式來依據 BMI 檢驗體重是否過重。BMI = 體重 (kg) / 身高 (m2)。其分級如下：
	  
	- 體重過輕 BMI ＜ 18.5 
	- 正常範圍 18.5 <= BMI ＜24 
	- 過重 24 <= BMI ＜ 27 
	- 輕度肥胖 27 <= BMI ＜ 30 
	- 中度肥胖 30 <= BMI ＜ 35 
	- 重度肥胖 BMI >= 35 

請用 EclEmma 來測試。



- 以下是一個最短路徑的程式，請改以 JUnit 的方式來測試它，並提昇包含度。\href{https://github.com/nlhsueh/sqa/blob/master/src/junitdemo/Dijkstra.java}{\underline{Dijkstra program}}。

- 以下是 infix 的程式，請改以 JUnit 的方式來測試它，並提昇包含度。\href{https://github.com/nlhsueh/sqa/blob/master/src/junitdemo/Infix.java}{\underline{Infix program}}。

### 基本路徑測試

- 以下何者為真（選三）
	
		- 繪製流程圖時，複合條件必須分解為單一條件;
		- 程式中的邏輯判斷越多，計算迥圈複雜度 (CC) 的值越高;
		- CC 為 n, 表示至少需要 n 個測試案例;
		- 若一個程式都沒有判斷敘述句，則其 CC 為 0;
		- 基本路徑測試要求分支涵蓋度百分百。
	

- 請描述 basis path testing 的步驟

- 何謂獨立路徑（independent path）？

- 何謂 cyclomatic complexity? 它在 basis path testing 的意義為何？

- 請寫出一個 selection sort 的程式，進行 basis path testing 的設計。

- \label{ex:nextDate} 針對程式 \ref{ex:list:nextDate}，利用 basis path testing 的方式設計測試案例。

	
	- Cyclomatic complexity 為何
	- Independent path 為何？
	- 設計測試案例
		 
	
```java [numbers=left, caption=nextDate(), label=ex:list:nextDate]
  nextDate(): 
  read(m, d);
  if (d == 28) {
      if (m == 2) {
         m++;
         d = 1;
      }
      else d++;   
  }
  else if (d == 30) {
     if (m == 4 or 6 or 9 or 11) {
         m++;
         d=1;
     }   
     else d++;
  }
  else if (d == 31) {
     if (m == 1 or 3 or 5 or 7 or 8 or 10) {
        d=1;
        m++;
     } 
     else if (m == 12) {
        d=1; m=1;
     }     
  }
  else d++;
  print (m, d);
}
```


### 資料流測試}

- 關於資料流測試，以下何者為錯（選一）：
	
	- 著重在資料變數定義、計算、與判斷之間的關係; 
	- if (x>10) 是一種對 x 變數的 p-use; 
	- 全判斷利用測試 (all p-use) 的測試資料必定包含全計算測試 (all c-use) 的測試資料; 
	- 全使用資料流測試 (all du) 是資料流測試中最完整的測試方法。
	
	
- 何謂 資料流測試? 

- 請寫出一個 selection sort 的程式，進行 all p-use 資料流測試。

- 針對程式 \ref{ex:list:sample} 程式的變數 X ，設計一群測試案例，使得百分百 all-use 涵蓋度。


- 同 Ex\ref{ex:nextDate}，針對 nextDate() 進行資料流測試：
	
	- All definition testing 
	- All c-use testing
	

### 變異測試}

- 關於變異測試，何者正確 
	
	- 存活變異體 (alive mutant) 越多，表示該測試案例集越有效;
	- 已刪除變異體 (killed mutant) 表示該程式是一個有錯誤的程式;
	- 「變異刪除率」用來計算程式的品質;
	-  變異運算元（mutation operator）用來修改測試碼;
	- 變異主要目的在自動化產生測試案例;
	

- 回答以下問題：
	
	-  何謂變異體? 何謂等價變異體？
	-  已刪除變異體 (killed mutant) 的含意為何？存活變異體 (alive mutant) 的含意為何？ 
	- 說明變異測試的流程 
	-  刪除變異率的定義為何？所代表的含意為何？
	- 舉出三個變異運算元	
		


- 以下 P2 為 P的 mutant, 請問兩者是否等價？
```java
//P
int index=0;
while (…) {
  … ;
  index++;
  if (index==10)
    break;
}

//P2
int index=0;
while (…) {
  … ;
  index++;
  if (index>=10)
    break;
}
```

- 針對程式 \ref{ex:list:sample}，我們採用 mutation test 的方式來檢驗測試案例，假設我們產生兩個變異：P1 是把  \&\& 改成 || (or), P2 是把 == 改成 >= ，請問 test case (x=1, y=1) 能夠 kill 哪些變異？其所代表的涵意為何？




### 綜合
- 以下何者為真
	
	- 應用 Eclemma 來進行測試是屬於黑箱測試
	- 如果 100% branch coverage 且結果都正確, 則保證程式的功能都正確了
	- 按照 basic path testing 的方法所設計出的測試案例會達到 100% branch coverage 和 100% condition coverage
	- mutation test 並不是一種測試方法，它是一種檢驗測試案例的方法
- 在實務上，mutation 一定要工具輔助才有功效
	



\myquote{\JokeIcon}{
我是一個程式，一天我坐在路邊一邊喝水一邊苦苦檢查bug，這時一個乞丐在我邊上坐下了，開始要飯，我覺得他可憐，就給了他一塊錢，然後接著改程式。他可能生意不好，就無聊的看看我在幹什麽，然後過了一會，他幽幽說，這裏少了一個分號。\\ \\
我驚奇的問：“你也懂這行啊” \\ \\  乞丐說：“我以前就是做這個的。”

%> {
%除錯，是喚醒沉睡錯誤的儀式。
%

%> {
%除三個錯就會冒出一個錯。這稱為 bug 的無窮迴圈。
%

\ifEx \originalMargin \fi

