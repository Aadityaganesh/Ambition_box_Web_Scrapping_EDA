# Ambition_box_Web_Scrapping_EDA
This project extracts data from the AmbitionBox website through web scraping techniques and performs comprehensive Exploratory Data Analysis (EDA). The analysis provides insights into industry trends, company ratings, and employee reviews, helping understand key patterns and metrics from a job seeker and industry analyst perspective.

# Table of Contents
- [Installation](#installation)
- [Tools](#tools)
- [Web Scraping](#web-scraping)
- [Challenges Faced](#challenges-faced)
- [Features](#features)
- [Data preprocessing](#data-preprocessing)
- [Data Analysis](#data-analysis)
- [Conclusion](#conclusion)

# Installation
**Installing Jupyter lab**
Open your terminal and then run this command to install jupyter lab

    pip install jupyter lab
    
**Clone this Repository**
If the repository on github, Clone it to your local machine

    git clone https://github.com/Aadityaganesh/Ambition_box_Web_Scrapping_EDA

**Launch jupyter lab**

Launch juypter lab in terminal by running the following command

    jupyter lab

# Tools 
These are the Tools used in this Project

- **Python:** A versatile programming language widely used for data analysis, web development, and automation.
- **BeautifulSoup:** A Python library for parsing HTML and XML documents, often used in web scraping to extract data from web pages.
- **Regex:** A sequence of characters defining a search pattern, used for string matching and manipulation in text data.
- **Numpy:** A Python library for numerical computing, providing support for large, multi-dimensional arrays and matrices.
- **Pandas:** A data analysis library in Python, offering data structures like DataFrames for manipulating structured data.
- **Matplotlib:** A Python library for creating static, animated, and interactive visualizations in data analysis.
- **Seaborn:** A Python visualization library based on Matplotlib, known for making attractive and informative statistical graphics.

You can install all these libraries in one command using pip.
Here’s how:
  
    pip install python beautifulsoup4 regex numpy pandas matplotlib seaborn

For Jupyter Notebooks,
use:

    !pip install python beautifulsoup4 regex numpy pandas matplotlib seaborn

Make sure you have Python and pip installed on your system. This command installs all libraries with the latest compatible versions.

# Web Scraping
Web scraping is the automated process of extracting data from websites. It involves using a program or script to request and retrieve specific information from a web page's HTML code, parsing it, and organizing it into a structured format like a spreadsheet or database for further analysis. Web scraping is widely used in applications like price comparison, content aggregation, market research, and data analysis, where large amounts of publicly available information are needed in a consumable format.

Key components of web scraping include:

**HTTP Requests:** Using libraries like requests to fetch the HTML content of a web page.
**Parsing:** Extracting specific data points using tools like BeautifulSoup or lxml to navigate the HTML structure.


# Challenges Faced
When web scraping, handling client-side (4xx) and server-side (5xx) errors is essential for ensuring reliable data extraction.

**Client-Side Errors (4xx)**

Examples: 404 (Not Found), 403 (Forbidden).
Causes: Invalid URLs, authentication needs, or malformed requests.
Solution: Validate URLs, set up correct headers, and use authentication as needed.

**Server-Side Errors (5xx)**

Examples: 500 (Server Error), 504 (Gateway Timeout).

Causes: Server overload or timeouts.

Solution: Add delays between requests, retry on failure, and handle errors gracefully.

**Ensuring 200 OK Response**

Check Status: Confirm response.status_code == 200.

User-Agent: Use a User-Agent header to mimic real browsing.

Request Frequency: Add delays to avoid overloading the server.


**Converting the response 403  to 200**

Your code snippet is configured with headers that should generally prevent a 403 Forbidden error, which typically occurs when the server blocks access. To help ensure a 200 OK response, consider these common solutions:

Modify the User-Agent String: Some websites block certain user agents. Try using a more commonly accepted User-Agent string or copy one from a popular browser (e.g., Chrome).

Use Proxies: If the server blocks your IP, you can try accessing the site through a proxy.

Enable Cookies: Some websites require cookies for access. Use requests.Session() to manage cookies automatically.

    import requests
    
    url = 'your_url_here'  # replace with the actual URL
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/106.0 Safari/537.36',
        'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
        'Accept-Language': 'en-US,en;q=0.5',
        'Connection': 'keep-alive',
    }
    
    # Use a session to maintain cookies and improve the likelihood of a 200 response
    session = requests.Session()
    response = session.get(url, headers=headers)
    
    if response.status_code == 200:
        print("Request successful!")
    else:
        print(f"Error: {response.status_code}")

Using requests.Session() helps manage cookies, and the updated User-Agent can improve chances of bypassing the 403 Forbidden error.

# Features

These were the brief description about dataset

- **Company:** The name of the organization being reviewed or analyzed.
- **Rating:** Overall rating or score given to the company, often based on employee feedback.
- **Industry:** The sector in which the company operates, such as IT, healthcare, or finance.
- **Employees:** Number of employees working at the company.
- **Location:** The geographical area where the company’s main offices or headquarters are situated.
- **Ownership:** Indicates whether the company is privately owned, publicly traded, or government-owned.
- **Age:** The number of years since the company was founded.
- **Reviews:** Total number of employee reviews, providing insights into the company culture and work environment.
- **Salaries:** Information on employee compensation, helping assess pay scales across roles.
- **Jobs:** Current job openings or listings available at the company.
- **Interviews:** Data on the interview process, including experiences and typical questions.
- **Benefits:** Summary of benefits and perks offered to employees, like health insurance or retirement plans.

## Data Preprocessing

Data preprocessing encompasses both data cleaning and analyzing, ensuring that the dataset is free of errors and inconsistencies. This process prepares the data for further analysis or modeling by transforming it into a usable format and uncovering patterns or relationships within the data.

- **Data Cleaning:** Involves handling missing values, correcting errors, and removing duplicates to enhance data quality.

- **Data Transforming:** Includes scaling, encoding categorical variables, and normalizing data to create a consistent and usable dataset for analysis and modeling.

## Data Analysis


   ### Top Industries
   A bar plot is a graphical representation of categorical data, where individual bars represent the frequency or value of each category. It is useful for comparing different groups and understanding the distribution of data across categories.
   
    top_15_industries = df['Industry'].value_counts().head(10)

    # Plot the result
    plt.figure(figsize=(13, 6))
    sns.barplot(x=top_15_industries.index, y=top_15_industries.values, palette='icefire')
    plt.title('The count of Top 10 Industries')
    plt.xlabel('Industry')
    plt.ylabel('Frequency')
    plt.xticks(rotation=45)
    plt.show()

   ![image](https://github.com/user-attachments/assets/6d4be506-d2ce-4b08-8841-a08dd68ddc64)

   ### Pie Chart
   A pie chart is a circular statistical graphic that represents proportions of a whole. Each slice of the pie corresponds to a category's contribution to the total, allowing for a quick visual comparison of different categories.

    df['Ownership'].value_counts().plot(kind = 'pie', autopct = "%0.2f")
   
   ![image](https://github.com/user-attachments/assets/8ddbfca2-2e91-4dcf-a29c-cfd5bb19b9e7)

 
   
   ### Box plot
   A box plot, also known as a whisker plot, is a standardized way of displaying the distribution of data based on a five-number summary: minimum, first quartile (Q1), median (Q2), third quartile (Q3), and maximum.
    
    sns.boxplot(x=df['Rating'], color='#B0E313')
    plt.title('Box Plot of Company Ratings')
    plt.xlabel('Rating')
    plt.show()

   ![image](https://github.com/user-attachments/assets/7cf66f6b-7442-45d4-9319-d8463ee00671)


   ### Scatter plot
   A scatter plot is a type of data visualization that uses dots to represent the values obtained for two different variables, one plotted along the x-axis and the other along the y-axis. This graphical representation helps to visualize relationships, trends, and patterns between the two variables.

    # Plotting Salaries vs Benefits
    plt.figure(figsize=(10, 5))
    sns.scatterplot(x='Salaries', y='Benefits', data=df, color = '#007BFF')
    plt.title('Salaries vs Benefits')
    plt.show()
    
   ![image](https://github.com/user-attachments/assets/8b50c735-17d1-4ca5-8c5f-c7e253aa3945)

   
   ### Heatmap
   
   Correlation is a statistical measure that expresses the extent to which two variables change in relation to each other. It indicates the strength and direction of a linear relationship between pairs of variables, with values ranging from -1 to 1.

    correlation = df[['Rating','Reviews', 'Salaries', 'Jobs', 'Benefits']].dropna()
    
    # Calculate the correlation matrix
    corr_matrix = correlation.corr()
    
    # Plotting the heatmap
    plt.figure(figsize=(10, 6))
    sns.heatmap(corr_matrix, annot=True, cmap="Blues", vmin=-1, vmax=1)
    plt.xticks(rotation=0)
    plt.title('Correlation Matrix')
    plt.show()


   ![image](https://github.com/user-attachments/assets/a4a9e3ad-a9aa-4a2e-8ea8-84765e9008ce)
   
   **Positive Correlation (0 to 1):** As one variable increases, the other variable also tends to increase. For example, a high rating may correlate with higher salaries.

   **Negative Correlation (-1 to 0):** As one variable increases, the other variable tends to decrease. For instance, a high number of jobs available might correlate with lower salaries.
    
   **No Correlation (around 0):** Indicates no discernible relationship between the variables.
   
   
   ### Extracting Top 5 Companies:

    new_df = df.head()
    # Creating a figure with subplots
    fig, axs = plt.subplots(2, 2, figsize=(14, 10))
    
    # Rating vs. Salaries
    sns.barplot(x='Company', y='Salaries', data=new_df, ax=axs[0, 0], palette='Blues')
    axs[0, 0].set_title('Salaries by Company', fontsize=16)
    axs[0, 0].set_ylabel('Salaries (in ₹)')
    
    # Rating vs. Reviews
    sns.barplot(x='Company', y='Reviews', data=new_df, ax=axs[0, 1], palette='Greens')
    axs[0, 1].set_title('Reviews by Company', fontsize=16)
    axs[0, 1].set_ylabel('Reviews Count')
    
    # Age vs. Benefits
    sns.barplot(x='Company', y='Benefits', data=new_df, ax=axs[1, 0], palette='Oranges')
    axs[1, 0].set_title('Benefits by Company', fontsize=16)
    axs[1, 0].set_ylabel('Benefits Count')
    
    # Age vs. Age
    sns.barplot(x='Company', y='age', data=new_df, ax=axs[1, 1], palette='Purples')
    axs[1, 1].set_title('Age by Company', fontsize=16)
    axs[1, 1].set_ylabel('Age')
    
    # Adjusting the layout
    plt.tight_layout()
    plt.show()


![image](https://github.com/user-attachments/assets/66fc0ccf-e854-4bae-a758-94751d4da7c6)
    
   Retrieves the first five rows from the DataFrame df, representing the top 5 companies.
    
   **Creating Subplots:** Sets up a 2x2 grid of subplots for visualizing multiple metrics.
    
   **Rating vs. Salaries:** Generates a bar plot comparing salaries across the top 5 companies.
    
   **Rating vs. Reviews:** Creates a bar plot showing the number of reviews for each company.
    
   **Age vs. Benefits:** Visualizes the count of benefits offered by each company in a bar plot.
    
   **Age vs. Age:** Displays the age of each company in a separate bar plot.
    
   **Adjusting Layout:** Optimizes the layout of subplots and displays the final figure

# Conclusion

- We explored individual variables and their relationships, revealing patterns like smaller companies receiving higher ratings.
- Our analysis showed significant variation in ratings across industries, with IT Services consistently performing well.
- We found strong correlations between review counts, salary, Jobs though company ratings remained independent.
- Companies younger than 50 years are experiencing rapid growth and are highly engaged with emerging trends, adapting quickly to the changing market landscape.
- Established companies show substantial growth and are making notable efforts to secure their positions in the Fortune 500, leveraging their long-standing presence.
