# web-scraping-with-selenium
Web Scrapping is an easy way to get a large volume of data in a relatively short time frame

**Steps:-**
1. Install selenium using pip
 ** pip3 install selenium**
 
 2. Download Chrome Driver:
    To download web drivers, you can choose any of below methods- 
    You can either directly download chrome driver from the below link-
    https://chromedriver.chromium.org/downloads
    Or, you can download it directly using below line of code-driver = webdriver.Chrome(ChromeDriverManager().install())
    
 3. import libraries
    Beautiful Soup is a Python library for pulling data out of HTML
    **from bs4 import BeautifulSoup**
    
    Selenium WebDriver acts as the bridge between the script and the web browser.And it is the main component that communicates with the web browser.
    f**rom selenium import webdriver**
    
    Python package that provides numerous tools for data analysis.
    import pandas as pd
    
    provides various time-related functions. For related functionality
    import time
    
    
    4. Install Driver
       driver = webdriver.Chrome(ChromeDriverManager().install())
        
    5. Check the Sourc code for the url and find the data you want to extract
    
    6. Define the Columns 
       ** df=pd.DataFrame(columns=['serial no','Registration Number','Date of Grant','Name Factory Address','IS NO','Product','Status','Valid Upto','Models deleted from scope','Brand','View Models'])**
       
     7. Set a range and url
         If the data is large then set a range put it inside the loop to ignor the server error. and also set the url like 
            **for param in range(1,11):
            url="https://www.crsbis.in/BIS/Lims_registration.do?hmode=getLimsData&regNo=NA==&prodCat=&models="
            driver= webdriver.Chrome("/home/abhishek/Desktop/Web/chromedriver")
            driver.get(url)
            time.sleep(10)
            soup= BeautifulSoup(driver.page_source,'html5lib')
            driver.close()
            rows = soup.find("table").find("tbody").find_all("tr")**
            
            
     8. Loop to Extract the Data 
            for row in rows:
                s_no=row.find_all('td')[0].get_text().replace(" ","").replace("\n","")
                Registration_Number=row.find_all('td')[1].get_text().replace(" ","").replace("\n","")
                Date=row.find_all('td')[2].get_text().replace(" ","").replace("\n","")
                Date1=row.find_all('td')[3].get_text().replace(" ","").replace("\n","")
                Date2=row.find_all('td')[4].get_text().replace(" ","").replace("\n","")
                Date3=row.find_all('td')[5].get_text().replace(" ","").replace("\n","")
                Date4=row.find_all('td')[6].get_text().replace(" ","").replace("\n","")
                Date5=row.find_all('td')[7].get_text().replace(" ","").replace("\n","")
                Date6=row.find_all('td')[8].get_text().replace(" ","").replace("\n","")
                Date7=row.find_all('td')[9].get_text().replace(" ","").replace("\n","")
                Date8=row.find_all('td')[10].get_text().replace(" ","").replace("\n","")
                df=df.append({'serial no':s_no,'Registration Number':Registration_Number,'Date of Grant':Date,'Name Factory Address':Date1,'IS NO':Date2,'Product':Date3,'Status':Date4,'Valid Upto':Date5,'Models deleted from scope':Date6,'Brand':Date7,'View Models':Date8},ignore_index=True)
    

       
     
