# Scrapy Stock Bot

## Description
A Scrapy bot that gathers data from the most active stocks on Yahoo Finance. In order to continously collect most active stocks data, the Scrapy bot is deployed on DigitalOcean. With the bot deployed on DigitalOcean, it was easy to integrate Scrapyd and ScrapyOP within the bot to create a scheduler. The bot continuously gathers stock data, Monday through Friday at 1600 est. After the bot collects the data, it feeds it into a pipeline where the data is cleansed (removes unwanted data or duplicates) and converts it into the data format that is needed. (In this case I needed XML format, so the pipeline creates a XML file). Then, the bot then sends over the cleansed and new data format, it is sent to a data lake which is hosted on AWS. Now that the data is properly and securly stored on AWS, the data can be pulled from the data lake and placed into an Iceberg SQL data table which is hosted locally through Docker. Through docker we can use Spark to query the SQL data for analysis.

## Technologies Used
- Scrapy
- Scrapyd & ScrapyOP
- Digital Ocean
- AWS
- Iceberg & Spark
- Docker

## Challenges
While working on this project, I have came across several challenging issues, most of which were just trying to install some of the technologies on my local machine (Scrapy & Docker). Other than those issues, the only real issue I had was writing an XML pipeline. Writing the XML pipeline code, was rough due to the poor documentation on Scrapy pipelines and the lack of XML examples within the documentation. 

## Future Features

## To-Do-List
1. ~~Accquire data~~
2. ~~Cleanse the data~~
3. ~~Convert the data to correct format~~ 
4. Hookup spider to a scheduler to scrape data over a certain time period (scrapyard)
5. Interpreting data that could be interpreted in multiple ways (Need to look more into this)
6. Remove duplicates of the data
7. Store data on a cloud service (most likely AWS)
8. Create a SQL database to query data (Iceberg & Spark)
