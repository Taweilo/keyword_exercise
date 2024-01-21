# Keywords automation system 

## content
1. undersand business problem
2. understand the data
3. prepare data
4. explore data
5. modeling
6. download the CSV file as the end product
7. repetitively running the notebook with different CSV files as automation

## 1. undersand business problem
To easily handle the keyword selection via KPI, an automated process can deal with different CSV files utilizing the same rule to explore, evaluate, and select the keywords. 

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
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%203.png" width="1100" height="450">

## 5. modeling 
Apply data wrangling to filter the keywords which have:
1. profit > 0
2. CTR > 10%
3. conversion rate >5%
The conditions vary in different situations.

## 6. download CSV file
<img src="https://github.com/Taweilo/keyword_exercise/blob/main/Image/image%204.jpg" >
