# datasci_9_data_prep

## Dataset Descriptions
**First Dataset**
- The first dataset I utilized is [Crime Data from 2010 to 2019](https://catalog.data.gov/dataset/crime-data-from-2010-to-2019). It reflected criminal incidents from 2010 to 2019 in Los Angeles, California.
- The intended machine learning task for this dataset is classification. In classification models, the target variable is a categorical variable, I utilized the variable `vict sex` as it describes categorical information about the individual.
- The independent variables, predictors, are `DATE OCC, TIME OCC, AREA NAME, Crm Cd, Desc, Vict Age, Vict Descent, Premis Desc and Weapon Desc`.
- The dependent variable, or target variable, is `Vict Sex`. 

**Second Dataset**
- The second dataaset I utilized is [NCHS - Death rates and life expectancy at birth](https://catalog.data.gov/dataset/nchs-death-rates-and-life-expectancy-at-birth). The dataaset highlights the mortality trends in the United States starting from 1900; the dataset highlights the death rates and life expecatancy at birth by race and sex. 
- The intended machine learning task for this dataset is regression, as the target variable is continuous, `Average Life Expectancy (Years)`.
-  The independent variables, predictors, are `Year, Race, Sex, Age-adjusted Death Rate`.
-  The dependent variable, or target variable, is `Average Life Expectancy (Years)`.

## Data Cleaning and Transforming 
- To clean the data, I found, dropped, and replaced missing values by:
  
```
    missing_values = df.isnull().sum()
    missing_values
    df = df.fillna(0)
```

- To drop columns:
```
to_drop = [
    'type out the columns you would like to drop here,
]
df.drop(to_drop, axis=1, inplace=True, errors='ignore')
df.head()
```

 -  To transform the data I preformed encoding on categorical variables:

```     
 #perform orindal encoding on a category, ex) AREA NAME
enc = OrdinalEncoder()
enc.fit(df[['AREA NAME']])
df['AREA NAME'] = enc.transform(df[['AREA NAME']])

  #create dataframe with mapping
df_mapping_area = pd.DataFrame(enc.categories_[0], columns=['AREA NAME'])
df_mapping_area['area_name
```

  - `AREA NAME` can be switched out with other independent variables.

# Handling Errors
Unfortunately, I encountered a few issues when working on this assignment. I originally started the assignment by utilizing Google Cloud Shell, instead of Google Colab, as we did in class. I started with `model_dev_1` and created all my folders and files within the workspace, populated them with code, raw and processed datasets, models etc. Everything was going fine and accordingly, until I started the process of pushing my work onto Github before moving on to working on `model_dev_2`. I typically push work into my Github repo fairly often while working, however, because there were so many different parts to the `model_dev` folder, I thought to only push when that whole step is completed. When I went to push my work I recieved this message in the terminal: ![image](https://github.com/amnasyed1/datasci_9_data_prep/assets/123895397/b6c2c89e-f342-4f71-b831-92142d4a36e3)
I had not seen that message before when pushing my work, I had previously while working on past assignments had gotten error messages because I had added or changed a file/folder in the Github repo, and then tried pushing work from Shell into the repo. However, this was a different message, so I looked up what this meant and how I would be able to fix it, and it said the message meant the size of the things I was trying to push was too much and I would have to try to push things in smaller amounts. I tried `cd`ing into different folders to push only what was in those folders and divide up the load. Unfortunately, that did not work. Here is a screenshot of how the workspace looked: ![image](https://github.com/amnasyed1/datasci_9_data_prep/assets/123895397/56ffbad6-8642-477c-a58b-b947c23e9b60)

I then made a new repo, and tried copying and pasting my code into the new repo to push it in batches, to not overwhelm the system. But, even then I kept getting the same error. I tried several other simailar ways to, but nothing was working and I felt as if I was just going around in circles. I then remembered that Professor Hants mentioned in class that we could use Colab to data prep for machine learning. I then made the notebook, which can be seen above, and was able to do most of the things I was doing in Cloud Shell in there. I was able to push the scripts from Cloud Shell into github (in the new other repo I had made), which can be seen [here](https://github.com/amnasyed1/datasci_9_data_prep2/tree/main/model_dev_1/scripts). 
I am though grateful now, after everything that I did end up using Colab as well and it was successful on there, because now I know how to data prep for machine learning on Cloud Shell and Colab. Both are very different platforms, yet have many similarities, which made the process of switching over, and continuing the work pretty easy. 
