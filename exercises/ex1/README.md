# Exercise 1 - Migrate your custom code from SAP ECC to SAP S/4HANA using SAP Joule for Developers, ABAP AI capabilities

### Scenario Overview
In this exercise you will learn how to speed up understanding of the custom code in an SAP ECC system and the issues, which must be resolved in your custom code during SAP S/4HANA conversion. Thereby you will utilize the Custom Code Migration app on SAP BTP and the AI-based skills to understand the code and the SAP S/4HANA related ABAP test cockpit (ATC) issues. You will also find out the issues which can be solved already on your SAP ECC system and learn how to fix them. Next you will use the ABAP development tools for Eclipse (ADT) for code analysis and adaptation on SAP S/4HANA system. Thereby you will utilize SAP Joule for Developers, ABAP AI capabilities to understand the custom code, the findings of the ATC check run for S/4HANA readiness and get code proposals for AI-based code fixes. After that you utilize the ADT MCP tools to apply AI-based code fixes. Finally you will use the ABAP Custom Code Migration agent on SAP Business AI Platform to automate your custom code migration to SAP S/4HANA compliant code.

## 🔴 Important Information

> **📌 Note**   
> We’ve got sessions running in several locations → please pick the one that’s right for you!

> **📌 Replace the two digits to get your group number:**
> * ZTM260_EXERCISES_**0##** → **01** → **40** → **SAP TechEd Berlin, October 27, 2026**  (e.g ``ZTM260_EXERCISES_019``)
> * ZTM260_EXERCISES_**0##** → **41** → **80** → **SAP TechEd Berlin, October 29, 2026**  (e.g ``ZTM260_EXERCISES_079``)
> * ZDT260_EX_**1##** → **100** → **170** → **ASUG TechConnect**  (e.g ``ZTM260_EXERCISES_119``)


### Exercise 1.1 Use Custom Code Migration app on SAP BTP to analyze your code in SAP ECC system for SAP S/4HANA

By following these steps you will get to know the Custom Code Migration app on SAP BTP using the existing custom code migration project for SAP S/4HANA analysis of custom code of the SAP ECC system. You will use the AI-based code explanation to understand the business purpose of the ABAP programs and AI-based explanation to understand the issues of the SAP S/4HANA related ATC custom code findings.


1. Navigate to the SAP Fiori Launchpad of the system **`S01`** and logon to it using the system connection URL, your user and password provided by the instructors. Navigate through as shown below on the screenshots to access the custom code migration project **Teched TM260 S/4HANA Readiness HE4** in the Custom Code Migration app and click on it.
   
   <br>![](/exercises/ex1/images/tm260_ex1_1_see_ccm_proj.png)

2. Click on the *Number of Findings* to display all SAP S/4HANA related ATC issues in the custom code of the SAP ECC system.
   
   <br>![](/exercises/ex1/images/tm260_ex1_2_number_findings.png)
   
3. Then navigate to the *Compact Filter*:
   
   <br>![](/exercises/ex1/images/tm260_ex1_3_click_filters.png)

4. Filter the *Findings* view to display the S/4HANA related ATC issues only in your package **`ZTM260_EXERCISES_###`** by proceeding as follows. Click on the *Adapt Filters*, then add the filter for a package, enter your package name and click *OK*:
 
   <br>![](/exercises/ex1/images/tm260_ex1_4_choose_pkg.png)

   <br>![](/exercises/ex1/images/tm260_ex1_4_choose_pkg_2.png)

5. Change the filter view back to visual filters by clicking on the *Visual Filter*.
 
   <br>![](/exercises/ex1/images/tm260_ex1_5_visual_filter.png)
   
6. Play around with the Custom Code Migration app to get to know it better. For example use different filters, settings in the *Findings* view to sort the issues, or find out how to download findings for upload to the SAP Readiness Check. If you want to display the source code of the code sample you will need to logon to the ABAP backend system **`HE4`** using your user **`TM260-###`**, and the password provided by the instructors.
 
   <br>![](/exercises/ex1/images/tm260_ex1_6_view_source.png)
   
7. Now use the AI-based code explanation in the Custom Code Migration app to analyse the business purpose of the ABAP program. This feature is targeted to support your migration decision and exclude the custom code, which is not required anymore on your new SAP S/4HANA system. In the *Findings* table select the line with the ABAP program **`ZTM260_MATERIAL_READ_###`** and click on the *Code Explain*.
 
   <br>![](/exercises/ex1/images/tm260_ex1_7_code_explain.png)

   You will get the information about the business purpose and processing logic of the ABAP program **`ZTM260_MATERIAL_READ_###`**. Scroll down and use the **Explain business purpose in detail** and **Explain processing logic in detail** options to understand the ABAP program in all details.
   
   <br>![](/exercises/ex1/images/tm260_ex1_8_show_code_explain.png)
   
