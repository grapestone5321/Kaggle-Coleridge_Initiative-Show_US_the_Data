# Kaggle-Coleridge_Initiative-Show_US_the_Data
Kaggle-Coleridge_Initiative-Show_US_the_Data


-------

## Final Submission Deadline.

June 22, 2021 at 11:59 PM UTC

-------

## Evaluation

The objective of the competition is to identify the mention of datasets within scientific publications. 

Your predictions will be short excerpts from the publications that appear to note a dataset.

Submissions are evaluated on a Jaccard-based FBeta score between predicted texts and ground truth texts, with Beta = 0.5 (a micro F0.5 score). 

Multiple predictions are delineated with a pipe (|) character in the submission file.

The following is Python code for calculating the Jaccard score for a single prediction string against a single ground truth string. 

Note that the overall score for a sample uses Jaccard to compare multiple ground truth and prediction strings that are pipe-delimited - this code does not handle that process or the final micro F-beta calculation.

      def jaccard(str1, str2): 
          a = set(str1.lower().split()) 
          b = set(str2.lower().split())
          c = a.intersection(b)
          return float(len(c)) / (len(a) + len(b) - len(c))

Note that ALL ground truth texts have been cleaned for matching purposes using the following code:

      def clean_text(txt):
          return re.sub('[^A-Za-z0-9]+', ' ', str(txt).lower())

For each publication's set of predictions, a token-based Jaccard score is calculated for each potential prediction / ground truth pair. 

The prediction with the highest score for a given ground truth is matched with that ground truth.

- Predicted strings for each publication are sorted alphabetically and processed in that order. Any scoring ties are resolved on the basis of that sort.

- Any matched predictions where the Jaccard score meets or exceeds the threshold of 0.5 are counted as true positives (TP), the remainder as false positives (FP).

- Any unmatched predictions are counted as false positives (FP).

- Any ground truths with no nearest predictions are counted as false negatives (FN).

All TP, FP and FN across all samples are used to calculate a final micro F0.5 score. 

(Note that a micro F score does precisely this, creating one pool of TP, FP and FN that is used to calculate a score for the entire set of predictions.)



### Jaccard-based FBeta 
https://en.wikipedia.org/wiki/Jaccard_index



-------

## Task

This competition will build just such an open and transparent approach. 

The results will show how public data are being used in science and help the government make wiser, more transparent public investments. 

It will help move researchers and governments from using ad-hoc methods to automated ways of finding out what datasets are being used to solve problems, what measures are being generated, and which researchers are the experts. 

Previous competitions have shown that it is possible to develop algorithms to automate the search and discovery of references to data. 

Now, we want the Kaggle community to develop the best approaches to identify critical datasets used in scientific publications.


In this competition, you'll use natural language processing (NLP) to automate the discovery of how scientific data are referenced in publications. 

Utilizing the full text of scientific publications from numerous research areas gathered from CHORUS publisher members and other sources, you'll identify data sets that the publications' authors used in their work.

The objective of the competition is to identify the mention of datasets within scientific publications. 

Your predictions will be short excerpts from the publications that appear to note a dataset.



### CHORUS 
https://www.chorusaccess.org/

-------

## Coleridge Initiative
https://coleridgeinitiative.org/


      The Coleridge Initiative is a not-for-profit organization, originally established at New York University, 
      that is working with governments to ensure that data are more effectively used for public decision-making. 
      We achieve this goal by working with government agencies to create value for the taxpayer from the careful 
      use of data, by building new technologies to enable secure access to and sharing of confidential microdata, 
      and by training agency staff to acquire modern data skills.



-------

## Resources


### Coleridge Data Examples
https://coleridgeinitiative.org/data-products/

### Rich Search and Discovery for Research Datasets
https://study.sagepub.com/richcontext

### Democratizing Our Data
https://mitpress.mit.edu/books/democratizing-our-data

### NSF"Rich Context" Video
https://www.youtube.com/watch?v=PIReIlsTI8U


-------

## Website

## Jaccard-based FBeta
https://en.wikipedia.org/wiki/Jaccard_index

-------

## Progress

### Public Best LB Score: 0.585

### Private Score: 





-------

## Coleridge Initiative-EDA📚 & Baseline Model
https://www.kaggle.com/prashansdixit/coleridge-initiative-eda-baseline-model


      Public Score 0.534




-------

## Loading Data, EDA
https://www.kaggle.com/mohamedbakrey/loading-data-eda

      Public Score 0.527

-------

## Brt MLM
https://www.kaggle.com/suryadeepti/0-573-mask-modeling

      Public Score 0.574
      
### PREDICT_BATCH:

      PREDICT_BATCH = 8     LB: error    ver4
      PREDICT_BATCH = 16    LB: error    ver3
      PREDICT_BATCH = 32    LB: 0.574    ver1     --- default
      PREDICT_BATCH = 64    LB: 0.573    ver2
      PREDICT_BATCH = 128   LB: 0.574    ver5
      PREDICT_BATCH = 256   LB: 0.574    ver6
      PREDICT_BATCH = 512   LB: 0.573    ver7


