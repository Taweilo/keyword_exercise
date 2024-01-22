# Keywords automation system 
<img src="https://nghenghiep.vieclam24h.vn/wp-content/uploads/2023/05/keyword-la-gi-1.jpg" >

## content
1. undersand business problem
2. understand the data
3. prepare data
4. explore data
5. modeling
6. download the CSV file as the end product
7. repetitively running the notebook with different CSV files as automation
   
```
├── Image                       
│
├── Keyword_simulation_notebooks.ipynb                <- code for automation
├── Keywords .csv                                     <- simulated dataset
├── Keywords_Automation_Process.ipynb                 <- code for simulated dataset generation
├── README.md                                         <- read me
```

## 1. understand business problem
To facilitate keyword selection based on key performance indicators (KPIs), an automated process can efficiently manage various CSV files using a consistent set of rules for exploration, evaluation, and keyword selection.

## 2. understand the data
- The dataset is simulated by the following code:
  
```
np.random.seed(42)

keywords = [
    "kids notebook",
    "plain paper",
    "large notebook",
    "spiral bound notebook",
    "leather cover notebook",
    "graph paper notebook",
    "vintage notebook",
    "notebook with pen holder",
    "dotted grid notebook",
    "recycled paper notebook",
    "travelers notebook",
    "personalized notebook",
    "academic planner notebook",
    "waterproof notebook",
    "hardcover notebook",
    "softcover notebook",
    "notebook with pockets",
    "art sketchbook",
    "college ruled notebook",
    "engineering notebook"
]
https://github.com/Taweilo/keyword_exercise/blob/main/Keyword_simulation_notebooks.ipynb

# Replicate keywords to have 100 rows
keywords = np.random.choice(keywords, size=100)

# Simulate random values for views
views = np.random.randint(1000, 5000, size=100)

# Simulate unique bid values, CTR, and conversion rate for each keyword
unique_bids = {keyword: len(keyword) + 1 for keyword in set(keywords)}
ctr_dict = {keyword: np.random.uniform(0.05, 0.2) for keyword in set(keywords)}
conversion_rate_dict = {keyword: np.random.uniform(0.05, 0.15) for keyword in set(keywords)}

# Create lists for CTR and conversion rate based on keywords
ctr = [ctr_dict[keyword] for keyword in keywords]
conversion_rate = [conversion_rate_dict[keyword] for keyword in keywords]

# Calculate clicks, conversions, total costs
clicks = np.round(views * np.array(ctr), 0)
conversions = np.round(clicks * np.array(conversion_rate))
total_costs = np.array([unique_bids[keyword] for keyword in keywords]) * clicks

# Create the DataFrame
data = {
    'keywords': keywords,
    'bid': [unique_bids[keyword] for keyword in keywords],
    'views': views,
    'clicks': clicks,
    'conversions': conversions,
    'total costs': total_costs
}

keyword_df = pd.DataFrame(data)

# Display the DataFrame
pd.set_option('display.max_rows', None)
keyword_df
```
- first 5 columns of the simulated dataset (total 10000 rows * 6 cols )
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%201.jpg" >

- Statistics of the dataset 
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%202.jpg">

## 3. prepare data
- aggregation via pivot table
- calculate different KPIs (CTR, Conversion rate, Revenue, Profits)

## 4. explore data
Bubble chart to evaluate the keyword performance 
x-axis: CTR <br>
y-axis: conversion rate <br>
bubble size by the profits <br>
bid cost by colors

<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%203.png">

## 5. modeling 
Apply data wrangling to filter the keywords which have:
1. profit > 0
2. CTR > 10%
3. conversion rate >5% <br>
The conditions vary in different situations.

## 6. download CSV file
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%204.jpg" >

## 7. utilize colab to perform the automation 
utilize the same process but apply to different dataset:
1. download dataset (https://github.com/Taweilo/keyword_exercise/blob/main/Keywords%20.csv)
2. run colab (https://colab.research.google.com/drive/18NXtBCv1bqLExXcyl4vUvMksfnbdKmkw#scrollTo=9-m8yacl7yXO)
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%205.jpg" >
3. upload dataset
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%206.jpg" >
4. download csv (check download file "keywords_selected.csv")