9. Now use the AI-based explanation of the SAP S/4HANA related ATC issues in the Custom Code Migration app. This feature is targeted to help you grasp the root cause quickly without having to read through numerous SAP S/4HANA simplification information materials. In the *Findings* table select the line with the type conflict ATC issue in the ABAP program **`ZTM260_MATERIAL_READ_###`** and click on the *ATC Explain*:

    <br>![](/exercises/ex1/images/tm260_ex1_9_atc_explain_1_fle.png)

   Read the explanation to understand the type conflict issue with SAP S/4HANA filed length extension of 40 chars. The explanation is provided in the pop-up window along with the proposed step-by-step resolution and contains also referenced S/4HANA simplification materials. Referenced documents are offered as clickable links within the AI-based response for navigation to further details.

   <br>![](/exercises/ex1/images/tm260_ex1_10_atc_explain_fle.png)

   Now select the line with the syntactically incompatible change ATC issue in the same ABAP program **`ZTM260_MATERIAL_READ_###`** and click again on the *ATC Explain*:
   
    <br>![](/exercises/ex1/images/tm260_ex1_11_atc_explain_2_syntax.png)

   Read the explanation to understand the material number field length extension issue for BAPI_MATERIAL_GETALL.
   
   <br>![](/exercises/ex1/images/tm260_ex1_12_atc_explain_syntax.png)

   Select further lines in the *Findings* table and try to understand the source code and SAP S/4HANA related ATC issues using *Code Explain* and *ATC Explain* AI-based features in the Custom Code Migration app.

10. Now take a look again at visual filters and discover in the filter for **Findings by Quick Fix Availability** the new filter option *AI Quick Fixes*. Use this filter option to display the SAP S/4HANA related ATC findings in the code samples of your package, for which AI-based code proposals (AI quick fixes) are available:

    <br>![](/exercises/ex1/images/tm260_ex1_13_ai_fixes.png)
   
11. Now remove (unselect) the **Findings by Quick Fix Availability** filter and discover the new visual filter **Findings by Transferable Quick Fix**. This filter is related to the ATC findings, which can be fixed already on your SAP ECC system prior to the SAP S/4HANA system conversion. Currently transferable quick fixes are available for the ATC issues related to data elements, which were removed in SAP S/4HANA, and for missing ORDER BY in SELECT statements.
    
    <br>![](/exercises/ex1/images/tm260_ex1_14_ecc_fixes.png)
    
   For upload to the ECC system you would need to download transferable quick fixes from the *Findings* table using the menu *Export Transferable Quick Fixes* **ℹ️ NOTE: Do not execute the download, just take a look at the context menu**
   
   <br>![](/exercises/ex1/images/tm260_ex1_15_export_ecc_fixes.png)

