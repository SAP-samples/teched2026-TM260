
# Exercises
<!-- TOC -->

- [Exercises](#exercises)
- [Exercise 4 - Analyze custom code adaptation results of the ABAP Custom Code Migration agent](#exercise-4---analyze-custom-code-adaptation-results-of-the-abap-custom-code-migration-agent)

<!-- /TOC -->

# Exercise 4 - Analyze custom code adaptation results of the ABAP Custom Code Migration agent

In this exercise you will obtain the final custom code migration results from the ABAP Custom Code Migration agent for further user review.

1. Meanwhile the ABAP Custom Code Migration agent started in the Exercise 1 already finished the custom code migration and can be asked for the final report. Go to the GitHub Copilot chat and provide the following prompt: **show me the status of session *your session ID***. Use your agent session noted in the Exercise 1. The agent provides the final report.

 <br>![](/exercises/ex4/images/tm260_ex4_1_agent_final_report.png)

 In the final migration report you will get the new transport request, which contains the code changes done by the agent. The code changes are distributed on several tasks of the transport request, containing respectively the proposed code changes with high, medium and low confidence score. An additional task was created for the deterministic quick fixes. Navigate to the transport request provided by the agent to examine the code changes.

 2. In the *Transport Request Editor* click on the *Object Changes* tab: 

    <br>![](/exercises/ex4/images/tm260_ex4_2_agent_tr.png)

 3. Click through the objects in the object list and try to understand the code changes proposed by the agent.
    
    <br>![](/exercises/ex4/images/tm260_ex4_3_agent_object_changes.png)

    The next recommended steps for the custom code migration developer are to accept the code change proposals with high confidence score and activate the related custom code objects. Then review the code proposals with medium and low confidence score and adjust them before applying the changes or revert back if the code changes are not acceptable.
 
 4. After reviewing the changes in the *Transport Viewer* fine tune the code changes and activate them. For this open every ABAP program in the editor in change mode and activate the changes. Again a transport task will be created for your change.
    
 5. Trigger ATC run again over your package using the context menu *Run As > ABAP Test Cockpit with ...* and use the S4HANA READINESS_2025 check variant. There will be still a few findings in the ATC result table, because they are false positives and cannot be detected correctly by the ATC check. Use the context menu *Apply Pseudo Comment* menu on every finding. After you finished that rerun the ATC again. The *ATC Problems View* should now show no findings.

    <br>![](/exercises/ex4/images/tm260_ex4_4_atc_no_findings.png)

**🎉Congratulations! You have finished all exercises.**

Go to start - [TM260 Migrate and modernize your custom code from ECC to RISE with agentic AI ](../../README.md)
