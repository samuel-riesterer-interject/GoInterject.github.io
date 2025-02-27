---
title: Budget Template
layout: custom
keywords: [Training, Budget, Budget Template]
description: 
---

## Overview

**Purpose**: This is the primary tool used for managing Budgets. This tool can be downloaded and customized in your local environment.

**Filter Options**:

* **District** - *Required*. Individual district. Cannot use district ranges or groupings
* **YYYY-MM** - *Required*. Needs to be in YYYY-MM format
* **Currency** - *Optional*. Blank defaults to your home district currency. Other options are USD and CAD.
* [ **Base Year** ](#base-year-and-fincube) - *Required*. Used in the pull. Drop-down filter ranges from *Aug Proj -> Dec Act*<br><br>
[ *Retain Rows - Related Parameters (used in the pull)* ](#retain-rows-and-how-it-works)
* **Retain Rows** - *Required*. Drop-down filter includes *Yes*, *No-Show Last Saved*, *No-Show Prior Bud*. If *Yes*, the Input columns will not wipe out on the pull.
* **Retain Comments** - *Required*. Drop-down filter includes *Yes* and *No*. If *Yes*, pulling in on the report will not wipe out comments not yet saved to the database.
* **Insert at End** - *Required*. Drop-down filter includes *Yes* and *No*. If *Yes* and **Retain Rows** is also *Yes*, then new accounts get added at the bottom of their grouping.<br><br>
[ *Summary and Detail Accounts - Related Parameters* ](#summary-and-detail-level-accounts)
* **Insert By Full Acct** - *Required*. Used in the pull. Drop-down filter includes *Yes* and *No*. For *No*, new accounts are aggregated at the summary level and dropped in.
* **Zero Out Missing Accts** - *Required*. Used in the save. Drop-down filter includes *Yes* and *No*. For *Yes*, accounts missing from the template are zeroed out. For *No*, missing accounts will keep their amounts, and any Summary level accounts are offsetted to include the missing accounts automatically.

![](/images/WCNTraining/Budget/BudgetTemplate_FullView.png)

## Input Field Explanations

### Base Year and Fincube

The **Base Year** drop-down filter changes how Actuals and Projections for the current year are pulled in from Fincube. For example, the screenshot below shows the *Aug Proj* option, which pulled in Actuals from January -> July, and Projections from August -> December.

![](/images/WCNTraining/Budget/BudgetTemplate_BaseYear01.png)

If we change the **Base Year** to *Aug Act*, August will pull in as Actual instead.

![](/images/WCNTraining/Budget/BudgetTemplate_BaseYear02.png)

### Retain Rows and how it works

With **Retain Rows** on *Yes*, any inputs in the Input columns will remain when the template is refreshed, or even if the report is cleared. If it is *No*, the Input columns will copu either the Budgets saved to the current Budget Year or last Year' (depending on the alternative option).

For and example with **Retain Rows** *Yes*, the screenshot below shows a formula used on the *50020-600-00* account.

![](/images/WCNTraining/Budget/BudgetTemplate_RetainRowsBeforeClear.png)

We clear the report, and afterwards we see that not only have all of the rows remain, but the formula is still there.

![](/images/WCNTraining/Budget/BudgetTemplate_RetainRowsAfterClear.png)

The **Retain Comments** on *Yes* will keep any comments saved in the template, even if there are different comments saved in the database.

If a new account is added to the Template with **Retain Rows** set to *Yes*, the setting for **Insert at End** dictates if the new account is added where it would normally go or get inserted at the end.

For example, if *50045-600-00* is added to the Template while **Insert at End** is set to *No*, it is nestled between the 50035 and 50050 accounts.

![](/images/WCNTraining/Budget/BudgetTemplate_InsertAtEndNo.png)

Otherwise if **Insert at End** is set to *Yes*, the added account is added at the bottom. Use this if you use formulas, so that newly added accounts do not mess them up.

![](/images/WCNTraining/Budget/BudgetTemplate_InsertAtEndYes.png)

>**Things to Remember**
>* After the first pull, the **Retain Rows** will automatically be set to *Yes*, to preserve your file changes.

### Summary and Detail level accounts

A new feature to the Budget Template is the ability to pull/save to Detail and Summary level accounts at the same time.

#### Pulling Summary and Detail levels together
On the pull, the **Insert By Full Acct** drop-down option dictates if the missing accounts are added on the Summary or Detail level. When **Retain Rows** is set to *Yes*, this permits you to pull in accounts on a different level than the ones you already have in your template.

Let's go through the following example. In the screenshot below, we see four account combinations for the 36009 account.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetailPullStart.png)

With **Retain Rows** set to *Yes* and **Insert By Full Acct** set to *No*, we delete the 36009-000-00 and 36009-600-00 rows.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetail_SummaryPrep.png)

When we pull on the tool now, the two detail rows 36009-000-00 and 36009-600-00 are summarized into one row, with the account header of 36009 alone. 36009-000-00 had $1,000 amounts for all months, and 36009-600-00 had $2,000 for all months. Together they have $3,000 for all months.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetail_SummaryPull.png)

>**Things to Remember**<br>
>For this to work, **Retain Rows** MUST be set to *Yes*. Otherwise, if **Retain Rows** is set to *No* and you pull, it will pull in ALL accounts on the Detail Level.

#### Saving Summary and Detail levels together

When saving with Summary and Detail level accounts on the same template, the Summary level accounts are saved to the *000-00* version of the summarized account. Depending on the **Zero Out Missing Accts** setting, the Detail level accounts already in the database will either be zeroed out or remain unaltered.

Let's use the example accounts we used from earlier. Let's update the summarized account for 36009 to $3,500 for all months.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetailSaveStart.png)

