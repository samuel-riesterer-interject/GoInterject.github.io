---
title: "Lab Create: Hiding Rows and Columns"
layout: custom
keywords: []
description:
---
##  **Overview**

The **ReportHideRowOrColumn()** function allows you to hide rows columns when they are not needed, for example if a row contains no data. In the first example, you will hide rows containing a total value of zero. The second example shows how to hide columns using the same function and for a similar reason. 

Once completed, these two features can be combined to hide, without eliminating, certain unneeded values and generally clean up the presentation of your financial reports. 

Both of these examples use the [ Customer Aging Detail  ](/wGetStarted/L3.4-Customer-Aging-Detail.html) report created in a previous walk through. You can navigate to the report by opening the **Customer Collections** report in the **Interject Demo** folder of the [ Report Library ](/wAbout/Report-Library-Basics.html). 

![](/images/L-Create-HideRowCol/01.png)

<br> 

###  **Hiding Rows**
 
**Step 1:** With the report opened to the **CustomerAgingDetail** tab, type "Market" into the company name filter and pull the data using Ctrl+Shift+J or the pull button. Notice on row 61 that Great Lakes Market has an entry with zero value. Rows like this are what we'll hide using the ReportHideRowOrColumn function.

![](/images/L-Create-HideRowCol/PullMarket.png)

**Step 2:**  Unfreeze the report formula panes by clicking the [ Quick Tools ](/wGetStarted/INTERJECT-Ribbon-Menu-Items.html) icon in the ribbon menu and selecting **Freeze/Unfreeze Panes**. 

![](/images/L-Create-HideRowCol/02.jpg)

<br>

**Step 3:** Insert a row above row **31**, and in cell **G30** type "For Backward Compatibility". Then in cell **H30** enter the formula **=ReportCalc()** and click **fx**. Enter the following into the Function Wizard:
- For **OnPullSaveOrBoth**, type **Pull**
- For **OnClearRunOrBoth**, type **Both**
- For **SheetOrWorkbook**, type **Sheet**
- For **SheetName**, type **CustomerAgingDetail**

[](/images/L-Create-HideRowCol/ReportCalc1.png)

**Step 4:** Type **Hide/Show Inv w/0 Subs** in cell **K27**. Then type **=ReportHideRowOrColumn()** in cell **L27**.

![](/images/L-Create-HideRowCol/TypeFormulas.png)

<br> 


**Step 5:** With cell **L27** still selected, click on the **fx** button to open the formula wizard.
- For **OnPullSaveOrBoth**, type **Pull**
- For **OnClearRunOrBoth**, type **Both**
- For **RowOrColumnRange**, enter **C43:C44** \(this will copy the formula through all rows of the report\)
- For **Disabled**, do not enter anything
- Hit OK

![](/images/L-Create-HideRowCol/FormWizard.png)

<br> 


**Step 6:** Now, in cell **C16**, type **=IF(P16=0,"Hide","Show")**. This specifies how to handle 0 values based on the formula entered for the subtotal column.  

![](/images/L-Create-HideRowCol/EnterForm.png)

<br> 


**Step 7:** Type **Market** into the customer name parameter again, then pull the report. Notice this time that the row containing no subtotal is now hidden. The data is not gone, it just isn't displayed in the report any longer.

![](/images/L-Create-HideRowCol/HideResult.png)

<br> 


###  Hiding Columns 

In this next example our goal is too hide the rows that have a payment expected date and show the rows without one. 

**Step 1:** To begin you will unfreeze the report using [ Quick Tools ](/wGetStarted/INTERJECT-Ribbon-Menu-Items.html). 

![](/images/L-Create-HideRowCol/21.png)

<br> 



You are now ready to begin editing the excel sheet. 

![](/images/L-Create-HideRowCol/22.jpg)

<br> 


**Step 2:** Select cell **M34** and **N34** and insert **Hide**. This is to hide the columns where the overdue charges are under 90 days since this data is not needed often. 

![](/images/L-Create-HideRowCol/23.jpg)

<br> 


**Step 3:** In cell **G30** input **Refresh Functions:**, in cell **G31** input **Hide Columns:**, and in cell **G32** input **Hide Rows:**, then right align all 3 cells to create labels for report formulas so they don't get mixed up. 

![](/images/L-Create-HideRowCol/24.jpg)

<br> 


**Step 4:** Select cell **O34** and insert **=IF(SUMIF(C47:C48,"Show",O47:O48) > 0, "Show", "Hide")**. 

![](/images/L-Create-HideRowCol/25.jpg)

<br> 


**Step 5:** In cell **G31** insert **Hide Columns:** and in cell **H31** input **=ReportHideRoworColumn()**

![](/images/L-Create-HideRowCol/26.jpg)

<br> 


**Step 6:** Select cell **H31** and click the **fx** button to open the function wizard 

![](/images/L-Create-HideRowCol/27.jpg)

<br> 


**Step 7:** In the function wizard input **Pull** in the field labeled **OnPullSaveOrBoth**, input **Both** in the field **OnClearRunOrBoth**. 

![](/images/L-Create-HideRowCol/28.jpg)

<br> 


**Step 8:** Select the filed **RowOrColumnRange** then select the three cells containing **Hide**. In this case it will be **M39:O39**. 

![](/images/L-Create-HideRowCol/29.jpg)

<br> 


**Step 9:** Select cells **M** **5** and **O** **5** and shift them left 3 cells by cutting the cells and pasting them into **J** **5** and **M** **5** respectively. 

![](/images/L-Create-HideRowCol/30.jpg)

<br> 


**Step 10:** Select cells **L19** and **N19** and shift them left 3 cells by cutting the cells and pasting them into **I19** and **K19** respectively. 

![](/images/L-Create-HideRowCol/31.jpg)

<br> 


**Step** **11:** Re-freeze the report 

![](/images/L-Create-HideRowCol/32.jpg)

<br> 


**Step 12:** In cell **H39** input **Market** and set cell **H42** to **No** and Pull the report 

![](/images/L-Create-HideRowCol/33.jpg)

<br> 


Your report is now finished and can hide rows and columns where the invoices have an expected date and there is no invoice that is 90 days past due. 

![](/images/L-Create-HideRowCol/34.jpg)


Finally, clear the report and upload it to the [ Report Library ](/wGetStarted/L-Create-UpdatingReportLibrary.html).
