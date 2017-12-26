# Welcome to LautarolTest!

**Dynamic rules and variables**  
 To set a dynamic variable to use in the task sequence, you can add a rule and then specify a value for each variable that you specify for the rule or add one or more variables to set without adding a rule. When you add a rule, you can choose from the following rule categories:  

 -   **Computer**: Use this rule category to evaluate values for Asset tag, UUID, serial number, or mac address. You can set multiple values, and if any value is true, then the rule will evaluate to true. For example, the following rule evaluates to true if the Serial Number is 5892087 regardless of whether the MAC address equals 26-78-13-5A-A4-22.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

-   **Location**: Use this rule category to evaluate values for the default gateway.  

-   **Make and Model**: Use this rule category to evaluate values for the make and model of a computer. Both the make and model must evaluate to true for the rule to evaluate to true.   

    Starting in Configuration Manager version 1610, you can specify an asterisk (**&#42;**) and question mark (**?**) as wild cards, where **&#42;** matches multiple characters and **?** matches a single character. For example, the string "DELL*900?" will match DELL-ABC-9001 and DELL9009.
