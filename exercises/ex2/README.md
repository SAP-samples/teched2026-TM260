# Exercise 2 - Adapt your custom code to clean core

The clean core level concept, outlined in the Clean Core Extensibility [Clean Core Extensibility](https://www.sap.com/documents/2024/09/20aece06-d87e-0010-bca6-c68f7e60039b.html) whitepaper allows you stepwise transformation to clean core at your own pace.

This overview explains how ABAP test cockpit supports the clean core level concept.
<br>![](/exercises/ex2/images/tm260_ex2_0_cc_pic.png)

In this exercise, you get to know the SAP GUI-based ABAP program about the **Clean Core Planning** in the SAP S/4HANA system which was implemented to display the clean core level rating for the custom code objects in a package. Then you will analyze this program for clean core using ABAP test cockpit (ATC) in ABAP development tools for Eclipse (ADT) with the ATC check variant for clean core readiness and get familiar with the clean core related ATC findings and their matching to the clean core level concept. Finally you will use the GitHub Copilot and ADT MCP tools to adapt the ABAP program **Clean Core Planning** to the clean core level B.


### 🔴 Important Information

> **📌 Note**   
> We’ve got sessions running in several locations → please pick the one that’s right for you!

> **📌 Replace the two digits to get your group number:**
> * ZTM260_EXERCISES_**0##** → **01** → **40** → **SAP TechEd Berlin, October 27, 2026**  (e.g ``ZTM260_EXERCISES_019``)
> * ZTM260_EXERCISES_**0##** → **41** → **80** → **SAP TechEd Berlin, October 29, 2026**  (e.g ``ZTM260_EXERCISES_079``)
> * ZDT260_EX_**1##** → **100** → **170** → **ASUG TechConnect**  (e.g ``ZTM260_EXERCISES_119``)

### Exercise 2.1 Get to know the ABAP program about clean core planning and understand the clean core issues

The ABAP program **Clean Core Planning** was implemented to display the clean core status of the custom objects in a package. By entering the package name you can display for each object in this package its current clean core level, the planned clean core level and provide comments about the current status. By following these steps you will get to know the ABAP program **Clean Core Planning** and use ATC to analyze it for clean core. You will also understand its clean core related ATC findings.

1. Select the **`ZTM260_CLEAN_CORE_PLANNER_###`** program in your package **`ZTM260_EXERCISES_###`** and execute it using the context menu *Run As > ABAP application (F8)*. The package with custom code objects **ZTM260_CLEAN_CORE_SAMPLES** is provided automatically as input. Do not change the package name. Just click on the *Execute*.
   
<br>![](/exercises/ex2/images/tm260_ex2_1_run_cc_report.png)

2.	The **Clean Core Planning** ABAP program displays the classes of the package along with their current clean core level (*Actual* column) and planned clean core level (*Planned* column). In the column *Date* the target date of the planned clean core level is provided. The comment in the *Comment* column provides more details about the current status of the clean core migration of an object to the target clean core level. Play around with the ABAP program to understand its features. Double click on dates, comments, responsible persons to change these data.

<br>![](/exercises/ex2/images/tm260_ex2_2_learn_cc_report.png)
   
3. Execute clean core readiness checks by selecting the **`ZTM260_CLEAN_CORE_PLANNER_###`** ABAP program in your package, using the context menu *Run As > ABAP Test Cockpit with...* and providing the ATC check variant **ZTM260_CLEAN_CORE_READINESS** in the popup dialog. You will get the following clean core related ATC findings displayed in the *ATC Problems* view:
   
<br>![](/exercises/ex2/images/tm260_ex2_3_run_atc_cc_report.png)

4. Get familiar with all ATC clean core findings and their matching to the clean core level concept. For example updating of SAP tables (Update TADIR) leads to the ATC error, which corresponds to the clean core level D, selecting from SAP tables (Select TADIR) leads to the ATC warning and corresponds to the clean core level C, usage of classic APIs (cl_salv_events_table class of ALV Grid) leads to the ATC information message and corresponds to the clean core level B.
   
<br>![](/exercises/ex2/images/tm260_ex2_4_check_atc_results_cc_report.png)

### Exercise 2.2 Use GitHub Copilot and ADT MCP tools to migrate the ABAP program about clean core planning to clean core level B

By following these steps you will use the GitHub Copilot and ADT MCP tools to solve the clean core related ATC errors and warnings and adapt your **Clean Core Planning** ABAP program to the clean core level B.

1.	Go to the GitHub Copilot chat window. 🔴**IMPORTANT: select the ***Claude Sonnet 5.0*** model in the GitHub Copilot**. Provide the following prompt: **Check **`ZTM260_CLEAN_CORE_PLANNER_###`** with ATC variant ZTM260_CLEAN_CORE_READINESS**. The GitHub Copilot will use ADT MCP tools to run ATC with the ZTM260_CLEAN_CORE_READINESS check variant over your **`ZTM260_CLEAN_CORE_PLANNER_###`** ABAP program and will find out, that three ATC findings can be fixed using deterministic quick fixes. Prompt the GitHub Copilot to execute the quick fixes by providing the following (or similar) prompt **Apply the 3 deterministic quick fixes and use transport...**. You would need to create a new transport beforehand for the changes in the **`ZTM260_CLEAN_CORE_PLANNER_###`**. The GitHub Copilot will execute the quick fixes using the corresponding ADT MCP tool to fix the 3 clean core issues.

<br>![](/exercises/ex2/images/tm260_ex2_5_fix_atc_copilot.png)

2.	From the clean core related errors and warnings only one ATC error is left, which is related to the UPDATE of TADIR table. Let's look for the publicly available successor SAP API in the Cloudification Repository on the GitHub. Go to the [Cloudification Repository](https://sap.github.io/abap-atc-cr-cv-s4hc/) and search for the object TADIR with the object type FUNC. The Cloudification Repository provides information about the **TR_TADIR_INTERFACE** which is the SAP classic API, which can be used instead of directly updating the SAP table TADIR to adapt this code to the clean core level B.

<br>![](/exercises/ex2/images/tm260_ex2_6_cloud_repo.png)

3. Verify the business purpose of the **TR_TADIR_INTERFACE** by navigating to it in the *Project Explorer* and using the context menu *Joule > Explain* (you can also provide **/explain TR_TADIR_INTERFACE** prompt in the Joule chat:

   <br>![](/exercises/ex2/images/tm260_ex2_6_joule_explain.png)
   
4.	Now ask the GitHub Copilot to fix the ATC error with the UPDATE of TADIR using the successor SAP classic API **TR_TADIR_INTERFACE** by providing the following (or similar) prompt: **Fix the ATC error by replacing the Update statement with the function module TR_TADIR_INTERFACE**. After GitHub Copilot successfully applied the TR_TADIR_INTERFACE instead of UPDATE it reports that no errors and warnings are left.

<br>![](/exercises/ex2/images/tm260_ex2_7_fix_update_tadir.png)

5. Verify the outcome by rechecking ATC result (use the context menu *Recheck* on the Findings in the *ATC Problems* view or execute again ATC for the **`ZTM260_CLEAN_CORE_PLANNER_###`** with the check variant **ZTM260_CLEAN_CORE_READINESS**. Only information messages about usage of classic APIs will be reported, which correspond to the clean core level B. 

<br>![](/exercises/ex2/images/tm260_ex2_7_rerun_atc.png)
   
6. You have successfully adapted the ABAP Program about the **Clean Core Planning** to the clean core level B. Verify, that the ABAP program **`ZTM260_CLEAN_CORE_PLANNER_###`** still works correctly by executing it using the context menu *Run As.. > ABAP Program (F8)*
   

### Summary

You have now learned how to use ATC with the clean core related check variant in ADT to analyze your custom code in the SAP S/4HANA system for clean core and understand clean core issues. Finally you used GitHub Copilot and ADT MCP tools to solve clean core issues in your ABAP program and adapted it to the clean core level B.

Continue to - [Exercise 3 - Modernize your SAPGUI application about clean core planning with RAP and SAP Fiori UI](../ex3/README.md)