First we save with **Zero Out Missing Accts** set to *No*, and pull in all detail rows by setting **Retain Rows** to *No* and **Insert By Full Acct** to *Yes*.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetail_ZeroOutNo.png)

The Budget saved to 36009-000-00 is the *offset* of $3,500 per month (summarized amount) and $2,000 per month for 36009-600-00 (amounts in database). This updated the $1,000 in the database 36009-000-00 to $1,500, so that the summarize amount matches what was saved AND preserves the amount already assigned to 36009-600-00.

If we had set **Zero Out Missing Accts** set to *Yes* instead, the pull on detail would have looked like this instead.

![](/images/WCNTraining/Budget/BudgetTemplate_SummaryDetail_ZeroOutYes.png)

Now 36009-000-00 has the full $3,500 for each month, and 36009-600-00 has been zeroed out because it was not in the template.

>**Things to Remember**
>* If there are other accounts you delete from your template, they will be zeroed out as well if **Zero Out Missing Accts** is set to *Yes* (even if they do not have summary level account present in the template).
>* When saving with a Summary level account (only Acct is present), you cannot also save to the same account with *000-00* included. The save thinks the two accounts are the same, and will be marked as duplicates.

## The Autocalcs

The majority of accounts in your template will be marked **Manual Input** in the *Bud Method* column (column J). Some of the other accounts will have something different in this column, and are considered **Autocalcs**.

![](/images/WCNTraining/Budget/BudgetTemplate_Autocalcs.png)

There are many different types of Autocalcs, but the main thing to know is that you cannot edit them with the **Budget Template**. These accounts are managed by Corporate. Notice also that any Manual Input account is highlighted yellow, and the Autocalcs are grayed out.

## Do I have security rights to Save from the Budget Template?

Only people in the District Position Assignment (DPA) for the District in Toolbox can save to this file. Your Division Controller can add you if you are not already in the DPA.

![](/images/WCNTraining/Capital/CapitalInput_DPANavigation.png)

![](/images/WCNTraining/Capital/CapitalInput_DPAWindow.png)

## Budget Template and the Control Center

Based on your position in the DPA for the district, you will have a certain level of access to this report. The types of levels you may be on are: **A/C**, **Dist**, **Div**, **Reg**, or **Corp**.

Budget is locked at these levels in the **Control Center**, in the N column. In the example below, District 2050 is locked at the Reg Level.

![](/images/WCNTraining/Budget/BudgetUpload_ControlCenter1District.png)

If an A/C level user tried saving to 2050 Budget, they would be stopped with the following message.

![](/images/WCNTraining/Budget/BudgetTemplate_LockLevelError.png)

