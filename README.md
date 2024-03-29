# Tableau Public - Customize Your Data Source

## Introduction

Now that we have established the knowledge and skills required to build out Tableau visualizations using one table from the Superstore Sales data set we can discuss adding nuance and complexity to your data story by including additional tables in our worksheets and visualizations. This is accomplished by customizing our Tableau **data source**. 

In Tableau, a data source is a bridge between Tableau and the underlying source data. Data sources can be from a single database or file and contain the connection information, metadata, and sheet/table/column names, as well as the relationships between them. Data sources can also be from disparate resources, like two different remote databases in which case Tableau would store and display the connection information, metadata, and sheet/table/column names for both databases in the Data Source. 

In this lesson, we will discuss what questions you should consider when planning a data source. Then, we will demonstrate the steps necessary to build a custom data source in Tableau. Along the way, we will learn more about essential components of the Tableau environment. 

## Learning Objectives

You will be able to:
- Identify and discuss considerations for planning a Tableau data source
- Create a custom data source from different tables in the same data set
- Generate a sheet and visualization from your custom data source
- Save and Publish to Tableau Public

### Planning a Data Source
When planning a data source in Tableau, six essential considerations should factor into your plan. Having a clear answer for each of the question groups below will set you up for success.

#### 1. Where is my data located?
These questions as you to think about **Data Location and Access** and how this can impact how you manage your resources.

1. Is the data on the premises or in the cloud?
    - If your data is local do you want to embed it in the workbook?
    - If your data is in the cloud, do you have the necessary subscriptions and access permissions for all users?

2. Are there any other limitations to locating the data?
    - If you are using a legacy system, you might want to make sure that drivers and connectors are available for your system.
    - Is the file type or connection source supported by Tableau?
    - Are the data usage agreements being negotiated?

3. Are there any other limitations to locating the data?
    - Are there any other anticipated obstacles to accessing this data, like problems with use agreements?


#### 2. What shape is the data and how clean is it?
These questions ask you to think about **Data Quality** and how it can be managed and improved.

1. Do I need to transform the data before it can be used?
    - If you have wide-format data, you may want to consider transforming it too long before building a relationship with that data.
    - You can also use **Swap** in the **Command bar** of your workspace to do this transformation!
   
2. Do I need a pipeline or a way to clean the data before connecting different data sources? Can I do any of these transformations natively in Tableau?
    - Sometimes, you may want to perform certain transformations or exclude data before connecting to another data set to improve the success of unions or joins.

#### 3. How can the data be combined?
These questions ask you to think about your **Data Model** or the structure of the links between your data sources.

1. Is my data spread across multiple systems? If so, what kind of links can I create?
    - For example, if you are working with two remote government databases from two separate agencies that both contain the name and address data for individuals, you can create a relationship between those data sets using the name and address fields in the link.
2. Are there any existing links between my sources?
    - Imagine that you are connected to two different workbooks -- **Customer Accounts** and **Customer Past Due Accounts**. It is likely, that **Customer Past Due Accounts** was generated by filtering **Customer Accounts** -- which means that links between them already exist -- the Customer and their balance due. 

#### 4. Why does the user need the data?
These questions ask you to think about your **User Experience** and if your data source is improving or hindering the users' success. 
1. Are the table and column names understandable?
    - You can make the data source more friendly for your end user by customizing table and column names for your use case when they are nonexistent or not informative.

2. Does the organization of the data make sense for my use case? 
    - We can improve the usability of this data by removing irrelevant columns and merging relevant columns into better-curated tables.

3. Is the metadata informative?
    - If not, you might consider making it more robust to improve how informative your data source is.

#### 5. Who should be accessing the data source?
These questions ask you to think about **Scalability, Security, and Discoverability** and how you can manage these three interests.
1. How many people need to access the data source? (Scalability)
    - If you expect that the data source will have a high volume of requests from users, it is important to find out if your underlying data resources can meet those demands.
    - If you are unsure of the demands on your data source during production, do you have the plan to scale?
2. Do all of my users have the necessary access permissions for the underlying resources? (Security)
    - How secure are the underlying resources? Will my data source undermine the security of these resources?
    - Do my end users have permission to access the underlying data source? Is it possible for them to get permission?
3. How will users find the data source? (Discoverability)
    - What will be the point of access for users? Can the people who need to find the data source find it easily?

#### 6. When will my data be used and refreshed?
These questions ask you to think about **Data Freshness and Resource Performance** and how these will impact the quality of your data source.
1. Should the data be a live connection or an extract?
    - If you want to stream data that will automatically refresh at the same time as the underlying data resource, go with a live connection. 
    - If that is not possible or if you prefer a static data source, consider how often it should be refreshed and who will refresh it.
