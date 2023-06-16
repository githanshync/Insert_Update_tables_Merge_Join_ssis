# Insert / Update in Oracle tables with SSIS.
Example of insert update in Oracle tables with Merge Join and Conditional Split from SSIS.
## Minimum requirements:
-	Visual Studio 2022 (import solution SQLServerTablesToOracle).
-	Oracle 12c or 19c (as target database).
-	Install Microsoft Connector for Oracle V1.2 (MicrosoftSSISOracleConnector-SQL22-x86.msi). https://www.microsoft.com/en-us/download/details.aspx?id=29284
-	Install SSIS for Visual Studio 2022 (Microsoft.DataTools.IntegrationServices.exe). https://marketplace.visualstudio.com/items?itemName=SSIS.MicrosoftDataToolsIntegrationServices
## To run the ssis package.
In the target database (Oracle), use the scripts from the "-Oracle_scripts" folder:
-	Create the user-schema "USERTEST".
-	Create the table PEOPLE (*PEOPLE.SQL*).
-   Insert rows in the table PEOPLE (*insertsPEOPLE.sql*).
-	Create the table PEOPLE_REP (*PEOPLE_REP.SQL*).
-   Insert rows in the table PEOPLE_REP (*insertsPEOPLE_REP.sql*).

## In the Visual Studio project:
In connection manager:
-	Update the "tns service name" field from Oracle Connection Manager (target database). 
-	And update the password for the user USERTEST in the password field.
- Update the "server or file name" field from OLE DB Provider.
- And update the password for the user USERTEST in the password field.

*Data flow:*

![Control Flow](https://github.com/githanshync/Insert_Update_tables_Merge_Join_ssis/blob/master/-img/design.PNG)

*Running package:*

![Control Flow](https://github.com/githanshync/Insert_Update_tables_Merge_Join_ssis/blob/master/-img/executing.PNG)

After the execution of the package, the PEOPLE_REP table will have 2 new rows inserted (personid 3270 and 3271) and the record will be updated with PERSONID = 1.
