# MexEE 402: Data Preprocessing Case Study

MexEE Elective 2: Data Science and Machine Learning
Batangas State University, Alangilan Campus
1st Semester, AY 2026-2027

## Members

| Name | Student Number | Section |
|---|---|---|
| Dimaandal, John Edward |22-06340 |MEXE-4103 |
| Moraleda, John Rey | 22-07249|MEXE-4103 |

## Notebook links

| Chapter | Dimaandal| Moraleda |
|---|---|---|
| Ch1_2_3 | [https://colab.research.google.com/drive/1aJuALpFoAfKO-Crufdm-fUPx2UYR10Q5]() | [https://colab.research.google.com/drive/1MLyO5F1zA4r9TyHLHeuI1KfCWtfp54pK?usp=drive_link]() |
| Ch4 | [https://colab.research.google.com/drive/1Z1_4mnWFQ8eBWW4ii0F3CIY8ZGg5-fWm]() | [https://colab.research.google.com/drive/191q6mj10UKQKhiB4WT3HbvS_iXpo7jOu?usp=drive_link]() |
| Ch5 | [https://colab.research.google.com/drive/1duip0vj-F1bza3aaNazgen4K_PlNY8iF]() | [https://colab.research.google.com/drive/1GAWGDVixQj2JWpnV_g5RKJdXDLzH8VmT?usp=drive_link]() |
| Ch6 | [https://colab.research.google.com/drive/1_qtEMVIMXOYz-psBZqAZ_ao5Csahe3n_]() | [https://colab.research.google.com/drive/1bcii6t1oaM5eobVHg4iTKs83dNT8T0Sr?usp=drive_link]() |
| Ch7 | [https://colab.research.google.com/drive/1njvd_eyPOPCeGNiXe12zzDfFdUF3nsIb]() | [https://colab.research.google.com/drive/16fuOFh39IQmueUmK8RttE-A6CluNMSsd?usp=drive_link]() |
| Ch8 | [https://colab.research.google.com/drive/1uamMwUyPmoeUNmTeNzKSeV1R4qCwyi1Z]() | [https://colab.research.google.com/drive/1k0HtWlIxKVj5mXsGlm3hQq9U7Asl_aGi?usp=drive_link]() |
| Ch9 | [https://colab.research.google.com/drive/1ichR-ih-al-DJ0riPfNJ0q3e2P3Cbd45]() | [https://colab.research.google.com/drive/1fpKtNLUPShu1Pbwrz3ZY7okw9_EbOme-?usp=drive_link]() |

## What we learned

One short paragraph per chapter, Ch1_2_3 to Ch9. Say what the chapter taught
you and what surprised you. Not what the library does, but what you understood.

### Chapter 1-3

I learned that data preprocessing is an important step in preparing raw data for analysis because real-world data can be messy, incomplete, inconsistent, or contain unnecessary information. I learned how to understand a dataset, identify different types of data, and clean it by handling missing values, duplicates, irrelevant features, and noisy data. What surprised me was that even simple problems like duplicate or unnecessary data can affect the results, so properly cleaning and understanding the data is important before using it for further analysis.

### Chapter 4

I learned that feature engineering involves creating or transforming features to make the data more useful for analysis. I also learned about binning and encoding categorical values. What surprised me was that changing the way information is represented, such as using Little, Medium, and Lots as ordered values, can make the data more suitable for a model.

### Chapter 5

I learned that scaling makes features comparable so that features with larger numbers do not dominate the model. I also learned that scaling is not always necessary because it depends on the data and the algorithm. What surprised me was how much the difference in numerical ranges, such as Grades being much larger than Study Hours, can affect a model.

### Chapter 6

 I learned how outliers can be identified using methods such as Z-score and IQR. I understood that an unusual value does not automatically mean it should be removed because it may still contain useful information. What surprised me was that the value *100* stood out in the sample data even though its Z-score was only about 2.62.

### Chapter 7

I learned that feature selection helps keep only the features that are useful for prediction. I learned that different methods, such as Filter, RFECV, and LassoCV, can select different features from the same dataset. What surprised me was that there is not always one fixed set of “best” features because the selection can depend on the method used.

### Chapter 8

I learned that a preprocessing pipeline organizes several data preparation steps in a specific order, similar to a conveyor belt. I also understood how different columns can require different preprocessing. What surprised me was how a pipeline can make the whole preparation process more consistent and reduce the need to perform each step manually.

### Chapter 9

I learned that preprocessing can include handling missing values, grouping continuous values through discretization, and examining the processed data through plots. I understood that visualization can help reveal patterns that are difficult to notice from numbers alone. What surprised me was how preprocessing can change the way the data is viewed while still preserving useful information.

## Errors we found


A major problem in the original notebooks was how missing categorical data was handled. Mean and median imputation, which only work on numbers, were applied to text columns, which caused errors and wrong data types. The fix was to set up SimpleImputer with strategy='constant' and fill_value='missing' for the categorical columns only.

Another key problem was data leakage during feature scaling. The original code fitted tools like StandardScaler on the full dataset before splitting it into training and testing sets, so information from the test data could leak into training. The corrected version fits the scalers on the training data alone, using a ColumnTransformer pipeline.

The last problem was how categorical variables such as Embarked were encoded. Label encoding turned them into numbers, which wrongly suggested that S, C, and Q had an order or a mathematical relationship. The notebook now uses OneHotEncoder(handle_unknown='ignore'), which gives each category its own binary column so that no ranking is implied.

## Note on AI tools

Say whether you used an AI tool, and what for. This is not a penalty.
Hiding it is.

Throughout this notebook, AI tools (ChatGPT/Gemini) were used to support learning and to help with thinking.

- In some sections of the chapters we relied on AI because the description was too brief for us to fully understand the topic.
- We also used AI to correct an error in the notebook.

## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.
