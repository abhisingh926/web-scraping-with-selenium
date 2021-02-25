# web-scraping-with-selenium
Web Scrapping is an easy way to get a large volume of data in a relatively short time frame

<b>Steps:-</b>
1. <b>Install selenium using pip <br/><b>pip3 install selenium</b>
 
2. <b>Download Chrome Driver:</b>
    To download web drivers, you can choose any of below methods- 
    You can either directly download chrome driver from the below link-
    https://chromedriver.chromium.org/downloads
    Or, you can download it directly using below line of code-driver = webdriver.Chrome(ChromeDriverManager().install())
    
3. <b>import libraries</b><br/>
    Beautiful Soup is a Python library for pulling data out of HTML
    <b>from bs4 import BeautifulSoup</b><br/>
    
    Selenium WebDriver acts as the bridge between the script and the web browser.And it is the main component that communicates with the web browser.
    <b>from selenium import webdriver</b><br/>
    
    Python package that provides numerous tools for data analysis.
    <b>import pandas as pd</b><br/>
    
    provides various time-related functions. For related functionality
    <b>import time</b><br/>
    
    
4. <b>Install Driver</b><br/>
       <b>driver = webdriver.Chrome(ChromeDriverManager().install())</b><br/>
        
5. <b>Check the Sourc code for the url and find the data you want to extract</b><br/>
    
6. <b>Define the Columns </b><br/>
       </b><br/>df=pd.DataFrame(columns=['serial no','Registration Number','Date of Grant','Name Factory Address','IS NO','Product','Status','Valid Upto','Models deleted from scope','Brand','View Models'])</b><br/>
       
7. <b>Set a range and url</b><br/>
         If the data is large then set a range put it inside the loop to ignor the server error. and also set the url like 
           <b>for param in range(1,11):<br/>
            url="https://www.crsbis.in/BIS/Lims_registration.do?hmode=getLimsData&regNo=NA==&prodCat=&models="<br/>
            driver= webdriver.Chrome("/home/abhishek/Desktop/Web/chromedriver")<br/>
            driver.get(url)<br/>
            time.sleep(10)<br/>
            soup= BeautifulSoup(driver.page_source,'html5lib')<br/>
            driver.close()<br/>
            rows = soup.find("table").find("tbody").find_all("tr")</b><br/>
            
            
8. <b>Extract the Data</b><br/>
      Extract the data using for loop
            <b>for row in rows:<br/>
                s_no=row.find_all('td')[0].get_text().replace(" ","").replace("\n","")<br/>
                Registration_Number=row.find_all('td')[1].get_text().replace(" ","").replace("\n","")<br/>
                Date=row.find_all('td')[2].get_text().replace(" ","").replace("\n","")<br/>
                Date1=row.find_all('td')[3].get_text().replace(" ","").replace("\n","")<br/>
                Date2=row.find_all('td')[4].get_text().replace(" ","").replace("\n","")<br/>
                Date3=row.find_all('td')[5].get_text().replace(" ","").replace("\n","")<br/>
                Date4=row.find_all('td')[6].get_text().replace(" ","").replace("\n","")<br/>
                Date5=row.find_all('td')[7].get_text().replace(" ","").replace("\n","")<br/>
                Date6=row.find_all('td')[8].get_text().replace(" ","").replace("\n","")<br/>
                Date7=row.find_all('td')[9].get_text().replace(" ","").replace("\n","")<br/>
                Date8=row.find_all('td')[10].get_text().replace(" ","").replace("\n","")<br/>
                df=df.append({'serial no':s_no,'Registration Number':Registration_Number,'Date of Grant':Date,'Name Factory Address':Date1,'IS NO':Date2,'Product':Date3,'Status':Date4,'Valid Upto':Date5,'Models deleted from scope':Date6,'Brand':Date7,'View Models':Date8},ignore_index=True)</b><br/>
    

       
     
