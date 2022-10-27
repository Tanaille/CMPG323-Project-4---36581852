# CMPG323-Project-4---36581852
### Testing and RPA project for CMPG323

<p align="center">
    <img src="https://seekvectorlogo.com/wp-content/uploads/2019/07/uipath-vector-logo-small.png">
</p>

The goal of this project is to automate the basic GUI CRUD operations of the API web frontend for user acceptance testing purposes.
This is enabled via the usage of UIPath Studio to develop the RPA workflows necessary to implement the automation.

### Basic information

API Web UI: https://connectedoffice-devicemanagement.azurewebsites.net/

### API Structure 
This API is composed of three primary controllers: 

- **Categories**  
Enables interaction with the product Category tables. 
- **Devices**  
Enables interaction with the Device tables. 
- **Zones**  
Enables interaction with the product Zone tables.

### API Access 
The API can be accessed via the web UI URL provided above. Credentials are saved within the UIPath project.

### Project details

This project utilizes four primary flowcharts, each implementing several workflows. Each flowchart starts by invoking the Login.xaml workflow to launch a browswer window and log into the API web UI.

- Main.xaml - Displays the usage guide, function selection dialog and invokes the desired operation workflows
- Zones_Flowchart.xaml - Executes GUI CRUD operations for zones
- Categories_Flowchart.xaml - Executes GUI CRUD operations for categories
- Devices_Flowchart.xaml - Executes GUI CURD operations for devices
  
Each of the three operation classes (zones, categories and devices) has 4 workflows associated with it. They are named as follows:
- [Class]_Create.xaml - Creates items of that class
- [Class]_Read.xaml - Reads the details of each item in that class
- [Class]_Edit.xaml - Edits the details of each item in that class
- [Class]_Delete.xaml - Deletes all items of that class

Two utility workflows are also provided:
- Login.xaml - Opens a browser window, navigates to the API web UI and logs in with a user account (the password is entered as a SecureString, using the SecureText input activity)
- WriteResults.xaml - Invoked after every CRUD operation. For every completed operation, it writes the value "TRUE" to the specified Excel sheet in the appropriate cell next to the test case ID.

### Usage

Upon running the automation (either via UIPath Studio or the automation published via Orchestrator), the user is presented with a short usage guide explaining the run options.

![Usage guide](/screenshots/usage_guide.PNG)

After closing the guide, the user is prompted to select the run option they desire. The selected automation then executes.

![Automation selection](/screenshots/automation_selection.png)

### Miscellaneous technical details
- Each workflow is invoked within a try..catch block. The workflows are terminated by throwing a BusinessRuleException (which logs an information-level result). The throw is caught and handled by the catch statements, ensuring error-free execution of a sequence of workflows.
- Individual workflows can be executed from within UIPath Studio. However, vecause the workflows are design to attach to existing browswer windows, the Login.xaml workflow needs to be executed first in all cases, in order to launch the browswer and log into the web UI. Once the user is logged in and the browser is open, they may execute any individual workflow as needed. These workflows will terminate by throwing a BusinessRuleException (see above). This is intended.

### Deployment 
The automation has been deployed to UIPath Orchestrator (personal workspace) and can be launched using UIPath Assistant. Alternatively, users may run the project directly via UIPath Studio, or deploy it to their own Orchestrator workspaces from Studio.

![Running the published automation via UIPath Assistant](/screenshots/publish.PNG)

### Reference list
1. https://forum.uipath.com/t/uipath-community-edition-publish-issue/35629/2
2. https://docs.uipath.com/studiox/v2019/docs/publishing-automation-projects
3. https://docs.uipath.com/studio/v2020.4/docs/tutorials
4. https://forum.uipath.com/t/how-to-add-3-4-sequences-in-one-process-and-execute-it-sequentially/335780
5. https://www.linkedin.com/pulse/understanding-concept-workflows-uipath-manish-kumar/
6. https://docs.uipath.com/activities/docs/open-browser
7. https://stackoverflow.com/questions/1570422/convert-string-to-securestring
8. https://forum.uipath.com/t/how-to-pass-securestring-variable-as-string-format-variable-in-smtp-mail/75315
9. https://forum.uipath.com/t/how-to-convert-excel-to-datatable-in-uipath/321763
10. https://rpalearners.com/how-to-create-a-datatable-from-excel-in-uipath/
11. https://www.c-sharpcorner.com/article/introduction-to-flowcharts-in-uipath-rpa-and-create-a-number-guessing-applicat/
12. https://forum.uipath.com/t/cleaner-way-to-exit-from-invoked-work-flow/415462
13. https://docs.uipath.com/studio/docs/using-arguments
14. https://www.youtube.com/watch?v=wpu4vjI36pM
15. https://docs.uipath.com/activities/docs/for-each-row
16. https://rpalearners.com/how-to-update-a-row-item-in-a-datatable-using-uipath/
17. https://forum.uipath.com/t/click-all-same-buttons-in-webpage/471009
18. https://forum.uipath.com/t/clear-text-box-before-typing/55253
19. https://docs.uipath.com/activities/docs/input-dialog
20. https://forum.uipath.com/t/what-the-use-case-for-a-switch-vs-flow-switch/2781
21. https://penrako.com/eng/uipathconditions/
22. https://docs.uipath.com/activities/docs/navigate-to
23. https://forum.uipath.com/t/i-would-like-to-go-to-another-website-without-using-a-second-open-browser-activity/399226
24. https://forum.uipath.com/t/how-to-select-an-element-from-dropdown/77887
25. https://docs.uipath.com/activities/docs/select-item
26. https://forum.uipath.com/t/how-to-use-select-item-activity/2299
27. https://www.youtube.com/watch?v=I5owUVRS9FY	
28. https://docs.uipath.com/activities/docs/add-data-row
29. https://docs.uipath.com/activities/docs/manage-databases-in-excel
30. https://docs.uipath.com/activities/docs/lookup-data-table
31. https://docs.uipath.com/activities/docs/manage-data-tables
32. https://stackoverflow.com/questions/67962910/how-to-switch-on-a-string-in-uipath
33. https://docs.uipath.com/studio/docs/the-switch-activity
34. https://docs.uipath.com/orchestrator/v2016.2/docs/publishing-a-project-to-orchestrator-from-studio
