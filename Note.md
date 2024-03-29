# Bert_Elmo_Gpt2_notebook
#[ELMO] Embeddings from Language Model#-   Red<br />
RNN base:蒐集一對句子,不用標註,可以訓練出!<br />
RNN去預測下一個token<br />
上下文不同吐給RNN,出來的RNN就不同<br />
輸出時讀完再輸出Embedding<br />
ELMO會去考慮前後文<br />
<br />
train deep : 每層都有embedding,ELMO全都要<br />
所以把每層embeddings全部加起來<br />
第一層a1 +第二層a2 = 新的<br />
a1,a2 : learn出來的<br />
不同任務用的a1,a2都不一樣<br />
<br />
SRL Coref SNLI SQuAD SST-5<br />
<br />
***
#[BERT] Bidirectional Encoder Representations from Transformers#-   Red<br />

BERT的裡面不是RNN而是transformer Encoder<br />
蒐集一堆句子即可訓練<br />

##1. 給一個句子進去,每個句子都會吐一個embedding出來 再 給Linear##<br />

##BERT用字當單位比用詞當單位好##<br />

##2. 給兩個句子,是要被接再一起的##<br />
##中間給個boundary [SEP]##<br />
##前面放一個特殊token[CLS]##<br />

#如何使用BERT#<br />

##1. input句子 output CLS:##<br />
##要分類句子丟給BERT##<br />
##開頭標好CLS, 丟給 Linear ##<br />
 ##(小BERT 24層;大的48層)##<br />
##BERT跟LinearCLS同時訓練##<br />
<br />

##2. input 句子 output每個詞回是屬於哪一個cls##<br />
##進去句子的每個詞彙都會有一個embeddings##<br />
##丟給每個LinearCLS來去決定是屬於哪個cls##<br />
<br />

##3. input兩個句子output一個cls##<br />
##根據前提,這是對還是錯!##<br />
##給兩個句子,句子之間加入[SEP],開頭給[CLS]輸出embedding到Linear Cls決定是T/F##<br />
<br />

##4. 解決 E.g.SQuAD  Extraction-based Question Answering(QA)##<br />
##讀一篇文章,問一個問題希望可以答對正確答案(文章裡面必須要有答案)##<br />

##input 文章 問題##<br />
##D 文章 ----- Model = s ##<br />
##Q 問題 ----- Model = e##<br />
##A 答案 -----             答案位置##<br />
##文章每個詞彙都會有embedding ---- ##<br />
##softmax 每個詞彙有一個分數##
<br />

##POS 詞性標記 文法剖析會需要BERT前幾層(11)##<br />
<br />
***
#[GPT] Generative Pre-Training#-   Red<br />
transformer decoder<br />
<br />
##給辭彙,預測接下來的詞彙##<br />
<br />
##可以做Zero-shot Learning## <br />
##給一篇文章,一個問題------輸入A就會有答案##<br />
<br />
#摘要#<br />
##輸入英文句子1= 法文1##<br />
##輸入英文句子2= 法文2##<br />
##輸入英文句子3= 自動輸出法文3##<br />
<br />
##GPT2其他能力: 寫作、給一篇文章##<br />
