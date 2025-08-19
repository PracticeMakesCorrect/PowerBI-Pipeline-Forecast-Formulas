This DAX formula tells the user what the Week Over Week (WoW) change for each deal has been. 
For example, if Business XYZ had a dollar value of $283,112 last week and this week it has a dollar value of $321,112, then it will display $38,000. 
By using conditional formatting in Power BI one can make it easy for the user to see whether it's a negative, neutral, or positive change.


```dax

Metric_Change_Justification = 
SWITCH(
    TRUE(),
    -- Moved Out (Active or Likely to Inactive/Lost/Excluded)
    (Prev_Status IN {"Active", "Likely"}) && 
    (Is_Shifted_Out || ISBLANK(Category) || Exclusion_Flag <> 0),
    "Active/Likely -> Inactive",

    -- Moved Out but Not in Active/Likely
    Is_Shifted_Out,
    "Shifted Out",

    -- New or Moved In to Active/Likely
    (Is_New || Is_Shifted_In) && Curr_Status IN {"Active", "Likely"},
    "New or Moved to Active",

    -- Status Upgrade (Low-Priority to Active/Likely)
    Prev_Status IN {"Low-Priority", "Low-Priority-Tracked"} && 
    Curr_Status IN {"Active", "Likely"},
    "Low-Priority to Active",

    -- Status Downgrade (Active to Low-Priority)
    Prev_Status = "Active" && 
    Curr_Status IN {"Low-Priority", "Low-Priority-Tracked"},
    "Active to Low-Priority",

    -- Value Change in Same Period
    Same_Period && Value_Difference <> 0 && 
    Curr_Status IN {"Active", "Likely"},
    "Value Adjustment",

    BLANK()
)

```



OUTPUT EXAMPLE BY DEAL ID
Note: the formula above is reponsible for the "Change Reason" column. Also, WoW Change displays $75K in the first row even though the dollar value of the opportunity didn't change. That's because once it moves into Change Reason Forecast/Won, it couunts as a positive addition to this week's forecast. 

![My Image](images/ByDeal.PNG)

OUTPUT EXAMPLE BY CHANGE REASON

![My Image](images/ByChangeReason.PNG)
