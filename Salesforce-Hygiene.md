This is an approximation of the Salesforce Hygiene page in this Power BI report. 
Field names and values are edited for confidentiality. 


HYGIENE SLICERS

 Stage Mismatches                     Nurture Accounts     Stale Next Steps     Stale Deals   
 [ ] Stage too high for Upside        [ ] 30 - 60 days     [ ] > 14 days        [ ] Show me   
 [ ] Stage too low for Forecast       [ ] 60 - 90 days     [ ] 7 - 14 days                    
                                      [ ] 90+ days                                                                           

MAIN TABLE

DR      | Stage        | Region     | Adjusted Stage Duration | Account Name | FLM       | Rep     | Fiscal Month | Week | Close Date | Licensing Program Type | Gross ASV | ARR      | Next Steps
--------|--------------|------------|-------------------------|--------------|-----------|---------|--------------|------|------------|------------------------|-----------|----------|------------
DR1001  | 05 - Forecast| Commitment | 15                      | Acme Corp    | Jane Doe  | John S  | M1           | WK2  | 2025-09-15 | New                    | $150,000  | $0       | Review on 2025-09-10
DR1002  | 04 - Forecast| Forecast   | 35                      | Beta Inc     | Tom Lee   | Mary K  | M2           | WK3  | 2025-10-01 | Renewal                | $300,000  | $250,000 | Call on 2025-09-20
DR1003  | 03 - Forecast| Commitment | 22                      | Gamma Ltd    | Jane Doe  | Peter R | M1           | WK4  | 2025-09-25 | Add On                 | $75,000   | $60,000  | Email on 2025-09-18
Total   |              |            |                         |              |           |         |              |      |            |                        | $525,000  | $310,000 |

