# NoSQL_Challenge
*Challenge 12 for UC Berkeley Data Analytics Bootcamp*

In this Challenge, we use NoSQL (MongoDB) to explore and analyze data. 

**Challenge Scenerio:** The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. We've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data to help their journalists and food critics decide where to focus future articles.

### Step 1: Database and Jupyter Notebook Set Up
We imported the data provided in the ```establishments.json``` file from Terminal with the databased name ```uk_food``` and the collection named ```establishments```. 

Within ```Jupyter Notebook```, ```PyMongo``` and ```Pretty Print``` (pprint) libraries were imported. An instance of the ```Mongo Client``` was created. Subsequently, the ```establishments``` collection was assigned to the variable ```establishments_table``` to prepare the collection for use.    
  
### Step 2: Update the Database
- The data for a new restaurant called "Penang Flavors" was added using ```.insert_one()``` and missing information filled using ```.update_one()```.
- All documents where ```LocalAuthorityName``` is "Dover" were removed using ```.delete_many()```.
- Number values are stored as strings in ```RatingValue```, ```Longitude```, and ```Latitude``` were converted to numbers using ```.update_many()``` and ```$toDouble```.
  
### Step 3: Exploratory Analysis
Eat Safe, Love had specific questions they wanted answered to help them find the locations they wished to visit and avoid. Please see the NoSQL Notebooks for the full code and analysis of this data.  
  
**1. Which establishments have a hygiene score equal to 20?**  
We used ```.count_documents()``` for this query and found 41 establishments with a hygiene score equal to 20.  
  
**2. Which establishments in London have a RatingValue greater than or equal to 4?**  
We used ```$regex```, ```$gte```, and ```.count_documents()``` for this query and found 33 establishments with a rating value greater than or equal to 4 (out of 5).  
  
**3. What are the top 5 establishments with a RatingValue of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?**  
We used ```$lte```, ```$gte```, ```.find()```, ```.sort()```, and ```.limit()``` for this query and found that "Howe and Co Fish and Chips - Van 17", "Atlantic Fish Bar", "Plumstead Manor Nursery", "Iceland", and "Volunteer" were the top 5 establishments nearest "Penang Flavors".  
  
**4. How many establishments in each Local Authority area have a hygiene score of 0?**  
Using the ```.aggregate``` function and a pipeline we found that 55 establishments had a hygiene score of 0.  
