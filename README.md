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

### Public Best LB Score: 0.574

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
      PREDICT_BATCH = 32    LB: 0.574    ver1
      PREDICT_BATCH = 64    LB: 0.573    ver2
      PREDICT_BATCH = 128   LB: 0.574    ver5
      PREDICT_BATCH = 256   LB: 0.574    ver6
      PREDICT_BATCH = 512   LB: 0.573    ver7
    
-------