11. **📌 NOTE: The following final step is provided only to demonstrate the end-to-end process for the transferable quick fixes. Please do not try to perform it, because it can be executed only on an SAP ECC system.**
   
   After downloading the ATC issues from the Custom Code Migration app that can be fixed using transferable quick fixes, they must be uploaded to the SAP ECC system, and the transferable quick fixes must be executed there using the SAP GUI transaction ATC.
   
   <br>![](/exercises/ex1/images/ecc_atc_transaction.png)

   <br>![](/exercises/ex1/images/ecc_gui_atc_qf.png)
   
   Please find more details about transferable quick fixes in the blog post [Automated custom code adaptation for SAP S/4HANA and SAP HANA on your SAP ECC system](https://community.sap.com/t5/technology-blog-posts-by-sap/automated-custom-code-adaptation-for-sap-s-4hana-and-sap-hana-on-your-sap/ba-p/14461544).

### Exercise 1.2 Analyze and adapt your code on SAP S/4HANA system using AI capabilities

By following these steps you will first run ATC to analyze your custom code package for SAP S/4HANA. Then you will use the Joule explain capability to understand the logic of some sample ABAP programs, use the Joule ATC finding explain capability to understand the issues of the ATC check run, use the Joule code proposal capability to suggest the AI based code fixes. Finally you will utilize ADT MCP tools to analyze your code samples and apply AI based code fixes.

1.	Start Eclipse on your desktop and switch to the ABAP Perspective.
   
   <br>![](/exercises/ex1/images/tm260_ex1_16_start_eclipse.png)

2.	Create ABAP project by selecting **File** > **New** > **ABAP Project** and connect to the system **`HE4`**. Use client **`400`**, your user **`TM260-###`**, and the password provided by the instructors.   

   <br>![](/exercises/ex1/images/tm260_ex1_17_create_abap_project.png)
   
3. Add your exercises packages for your group **`###`** to the *Favorite Packages*.
   
   <br>![](/exercises/ex1/images/tm260_ex1_18_add_fav_pkgs.png)

4.	Now logon to Joule using the menu *Window > Show View > Joule* using the system **`S01`**, your user and your password provided by instructors. After successful browser logon you will be able to see your Joule for developers digital assistant in the Joule window. 

   <br>![](/exercises/ex1/images/tm260_ex1_19_joule_logon.png)

As next you will try out the basic Joule skills for code migration: code explanation, ATC findings explanation, and AI-based code fixes.

5. Now execute the ABAP program **`ZTM260_MATERIAL_READ_###`** using the context menu *Run As > ABAP Application (F8)*. Enter the material number *123* for example and click on the *Execute* button. You will get the ABAP runtime error, indicating, that there is a type conflict during a function module call. This is an S/4HANA-related issue that illustrates a common scenario in which custom code that previously worked in an ECC system no longer functions correctly in S/4HANA due to simplifications in S/4HANA, resulting in runtime dumps, syntax errors, and other issues. These issues must be fixed.

    <br>![](/exercises/ex1/images/tm260_ex1_26_run_dump.png)

6.	Now use the ABAP program **`ZTM260_MATERIAL_READ_###`** to try out the AI-based features for code migration in the ABAP development tools for Eclipse. Start with the AI-based explanation of the code. For this use the context menu *Joule > Explain*:

   <br>![](/exercises/ex1/images/tm260_ex1_20_joule_explain.png)

Joule will explain the business purpose and processing logic and will list all called objects. You can further deep dive into details using **Explain business purpose in detail** or/and **Explain processing logic in detail** features in the Joule chat window. You can follow on details of the processing logic to understand the program better for the upcoming adaptation.

   <br>![](/exercises/ex1/images/tm260_ex1_21_joule_explain_result.png)

7. Now perform the SAP S/4HANA readiness checks with ATC for your package **`ZTM260_EXERCISES_###`**. For this use the context menu *Run As > ABAP Test Cockpit With...*, enter the **S4HANA_READINESS_2025** check variant and execute ATC check run.

   <br>![](/exercises/ex1/images/tm260_ex1_22_run_atc_pkg.png)
   
   You get a table with the SAP S/4HANA related ATC findings in the ABAP programs of your package and can see in the column *Joule Support*, which ATC findings are supported by Joule. The icons with sparkles placed before ATC findings indicate the findings, for which the AI-based code proposals can be obtained.
   
   <br>![](/exercises/ex1/images/tm260_ex1_23_joule_support.png)

8. Now try out the Joule support for the ATC findings of the chosen ABAP program **`ZTM260_MATERIAL_READ_###`**. For the convenience purposes use in the ATC results table on the *Findings* the context menu *Group By > Object* to group the issues by the ABAP source code objects where they occur. Then select the ABAP program **`ZTM260_MATERIAL_READ_###`** and use the context menu *Joule > Explain* on its first ATC finding. Read and understand the explanation provided by Joule along with proposed resolution steps.

    <br>![](/exercises/ex1/images/tm260_ex1_24_joule_atc_explain_1.png)

   Do the same also for the second ATC finding:

   <br>![](/exercises/ex1/images/tm260_ex1_25_joule_atc_explain_2.png)

   Try out the Joule explanation of the SAP S/4HANA related ATC findings also for further findings of the ATC result.
   
 9. Let's now fix the ATC findings in the chosen ABAP program **`ZTM260_MATERIAL_READ_###`** using AI-based code fixes. For this select the second ATC finding (with the type-conflict check title) and use the context menu *Joule > Get Code Proposal*. Joule will use its /fix skill and present the AI-generated code proposal. Click the *Apply* button to show the code review dialog (FYI: the *Insert* button would insert the AI code proposal directly into the source code without code review dialog).
  
      <br>![](/exercises/ex1/images/tm260_ex1_26_joule_click_apply_qf.png)

    You will see the same code review dialog, which you probably already know from using deterministic quick fixes. On the left side the original source code is displayed, whereby on the right side you see the refactored source containing the code proposal. Click on the *Finish* button to apply the changes.

      <br>![](/exercises/ex1/images/tm260_ex1_27_joule_code_review.png)

   You can now *Save* and *Activate* your adjusted ABAP program **`ZTM260_MATERIAL_READ_###`**. For this create a new transport request, where you will store your changes. **🔴 Important - you will reuse this transport request to adapt the code sample of the next exercise**.
      
   <br>![](/exercises/ex1/images/tm260_ex1_28_joule_code_after_qf.png) 
      
   After rechecking your ATC result using the context menu *Recheck* on the ABAP program **`ZTM260_MATERIAL_READ_###`** in the ATC result table
    
   <br>![](/exercises/ex1/images/tm260_ex1_29_joule_code_after_qf_atc_recheck.png)  

   you will see that the first issue still persists. This is a false-positive, which can be suppressed with the pseudo comment. Use the context menu *Apply Pseudo Comment* and *Save* and *Activate* your ABAP program **`ZTM260_MATERIAL_READ_###`**.
   
   <br>![](/exercises/ex1/images/tm260_ex1_30_pseudo_comment.png)   

   Finally recheck your ATC result using the context menu *Recheck* on the ABAP program **`ZTM260_MATERIAL_READ_###`**. All issues are resolved. 
 
 <br>![](/exercises/ex1/images/tm260_ex1_31_recheck_source_solved.png)   

10. Now you will use GitHub Copilot and ADT MCP tools to check and adapt the ABAP program **`ZTM260_VBUK_SELECT_###`** for SAP S/4HANA. First verify, that the ADT MCP Server is enabled and GitHub Copilot can use it. For this use the menu *Window > Preferences*.
    
    Navigate to *ABAP Development -> MCP Server* and click the *Apply and Close* button.

    <br>![](/exercises/ex1/images/tm260_ex1_32_start_mcp_server.png)

    Navigate to *GitHub Copilot > Model Context Protocol* and enter the ADT MCP Server configuration as follows.**🔴 Important - make sure that you enter the provided JSON code snippet to the right place and not miss the final two curly braces** 

    <br>![](/exercises/ex1/images/tm260_ex1_33_co_enter_mcp_server.png)
    
   Enter this code and copy and paste the token from the MCP server preferences above.
   
   ```json
   "adt-mcp-server": {
      "url": "http://localhost:2234/mcp",
     "requestInit": {
         "headers": {
           "Authorization": "Bearer <copy & paste your token from the MCP server preferences>"
         }
       }
     }
   ```
   After that you will get below in the tools window the **adt-mcp-server** node displayed and can expand it to see all MCP tools, exposed by the ADT MCP Server. Among them there are also the ATC tools, which you will use. Click on the *Apply and Close* button. You have finished the ADT MCP server configuration and can start using the ADT MCP tools in the GitHub Copilot.
   
   <br>![](/exercises/ex1/images/tm260_ex1_34_co_see_mcp_tools.png)

11. Now use GitHub Copilot and ADT MCP ATC tools to check and adapt for SAP S/4HANA the ABAP program **`ZTM260_VBUK_SELECT_###`**. Open the GitHub Copilot using the menu *Copilot > Open Chat*. Select the ***Claude Sonnet 5.0*** model in the GitHub Copilot.
    
   <br>![](/exercises/ex1/images/tm260_ex1_35_co_open_chat.png)

   Enter the prompt **Check **`ZTM260_VBUK_SELECT_###`** with S4HANA_READINESS_2025** into the chat. The GitHub Copilot calls the ADT MCP tool to detect all opened projects in your development environment (if there are multiple, it will request to choose the project) and will execute the ATC run. You will be requested to allow the GitHub Copilot to execute the MCP tool. Just click on the *Continue*.

   <br>![](/exercises/ex1/images/tm260_ex1_36_co_first_prompt_migrate.png)

After executing the ATC run with S/4HANA_READINESS_2025 check variant the GitHub Copilot will fetch the result by calling the ADT MCP tool **abap_atc_get_result**. You will see, that there are 4 ATC findings, and all of them can be fixed using deterministic quick fixes. The GitHub Copilot will prompt, if these ATC findings must be fixed now and will need a transport request to store the changes.

   <br>![](/exercises/ex1/images/tm260_ex1_37_co_atc_run.png)

  Now prompt the GitHub Copilot to apply the deterministic quick fixes and provide the transport request number which you have created above to change the ABAP program **`ZTM260_MATERIAL_READ_###`**. The GitHub Copilot will use again the ADT MCP tools to apply the quick fixes, rerun the ATC check and request the final result. All issues are now fixed.

   <br>![](/exercises/ex1/images/tm260_ex1_38_co_atc_run_finished.png)

   Verify that the ABAP program **`ZTM260_VBUK_SELECT_###`** is adapted for SAP S/4HANA and examine the results of the deterministic quick fixes by opening the source code in the editor.

   <br>![](/exercises/ex1/images/tm260_ex1_39_co_final_result.png)

   You are done.
   
12. Now orchestrate execution of AI-based code fixes with GitHub Copilot. The ABAP Program **`ZTM260_ACCOUNTING_###`** for example has the ATC finding in your findings table, for which an AI-based code fix can be obtained. Enter the prompt **Check **`ZTM260_ACCOUNTING_###`** with S4HANA_READINESS_2025** into the chat. After executing the ATC run with S/4HANA_READINESS_2025 check variant the GitHub Copilot will fetch the result by calling the ADT MCP tool **abap_atc_get_result**. You will see, that there is one ATC finding, which can be fixed using AI quick fix. The GitHub Copilot will ask, if this ATC finding must be fixed now and will need a transport request to store the changes.

   <br>![](/exercises/ex1/images/tm260_ex1_40_co_second_prompt_migrate.png)

Now prompt the GitHub Copilot to apply the AI fix and provide the transport request number which you have created above to change the ABAP program **`ZTM260_MATERIAL_READ_###`**. The GitHub Copilot will use the ADT MCP tool **abap_atc_apply_ai_fix** to apply the AI fix. Since this AI-based code proposal has a medium confidence score, it will not be applied directly, but inserted as a comment. 

   <br>![](/exercises/ex1/images/tm260_ex1_41_co_ai_fix_applied.png)

  Now you can review the proposed change and decide either to accept it or not. You can also make manual adjustments to the code proposal.

   <br>![](/exercises/ex1/images/tm260_ex1_42_co_code_review.png)

   Try out to fix also further ATC findings from the ATC results table using GitHub Copilot and ADT MCP tools with a similar prompt as above.
   
### Exercise 1.3 Automate your custom code migration using ABAP Custom Code Migration agent

By following these steps you will first configure the MCP tools of the ABAP Custom Code Migration agent to be used by the GitHub Copilot. Then you will use ABAP Custom Code Migration agent to automate analysis and adaptation of your code samples for SAP S/4HANA.

1. Use the menu *Window > Preferences*. Navigate to the *GitHub Copilot > Model Context Protocol* and enter the MCP Server configuration as follows.**🔴 Important - make sure that you enter the provided JSON code snippet to the right place and don't forget to put the comma before ADT MCP server configuration**. 

    <br>![](/exercises/ex1/images/tm260_ex1_49_agent_config.png)
    
   Enter this code and copy and paste it before the ADT MCP server entry. Replace **`###`** with your location and group number.
   
   ```json
    "ccm-agent-1": {
      "url": "https://ccm-single-pod.c-932234c.kyma.ondemand.com/mcp",
      "requestInit": {
        "headers": {
          "Authorization": "Bearer <<TOKEN>>",
          "sap-adt-destination": "H4TECH_###"
        }
      }
    },
   ```
   After that you will get below in the tools window the **ccm-agent-1** node displayed and can expand it to see all MCP tools, exposed by the MCP server for the agent. Click on the *Apply and Close* button. You have finished the MCP server configuration and can start using the MCP tools of the agent in the GitHub Copilot.
   
3. Go to the GitHub Copilot chat and provide there the following prompt **Migrate the package **`ZTM260_EXERCISES_###`** using ATC check variant S4HANA_READINESS_2025**. Allow the **start_migration** MCP tool of the agent to run. Once migration is started, a new session id is issued for your agent session. Note it for your future requests. Now the agent started custom code migration, which will require some execution time. Meanwhile you can continue with the Exercise 2.
   
   <br>![](/exercises/ex1/images/tm260_ex1_50_agent_start.png)

4. **Optional:** after some time you can ask the agent about the status of code migration by providing the following prompt in the GitHub Copilot chat: **show me the status of session *your agent session***. The agent will report back on the current status of code migration:

    <br>![](/exercises/ex1/images/tm260_ex1_51_agent_check_status.png)


### Summary

You've now got to know the AI-based capabilities of the Custom Code Migration app on SAP BTP for explanation of legacy code and S/4HANA related ATC issues and learned how to identify the issues which can be solved on your SAP ECC system via transferable quick fixes. You have learned how to speed up your code adaptation on SAP S/4HANA system using Joule AI capabilities for code explanation, ATC finding explanation and code proposal (AI-based code fix), and how to automate mass adaptation of custom code for SAP S/4HANA by the ABAP Custom Code Migration agent.
Continue to - [Exercise 2 - Adapt your custom code to clean core.](../ex2/README.md)


