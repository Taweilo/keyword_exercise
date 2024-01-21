# Keywords automation system 

## content
1. simulated dataset
2. perform keyword analysis
3. build algorism
4. download csv 

## 1. undersand business problem
To easily handle the keyword selection via KPI, an automated process can deal with different CSV file utilizing the same rule to explore, evaluate, and select the keywrods. 

## 2. understand the data
The data is simulated  

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

# Replicate keywords to have 100 rows
keywords = np.random.choice(keywords, size=10000)

# Simulate random values for views
views = np.random.randint(1000, 5000, size=10000)

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

df = pd.DataFrame(data)

# Display the DataFrame
pd.set_option('display.max_rows', None)
df.head()

'''

## 3. Prepare data
to calculate different KPI 
1. CTR
2. Conversion rate
3. Revenue = conversions * notebook price
4. Profits = revenue - total PPC costs

## 4. explore data


## 5. modeling 


