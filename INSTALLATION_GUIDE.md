# Installation and Setup Guide

## Prerequisites

### Software Requirements
- **Python 3.8 or higher**
- **Database**: MySQL 8.0+ OR PostgreSQL 12+ OR SQL Server 2019+
- **Power BI Desktop** (latest version)
- **Jupyter Notebook**
- **Git** (optional, for version control)

### Hardware Requirements
- **RAM**: Minimum 4GB, Recommended 8GB+
- **Storage**: 2GB free space
- **OS**: Windows 10+, macOS 10.14+, or Linux

## Step-by-Step Installation

### 1. Clone or Download Project

**Option A: Using Git**
```bash
git clone <your-repository-url>
cd amazon_review_analysis
```

**Option B: Manual Download**
- Download ZIP file
- Extract to your preferred location
- Open terminal/command prompt in project directory

### 2. Set Up Python Environment

**Create Virtual Environment (Recommended)**
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

**Install Dependencies**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**Download NLTK Data**
```python
python -c "import nltk; nltk.download('punkt'); nltk.download('stopwords'); nltk.download('vader_lexicon')"
```

### 3. Set Up Database

**Option A: MySQL**
```bash
# Install MySQL
# Windows: Download from mysql.com
# macOS: brew install mysql
# Linux: sudo apt-get install mysql-server

# Start MySQL service
# Windows: Services → MySQL → Start
# macOS: brew services start mysql
# Linux: sudo systemctl start mysql

# Create database
mysql -u root -p < sql/schema.sql
```

**Option B: PostgreSQL**
```bash
# Install PostgreSQL
# Windows: Download from postgresql.org
# macOS: brew install postgresql
# Linux: sudo apt-get install postgresql

# Start PostgreSQL
# macOS: brew services start postgresql
# Linux: sudo systemctl start postgresql

# Create database
psql -U postgres -f sql/schema.sql
```

**Option C: SQL Server**
```bash
# Install SQL Server Express (free)
# Download from microsoft.com/sql-server

# Run schema script in SQL Server Management Studio
```

### 4. Configure Database Connection

**Create .env file in project root:**
```env
# MySQL
DB_TYPE=mysql
DB_HOST=localhost
DB_PORT=3306
DB_NAME=amazon_reviews_db
DB_USER=your_username
DB_PASSWORD=your_password

# PostgreSQL
# DB_TYPE=postgresql
# DB_HOST=localhost
# DB_PORT=5432
# DB_NAME=amazon_reviews_db
# DB_USER=your_username
# DB_PASSWORD=your_password
```

### 5. Verify Installation

**Test Python Setup**
```bash
python -c "import pandas; import nltk; import sklearn; print('All packages installed successfully!')"
```

**Test Database Connection**
```bash
python -c "from sqlalchemy import create_engine; engine = create_engine('mysql://user:pass@localhost/amazon_reviews_db'); print('Database connection successful!')"
```

## Data Setup

### Option 1: Use Sample Data (Included)

The project includes a sample dataset for testing:
```bash
# Data is in data/raw/sample_reviews.csv
# Run preprocessing
python src/data_preprocessing.py
```

### Option 2: Download Full Dataset

**From Kaggle:**
1. Visit: https://www.kaggle.com/datasets/bittlingmayer/amazonreviews
2. Download dataset
3. Place CSV in `data/raw/amazon_reviews.csv`
4. Run preprocessing

```bash
python src/data_preprocessing.py
```

### Option 3: Use Your Own Data

**Required CSV columns:**
- `product_id` (string)
- `product_name` (string)
- `rating` (integer, 1-5)
- `review_text` (text)
- `review_date` (date, optional)
- `product_category` (string, optional)

Place CSV in `data/raw/` and update file paths in scripts.

## Running the Project

### 1. Data Preprocessing
```bash
python src/data_preprocessing.py
```
**Output**: `data/processed/cleaned_reviews.csv`

### 2. Sentiment Analysis
```bash
python src/sentiment_analyzer.py
```
**Output**: `data/processed/sentiment_analyzed_reviews.csv`

### 3. Generate Visualizations
```bash
python src/visualization.py
```
**Output**: Charts in `visualizations/` folder

### 4. Load Data to Database
```bash
# Use provided script or custom loader
python scripts/load_to_database.py
```

### 5. Run Jupyter Notebooks
```bash
jupyter notebook
```
Open notebooks in order:
1. `01_data_cleaning.ipynb`
2. `02_sentiment_analysis.ipynb`
3. `03_exploratory_analysis.ipynb`

### 6. Open Power BI Dashboard
```bash
# Open Power BI Desktop
# File → Open → powerbi/amazon_review_dashboard.pbix
# Refresh data connections
```

## Troubleshooting

### Common Issues

**Issue: ModuleNotFoundError**
```bash
# Solution: Reinstall requirements
pip install -r requirements.txt --force-reinstall
```

**Issue: NLTK Data Not Found**
```python
# Solution: Download NLTK data
import nltk
nltk.download('all')  # Downloads all data
```

**Issue: Database Connection Failed**
```bash
# Solution: Check credentials in .env file
# Verify database service is running
# Test connection manually
```

**Issue: Memory Error During Processing**
```python
# Solution: Process data in chunks
# Modify data_preprocessing.py to use chunksize parameter
df = pd.read_csv('file.csv', chunksize=10000)
```

**Issue: Power BI Can't Connect to Data**
```
Solution:
1. Power BI → Home → Transform Data → Data source settings
2. Update file paths to match your system
3. Refresh preview
```

## Performance Optimization

### For Large Datasets (>1M rows)

**1. Use Sampling**
```python
# In preprocessing script
df = df.sample(frac=0.1, random_state=42)  # Use 10% sample
```

**2. Enable Multiprocessing**
```python
# In sentiment analysis
from multiprocessing import Pool
# Use parallel processing for sentiment analysis
```

**3. Optimize Database**
```sql
-- Add indexes for better performance
CREATE INDEX idx_product_rating ON reviews(product_id, rating);
CREATE INDEX idx_sentiment ON reviews(sentiment);
```

## Verification Checklist

- [ ] Python environment activated
- [ ] All packages installed successfully
- [ ] NLTK data downloaded
- [ ] Database created and accessible
- [ ] Sample data processed without errors
- [ ] Visualizations generated
- [ ] Jupyter notebooks run successfully
- [ ] Power BI dashboard opens and displays data

## Next Steps

After successful installation:
1. Review `README.md` for project overview
2. Explore `notebooks/` for detailed analysis
3. Check `sql/queries.sql` for analytical queries
4. Open Power BI dashboard for interactive insights
5. Customize analysis for your specific needs

## Support

If you encounter issues:
1. Check troubleshooting section above
2. Review error messages carefully
3. Verify all prerequisites are installed
4. Check Python and package versions
5. Consult documentation for specific tools

## Additional Resources

- **Python**: https://docs.python.org/3/
- **Pandas**: https://pandas.pydata.org/docs/
- **NLTK**: https://www.nltk.org/
- **Power BI**: https://docs.microsoft.com/power-bi/
- **SQL**: https://www.w3schools.com/sql/

---

**Installation complete!** You're ready to start analyzing Amazon reviews.