2. How will we manage multiple connections if our data resources update at different times?
    - Consider how to coordinate conflicting or asynchronous data resources.
3. How often will users access the data source?
    - Do we have the resources to meet the demands of the users?


### Your Turn: Create a Custom Data Source
Now that we have discussed some of the most important considerations for planning a data source in Tableau, we will walk through the steps of creating a data source in Tableau with two different tables from the same database.

#### 1. Create a new data source
Launch Tableau and use the **Connect Pane** on the **Start Page** to open the **Superstore Sales dataset**. This will launch the **Data Source Page**.

In the video below, we demonstrate step 1.

<p>
<div>
    <center>
<table><tr><td>
<video controls src = "https://curriculum-content.s3.amazonaws.com/data-science/images/v3/tableau/tableau/3_custom_data_sources/step1.mov" alt="This is the alt-text for the image." style="width: 700px;"/>
</td></tr></table>
    </center>
</div>


#### 2. Populate the Data Source page
1. Drag the `Orders` table from the **Data pane** to the **canvas**. Then, drag the `Return` table to the canvas. Since the tables have an existing link (`OrderID`) a noodle appears to form an automatic relationship between the tables. 
2. If no automatic relationship was detected by Tableau, the **Edit Relationship*- dialog would open. Then, you can indicate which field should be used to relate the tables.
3. For our purposes, we will use two tables, but in the future, you can use as many tables as needed.

In the video below, we demonstrate step 2.
<p>
<div>
    <center>
<table><tr><td>
<video controls src = "https://curriculum-content.s3.amazonaws.com/data-science/images/v3/tableau/tableau/3_custom_data_sources/step2.mov" alt="This is the alt-text for the image." style="width: 700px;"/>
</td></tr></table>
    </center>
</div>

#### 3. Create a new worksheet
1. Select **Sheet 1*- from the Sheets tab. 
2. Then, double click the **Title box*- near the top of the Sheets pane (it will say 'Sheet 1') and rename it **'Returns by Product Sub-Category'**.

#### 4. Populate the worksheet with `Sub-Category` and `Returns (CNT)`
1. Drag `Sub-Category` from Dimensions listed under the `Orders` table on the Data pane to the Columns shelf.
2. Then, drag `Returns (Count)` from the Measures under the `Returns` table on the Data pane to the Rows shelf. 
3. Tableau will generate a horizontal bar chart with the number of returns for that sub-category. 
4. The `Returns` table does not have a `Sub-Category` column, but it does have an `OrderID` column that can be used to build a relationship between `Returns` and `Orders`. 
5. When we connected to both of these tables on the Data Source page, Tableau intuited this relationship. This reduces the need to perform joins to link tables.

    
#### 5. Tidy up the worksheet
1. Navigate to the **Fit Drop Down Menu** on the **Command bar** at the top of your screen. Select **Entire View**.
2. Then, drag `Returns. Returns (Count)` from the Data pane to the Marks card. Click the icon next to the pill on the Marks card and select the label. 

In the video below, we demonstrate steps 3, 4, and 5.
<p>
<div>
    <center>
<table><tr><td>
<video controls src = "https://curriculum-content.s3.amazonaws.com/data-science/images/v3/tableau/tableau/3_custom_data_sources/step3-4.mov" alt="This is the alt-text for the image." style="width: 700px;"/>
</td></tr></table>
    </center>
</div>

    
##### 6. Great work! Now, let's save this workbook and the viz we created in Tableau public.
    
    
1. Click the **Save** icon on the command bar. 

    
2. Sign in to Tableau Public if prompted. Keep in mind -- when you publish to Tableau Public anyone using Tableau Public can see it. 

    
3. Name your workbook `learn-wb-YYYY-MM-XX`, where YYYY = Current Year, MM = Current Month and XX = Your Initials.
    
<p>
<div>
    <center>
<table><tr><td>
<img src="https://curriculum-content.s3.amazonaws.com/data-science/images/v3/tableau/tableau/3_custom_data_sources/step5.png" alt="Image of the sheets tab in the lower-left corner of the Tableau Data Source Page, with the Left Pane and Canvas visible." alt="This is the alt-text for the image." style="width: 700px;"/>
</td></tr></table>
    </center>
</div>

## Summary
In this lesson, we reviewed the essential questions one must consider when planning a data source in Tableau. Then, we walked through the steps to create a data source with multiple connections using the SuperStore Sales data set and created a link between the `Orders` and `Returns` tables. Then, we created a visualization that communicates the number of returns by sub-category. Finally, we saved and published our new workbook to Tableau Public.

In the next lesson, we are going to build on the foundation we created to generate some more complex visualizations in our workbook.