You are able to save Budget as long as the Budget lock level is your level or below. Otherwise you will not be able to save Budget.

## After Corp Cutoff and after BOD

### After Corp Cutoff
If you save to Budget **After Corp Cutoff**, the numbers will still be updated in Target Center 2.0. However, they will not be synced through to Interject.

In this example, the *Corp Cutoff* date in Control Center is set to 11/3/2018.

![](/images/WCNTraining/Budget/BudgetUpload_CCAfterCorpCutoff.png)

We then try and upload a change to Budget using the **Budget Template** tool (after this date), and get the following popup message.

![](/images/WCNTraining/Budget/BudgetTemplate_AfterCorpCutoffSave.png)
![](/images/WCNTraining/Budget/BudgetTemplate_AfterCorpCutoff.png)

So our changes here have been saved to Target Center 2.0, but they are not yet synced to Interject. Once the *Corp Cutoff* date is set to a Date/Time after our change or BOD, this change will then be synced to Interject.

We can use the the new tab [ UnsyncedChanges ](/bApps/InterjectTraining/Budget/BudgetChangeQuery_UnsyncedChanges.html) in the [ Budget Change Query Tool ](/bApps/InterjectTraining/Budget/BudgetChangeQuerySummary.html) to see our changes in Target Center 2.0.

![](/images/WCNTraining/Budget/BudgetTemplate_AfterCorpCutoffBudChangeQuery.png)

### After BOD
Once **BOD** for a Budget Year has been created, then any save from the **Budget Template** will not automatically sync to Interject again. This is just like with *After Corp Cutoff*, and while it is not in Interject it is in Target Center 2.0, and can be checked using the [ UnsyncedChanges ](/bApps/InterjectTraining/Budget/BudgetChangeQuery_UnsyncedChanges.html) tab in the [ Budget Change Query Tool ](/bApps/InterjectTraining/Budget/BudgetChangeQuerySummary.html). 

Once Corporate has versioned your change, the Budget amount will be sycned through to Interject.

## Common Save Errors

![](/images/WCNTraining/Budget/BudgetTemplate_Error_TemplateOutofDate.png)

*The template you are using is not current. You need to grab a new template from the Report Library.*

___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_LockLevel.png)

*The district is locked at a level higher than what you have access for. Work with your supervisor to unlock the file to your level.*


<button class="collapsible">Other Possible Save Errors</button>
<div markdown="1" class="panel">
![](/images/WCNTraining/Budget/BudgetTemplate_Error_LastPullFor.png)

*You last pulled for a district different from the one you are trying to save to. You need to repull for the district you want to save for with Retain Rows set to No. Be sure to make a copy to copy your notes/amounts over.*
        
___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_DistrictRequired.png)

*You need to use a valid District in the District parameter.*
       
___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_YearMonthRequired.png)

*The YearMonth is required, and needs to be in the YYYY-MM format.*

___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_AfterCorpCutoff.png)

*Your save updated Target Center 2.0, but is not synced to Interject yet. Once Corp Cutoff is updated to after your change or BOD is created, it will then be synced to Interject.*
        
___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_MissingColumns.png)

*Your local template is missing some of the required columns. Get a fresh copy of the template for the library, or reach out to support to fix your template.*

___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_InvalidAccount.png)

*The Account on the specified row is not a valid Account.*

___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_InvalidSyst.png)

*The Syst on the specified row is not a valid Syst.*
        
___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_InvalidSbst.png)

*The Sbst on the specified row is not a valid Sbst.*

___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_NonumericAmount.png)

*The amount in the provided column for the given row is non-numeric, and needs to be fixed (Proj12 = Bud12)*
        
___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_ExponentialAmount.png)

*There is a rounding error in the provided column for the given row, and needs to be fixed (Proj12 = Bud12)*

___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_Duplicates.png)

*Two of your rows have the same Account combination listed. It could be that one row is on the summarized level and you have the detail version 000-00 as well.*
        
___
![](/images/WCNTraining/Budget/BudgetTemplate_Error_BrokenFormula.png)

*There is a broken formula in the provided column for the given row, and needs to be fixed (Period 1 = Bud1)*
</div>
