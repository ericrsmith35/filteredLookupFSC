# filteredLookupFSC
Updated lookupFSC to include Filters and Parent/Child lookups

3 additional parameters added

Filter on which field? - Name of the field to filter the lookup on
Filter Value - Value of field to filter by
'Parent' or 'Child' Lookup? - default is Parent
     
   If Child is entered, the filter value will be replaced by the value returned by the Parent lookup on the same screen. 
   Multiple Child lookups can be on a single flow screen and their values will be reset any time the Parent lookup changes.

 
 Example #1: Lookup a Case filtered by an Account where the ID is passed into the flow variable vInputAcctId
 
     Case Lookup
      I1_Object Name                    Case
      I2_Display Which Field?           Subject
      I3_Field Label                    Select Case
      I4_Output Which Field as Value?   Id
      I6_Filter on which field?         AccountId
      I7_Filter Value                   {!vInputAcctId}
      ---
      O1_Output Value                   {!vCaseId}
      
      
 Example #2: Lookup an Account and a Contact on the same screen and only select from Contacts from the selected Account
  
    Account Lookup
      I1_Object Name                    Account
      I2_Display Which Field?           Name
      I3_Field Label                    Select Account
      I4_Output Which Field as Value?   Id
      I5_'Parent' or 'Child' Lookup?    Parent
      ---
      O1_Output Value                   {!vAccountId}
      
    Contact Lookup
      I1_Object Name                    Contact
      I2_Display Which Field?           Name
      I3_Field Label                    Select Contact
      I4_Output Which Field as Value?   Id
      I5_'Parent' or 'Child' Lookup?    Child
      I6_Filter on which field?         AccountId
      ---
      O1_Output Value                   {!vContactId}      
