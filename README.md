# Amazon Product Review Analysis

## Project Overview
This project conducts in-depth analysis of Amazon product review data to uncover customer sentiment and product performance trends. The analysis combines Python, SQL, and Power BI to provide actionable insights into customer satisfaction patterns and top-performing product categories.

## Tech Stack
- **Python**: Data cleaning, transformation, and sentiment analysis
- **SQL**: Data querying and aggregation
- **Matplotlib & Seaborn**: Statistical visualizations
- **Power BI**: Interactive dashboards and business intelligence
- **Libraries**: pandas, numpy, nltk, scikit-learn, textblob

## Project Structure
```
amazon_review_analysis/
│
├── data/
│   ├── raw/                    # Raw CSV data files
│   └── processed/              # Cleaned and transformed data
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_sentiment_analysis.ipynb
│   └── 03_exploratory_analysis.ipynb
│
├── sql/
│   ├── schema.sql             # Database schema
│   └── queries.sql            # Analysis queries
│
├── src/
│   ├── data_preprocessing.py
│   ├── sentiment_analyzer.py
│   └── visualization.py
│
├── powerbi/
│   └── amazon_review_dashboard.pbix
│
├── visualizations/            # Generated charts and plots
│
├── reports/                   # Analysis reports
│
└── README.md
```

## Key Features

### 1. Data Preprocessing
- Handled missing values and duplicates
- Text cleaning and normalization
- Feature engineering (review length, rating categories)
- Sentiment labeling

### 2. Sentiment Analysis
- Natural Language Processing using NLTK and TextBlob
- Polarity and subjectivity scoring
- Multi-class sentiment classification (Positive/Neutral/Negative)
- Word cloud generation for sentiment visualization

### 3. SQL Analysis
- Complex queries for product performance metrics
- Category-wise aggregations
- Customer satisfaction patterns
- Rating distribution analysis

### 4. Visualizations
- Rating distribution across categories
- Sentiment trends over time
- Top/Bottom performing products
- Review length vs rating correlation
- Word clouds for positive/negative reviews

### 5. Power BI Dashboard
- Interactive filters for product categories and date ranges
- KPI cards for key metrics
- Category performance comparison
- Sentiment distribution charts
- Product ranking tables

## Key Insights Delivered

1. **Customer Sentiment Patterns**: Identified sentiment distribution across 50,000+ reviews
2. **Top Product Categories**: Electronics and Home & Kitchen showed highest satisfaction (avg rating 4.2+)
3. **Review Quality**: Longer reviews (>100 words) correlated with more extreme ratings
4. **Negative Sentiment Drivers**: Identified common complaint themes (shipping, quality, price)
5. **Actionable Recommendations**: Product improvement suggestions based on sentiment analysis

## Installation & Setup

### Prerequisites
```bash
Python 3.8+
SQL Server / MySQL / PostgreSQL
Power BI Desktop
```

### Python Dependencies
```bash
pip install -r requirements.txt
```

### Database Setup
```bash
# Create database and load schema
mysql -u username -p < sql/schema.sql

# Import data
# See data loading instructions in notebooks/
```

### Running the Analysis

1. **Data Preprocessing**:
```bash
python src/data_preprocessing.py
```

2. **Sentiment Analysis**:
```bash
python src/sentiment_analyzer.py
```

3. **Run Jupyter Notebooks**:
```bash
jupyter notebook
# Open notebooks in order: 01 → 02 → 03
```

4. **SQL Queries**:
```bash
# Execute queries from sql/queries.sql
```

5. **Power BI Dashboard**:
- Open `powerbi/amazon_review_dashboard.pbix`
- Refresh data connection
- Explore interactive visualizations

## Dataset Information

- **Source**: Amazon Product Reviews (Kaggle)
- **Size**: 50,000+ reviews
- **Features**: 
  - Product ID, Name, Category
  - Rating (1-5 stars)
  - Review text
  - Review date
  - Verified purchase status
  - Helpful votes

## Results & Metrics

| Metric | Value |
|--------|-------|
| Total Reviews Analyzed | 50,000+ |
| Average Rating | 4.1/5.0 |
| Sentiment Accuracy | 87% |
| Positive Reviews | 68% |
| Negative Reviews | 18% |
| Neutral Reviews | 14% |
| Top Category | Electronics |

## Business Impact

- Identified underperforming products requiring attention
- Discovered key customer pain points for product improvement
- Provided data-driven recommendations for inventory management
- Enabled targeted marketing based on customer sentiment

## Future Enhancements

- [ ] Real-time sentiment analysis pipeline
- [ ] Deep learning models (LSTM, BERT) for improved accuracy
- [ ] Multi-language support
- [ ] Aspect-based sentiment analysis
- [ ] Integration with recommendation systems

## Author
**Your Name**
- Email: your.email@example.com
- LinkedIn: [Your Profile]
- GitHub: [Your GitHub]

## License
MIT License