### MAX_LENGTH = 64
PREDICT_BATCH = 32:

      MAX_LENGTH = 16      LB: 0.572    ver9
      
      MAX_LENGTH = 31      LB: 0.574    ver17
      MAX_LENGTH = 30      LB: 0.574    ver18
      MAX_LENGTH = 29      LB: 0.574    ver19
      MAX_LENGTH = 28      LB: 0.576    ver20
      MAX_LENGTH = 24      LB: 0.572    ver21
    
      MAX_LENGTH = 32      LB: 0.576    ver8     --- (Best)      
      MAX_LENGTH = 36      LB: 0.574    ver12
      MAX_LENGTH = 40      LB: 0.574    ver13
      MAX_LENGTH = 48      LB: 0.573    ver14
      MAX_LENGTH = 56      LB: 0.574    ver15
      MAX_LENGTH = 60      LB: 0.573    ver16            
      MAX_LENGTH = 64      LB: 0.574    ver1     --- default
      MAX_LENGTH = 128     LB: 0.573    ver10
      MAX_LENGTH = 256     LB: error    ver11
    
MAX_LENGTH = 32:

      OVERLAP = 20        LB: 0.576    ver8     --- (Best)    
      OVERLAP = 21        LB: 0.575    ver22
      OVERLAP = 22        LB: 0.574    ver23
      OVERLAP = 23        LB: 0.574    ver24
      OVERLAP = 19        LB: 0.574    ver25
      OVERLAP = 18        LB: 0.575    ver26 

OVERLAP = 20：

      adnl_govt_labels_path = '..//data_set_800.csv'        LB: 0.576    ver8     --- (Best)  
      adnl_govt_labels_path = '..//data_set_26897.csv'      LB: 0.244    ver28

      adnl_govt_labels = pd.read_csv(adnl_govt_labels_path)      LB: 0.244   ver28
      adnl_govt_labels = df_data10000                            LB: 0.271   ver29
      adnl_govt_labels = df_data16897                            LB: 0.047   ver30
      adnl_govt_labels = df_datahead5000                         LB: 0.271   ver32
      adnl_govt_labels = df_datatail5000                         LB: 0.047   ver33


### def compute_fbeta(y_true: 

      beta: float = 0.5) -> float:           LB: 0.576    ver8     --- (Best)  --- defalt
      beta: float = 0.6) -> float:           LB: 0.576    ver34 
      beta: float = 0.7) -> float:           LB: 0.576    ver35
      beta: float = 0.8) -> float:           LB: 0.576    ver36 
      beta: float = 0.4) -> float:           LB: 0.576    ver37 
      beta: float = 0.3) -> float:           LB: 0.576    ver38 
                  

### SEED:

      SEED = 42          LB: 0.576    ver8     --- (Best)  --- defalt
      SEED = 100         LB: 0.576    ver39    
      SEED = 500         LB: 0.576    ver40     
      SEED = 1000        LB: 0.576    ver41     
      SEED = 1500        LB: 0.576    ver42     
      SEED = 2000        LB: 0.576    ver43     



### for label in sorted(pred_bag, key=len, reverse=True):

      got_label) < 0.60 for got_label in filtered_labels):          LB: 0.576    ver46
      got_label) < 0.65 for got_label in filtered_labels):          LB: 0.576    ver45
      got_label) < 0.70 for got_label in filtered_labels):          LB: 0.576    ver44      
      got_label) < 0.75 for got_label in filtered_labels):          LB: 0.576    ver8      --- (Best)  --- defalt
      got_label) < 0.80 for got_label in filtered_labels):          LB: 0.576    ver47
      got_label) < 0.85 for got_label in filtered_labels):          LB: 0.575    ver48



### if not MATCH_ONLY:

      PRETRAINED_PATH = '/checkpoint-60000':           LB: 0.576    ver8      --- (Best)  --- defalt   
      PRETRAINED_PATH = '/checkpoint-48000':           LB: 0.576    ver50
      PRETRAINED_PATH = '/checkpoint-36000':           LB: 0.575    ver51
      PRETRAINED_PATH = '/checkpoint-24000':           LB: 0.574    ver52
      PRETRAINED_PATH = '/checkpoint-12000':           LB: 0.570    ver53

      BS_CLEANING = False:             LB: 0.576    ver8       --- (Best)  --- defalt
      BS_CLEANING = True:              LB: 0.571    ver54


      adnl_govt_labels = df_data2300:           LB: 0.577    ver55
      adnl_govt_labels = df_data2000:           LB: 0.577    ver56
      adnl_govt_labels = df_data1800:           LB: 0.579    ver57
      adnl_govt_labels = df_data1500:           LB: 0.583    ver58
      adnl_govt_labels = df_data1000:           LB: 0.584    ver59 
      adnl_govt_labels = df_data900:            LB: 0.585    ver60
      adnl_govt_labels = df_data700:            LB: 0.585    ver61      --- Best
      adnl_govt_labels = df_data500:            LB: 0.585    ver62
      adnl_govt_labels = df_data300:            LB: 0.585    ver63
      adnl_govt_labels = df_data100:            LB: 0.441    ver64
      
-------

