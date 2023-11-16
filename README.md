# Goal: Explore the application of unsupervised machine learning methods on emergency department (ED) visit narratives about older (age 65+) adult falls. Ultimately, insights gained through such analyses can help inform policies and interventions to reduce older adult falls.
## Summary of the approach:
### Data preparation
Primary data was used for the analysis. The data were mapped with their variable and then age, and sex were removed from the narrative. Two new columns were added to the primary data. The first one (narrrative_processed) is to translate the abbreviations in narrative and convert narrative to lowercase. The second column (big_narrative) helps the model understand that the fall has happened, and the narrative is the description.
### Model
Google Flan-T5 model was used for question-answering extraction from the big narrative. The model was optimized by adding batching and a torch. bfloat16. The model took 3.5 hours for primary data.
### Data processing
The processing steps for the answers were tokenization, removing stop words, and lemmatization. Lemmatization was optimized by adding batching and only took 45 minutes for all primary data. Processed data will make it easy for us to do the analysis.
After analyzing the results, the answers gave us a general idea about precepting events that happened before the fall, but it wasn’t clear enough for the analysis because there are different actions with different causes. The narrative column was unstructured.
It's better to perform separate iterations using the T5 model for each specific action. This approach will enable us to create personalized questions tailored to each action and obtain clear answers. After analyzing the narrative, trip and slip were selected for analysis.
### Exploratory Data Analysis (EDA)
The EDA was performed by using the top counts in each of the columns.

### References:
- https://www.drivendata.org/competitions/217/cdc-fall-narratives/community-code/13/ 
- https://www.drivendata.org/competitions/217/cdc-fall-narratives/community-code/52/
