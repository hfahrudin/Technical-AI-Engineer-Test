# Coding Test 3 - Explain how it's different from splitting the small vs large files

### Small vs Large Files
- **Small files**
  - Processed quickly and individually.
  - Minimal risk of performance issues when reading/writing.
  - Easy to transfer, copy, or back up without special handling.

- **Large files**
  - Can be slow to process, read, or write in one go.
  - Higher risk of RAM or I/O bottlenecks in reading or writing.
  - Often require additional strategy to work around memory limitation.

⚠️ Large files need carefull handling and the strategy need to be made depend on the use cases

---

### Managing Large Files

When working with large files, direct processing can be slow or memory-intensive. There are several strategies to manage them effectively:

### 1. Splitting Large Files
- Break a large file into smaller chunks to process each part separately.
- Reduces memory load and allows parallel processing.
- Enable storage, transfer, and error recovery with out constrain of physical I/O bottlenecks.

### 2. Reducing Dimensions / Summarization
- Instead of processing all raw data, extract or summarize key features.
- Techniques include aggregation, sampling, or feature selection.
- Helps focus on necessary information while speeding up analysis.
- Particularly useful during *data exploration*, where insights can be gained without full dataset processing.

💡 Managing large files is not only about *splitting*; *reducing dimensionality* or summarizing data is often equally effective.

---

### Coding Test 1 & 2 Cases: Reducing Dimentionality to Allow Ease Data Exploration

By processing the dataset in **chunks** and aggregating within each chunk, we efficiently summarize the data while keeping memory usage manageable.  

- **City counts per country:** Number of customers per `(Country, City)` pair.  
- **Company counts:** Total customers per company.  
- **Monthly counts per country:** Customer totals per `(Country, Subscriber Date)`.

Aggregating per chunk allows us to **incrementally build the final summaries** (`city_counts_df`, `company_counts_df`, `monthly_counts_df`) without loading the entire dataset into memory. This strategy is particularly suitable for obtaining the key insights identified which are:

- **Total Account Insights** : Breakdown by **Country**, **City**, and **Company**.
- **Historical Growth Analysis**: Customer trends over time (monthly totals per country).

As a result, we could reduce the memory usage relatively signficant. Here are brief **memory usage benchmark:**
- Full CSV: 1,338.19 MB
- Total summary DataFrames: 331.96 MB
- Memory reduction: 75.2%

🎉 By processing the dataset in **chunks** and aggregating within each chunk, we efficiently summarize the data while keeping memory usage manageable. This approach allows us to retain insights from the entire dataset **without any noticeable caveats**.


