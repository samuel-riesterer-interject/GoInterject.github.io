---
title: Basics of Report Formulas
layout: custom
keywords: [report formula, column definitions, formatting range, walkthrough]
description: At the top of INTERJECT reports is a section called report formulas which handles the behavior of the report.
---

##  **Overview**
---
Inside INTERJECT tabular reports there is a hidden configuration section at the top of the worksheet. Notice in the following screenshot how the [ Customer Aging ](/wAbout/Customer-Aging.html) report from the Walk-through begins at row 14? Above row 14 is a section devoted to the report configuration. The **Report Formulas** section is a common place where INTERJECT Report Formulas are added to direct the behavior of the report. Most users of reports will not have any need to view this area. For advanced users, there are various reasons to access these formulas. 


###  Accessing the Report Formulas 

**Step 1:** For this walk-through, you will use the Customer Collections report located in the INTERJECT Demos folder of the [ Report Library ](/wAbout/Report-Library-Basics.html). 

![](/images/BasicsReportFormulas/01.png)

When the report is opened it will be blank. It is ready for any filters before pulling data. 

![](/images/BasicsReportFormulas/02.png)

**Step 2:** To see the formulas working behind INTERJECT, you need to [ Unfreeze ](/wPortal/INTERJECT-Ribbon-Menu-Items.html#unfreeze) the panes hiding them. Select the View ribbon and select  the **Freeze Panes** drop-down. Then choose the first operation, **Unfreeze Panes**. 

![](/images/BasicsReportFormulas/03.png)

**Step 3:** Now scroll up and see the Report Formulas section of the report. Notice that now all the rows are visible, starting at row 1. 

![](/images/BasicsReportFormulas/04.png)

###  Column Definitions 

Column Definitions define which columns of a spreadsheet will be populated with data. This is how INTERJECT knows where to place data within the spreadsheet. Moving column definitions will change where data is placed the next time it is pulled. 

You have full control of what column labels that are shown in the reports. Notice that the column labels in row 21 are directly below the coinciding column definition in row 2. Since this column label row is displayed for users, you can make the text more readable by, for example, adding spaces for the column name **30Days** to show in the report like **30 Days** . 

![](/images/BasicsReportFormulas/05.png)

**Step 1:** INTERJECT uses the column definitions in row 2 to determine where data is placed in the report. The labels in row 21 are ignored. To show this, move the **CustomerID** label in row 2 and place it in Column N, but do not move the column label in row 21. 

![](/images/BasicsReportFormulas/06.png)

**Step 2:** Now use [ **Pull Data** ](/wGetStarted/INTERJECT-Ribbon-Menu-Items.html#pull-data)to see where the **CustomerID** data is populated. 

![](/images/BasicsReportFormulas/07.png)

Notice that the **CustomerID** data is populating column N below the column definition. 

![](/images/BasicsReportFormulas/08.png)

**Step 3:** Put the CustomerID back where it belongs in Column B. First, clear the report so you can remove the CustomerID data already in column N. 

![](/images/BasicsReportFormulas/09.png)

**Step 4:** Move the **CustomerID** column definition value back to cell B2. 

![](/images/BasicsReportFormulas/10.png)

###  Formatting Range

The **Formatting Range** is the place designated to hold the formatting and formulas that will be copied down with the data in the report. When the report is populated, the formatting range is first copied down to the new rows in the report, along with any input text or formulas. Then the data specified in the Column Definition area is placed in the respective column. It is important to note, if the reporting range has values or formulas in the same column as the Column Definitions, it will be replaced with the data. 

A Formatting Range configuration is not required. If one is not specified in a Report Formula (discussed below), then the first row in the report is considered the Reporting Range. 

![](/images/BasicsReportFormulas/11.png)   

###  Report Formulas 

Report Formulas are a big part of how INTERJECT directs data in and out of the spreadsheets. For example, you can see here that the Customer Aging Report contains 4 formulas, a pull and 3 drills. 

![](/images/BasicsReportFormulas/12.png)

The first formula is a **Report Range** formula and will pull the data from a data source to the spreadsheet. There are other, similar, Report Formulas to pull data, such as [ ReportFixed() ](/wIndex/ReportFixed.html) , [ ReportVariable() ](/wIndex/ReportVariable.html) and [ ReportLookup() ](/wIndex/ReportLookup.html) . You will look at these later. The screenshot above also shows three [ ReportDrill() ](/wIndex/ReportDrill.html) formulas that enable [ drill ](/wGetStarted/INTERJECT-Ribbon-Menu-Items.html#drill-on-data) functionality. A drill lets us navigate to another spreadsheet report based on the context selected. 

Another type of Report Formula is the [ Save ](/wGetStarted/INTERJECT-Ribbon-Menu-Items.html#save-data) formula which is not shown here. This type of Report Formula enables an application developer to build save back features into our reports, such as saving back comments on financial variances to a central database so they can be presented in other reports. 

Each of these formulas is activated by its corresponding button in the [ INTERJECT Ribbon menu ](/wGetStarted/INTERJECT-Ribbon-Menu-Items.html). 

<img class="img-modal" src="/images/BasicsReportFormulas/13.png" onclick="zoom_img(this)" />

If a report has multiple Pulls or Saves, INTERJECT will activate them in order from left to right, for the first 1000 rows of the spreadsheet. If a report has multiple drills, then, when activating a drill, INTERJECT will show a popup to select one specifically. INTERJECT orders that list based on the order of the drills in the report from left to right and top to bottom. 

<img class="img-modal" src="/images/BasicsReportFormulas/14.png" onclick="zoom_img(this)" />

###  Hidden Parameters and Notes 

The Hidden Parameters and Notes section has two uses. First, it holds documentation on the configuration for other report writers to see. Second, it can contain hidden parameters and spreadsheet formulas that support the other areas of the spreadsheet report. In this example, the notes contain a basic overview of the report as well as what the drills do. 

<img class="img-modal" src="/images/BasicsReportFormulas/15.png" onclick="zoom_img(this)" />

This concludes the discussion of the basics of Report Formulas. Be sure to continue reading, since there are many advanced options to learn more about, which can be leveraged to create tailored reports and applications for the company's needs. 
