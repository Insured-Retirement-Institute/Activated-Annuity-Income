# Activated Annuity Income

Enabling annuity income to be reflected next to other sources of income for clients where financial professionals are currently showing their income.

Please refer to the [style guide](https://github.com/Insured-Retirement-Institute/Style-Guide) for technical governance of standards, data dictionary, and the code of conduct.

## Business Cases
The Digital-First for Annuity goal is to increase the net new number of financial professionals wanting to understand, transact, and manage annuities. This project will focus on the 93% of financial professionals that are not meaningfully transacting annuities. To do that, the industry needs to enable financial professionals to report annuity income in the tools that they are using for portfolio management, wealth management, the brokerage account. 

The industry needs to create a standardized, easy, way for reporting current and future income from annuities, which will allow any tool to seamlessly integrate annuity income projections into their comprehensive portfolio reports without requiring in-depth product knowledge, mapping, or complex calculations. THis standard will focus only on activated income. 

Problem:
Financial advisors face significant challenges presenting annuity income to their consumers in the same tool where their other products are managed. These challenges are due to… 
- Current inability to see activated income alongside traditional investments
- Current inability to see available income alongside traditional investments (Will be solved in a future standatd.)
-	Current inability to run long-term annuity income projections, preventing directionally accurate long-term income planning. (Will be solved in a future standatd.)
-	Custom work by carrier and by product is often required to support annuity products, creating barriers to integrating. 
-	Lack of standardization across different annuity products and carriers creates barriers to integration. 
-	Complexity of calculations, that very by carrier and product, creating barriers to integration. 

These barriers create missed financial planning and reporting opportunities, reducing advisors' ability to recommend annuities effectively or even manage the annuity (activation of riders, etc) or manage the consumer’s income planning discussions. Without visibility into annuity income, advisors are less likely to recommend annuities, despite their value. 


## User Story 1 - for Visualizing Income that has started for a single policy
Day1 Use Case 1: A portfolio management and reporting tool can be used for accurate income planning where the annuity short-term income (12 months) has been activated for inforce policies.  This use case shows baseline income to provide the near-accurate income for the next rolling 12 months including income that has started (income rider activated) or the contract has been annuitized . 

-  **User Story 1**: As a financial advisor, I want to get a snapshot in time in my portfolio tool for a single policy with near-accurate income planning that includes the inforce annuity to present a comprehensive look at activated income on the annuity over the next 12 months (rolling). 

## Day1 Use Case2 - Bulk response:  
A portfolio management and reporting tool can be used for accurate income planning where the annuity short-term income (12 months) has been activated for inforce policies.  This use case pulls bulk policies by firm and then agent to show baseline income to provide the near-accurate income for the next rolling 12 months including income that has started (income rider activated) or the contract has been annuitized . 

- **User Story 2**: for Visualizing Income that has started in bulk
Day1 Use Case 2: As a firm or agent, I want to get a snapshot in time for all of my contracts in bulk (by firm and then agent) for near-accurate income planning that includes the inforce annuity to present a comprehensive look at activated income on the annuity over the next 12 months (rolling). 

**Bulk Policy Request/Response:**
Get request will have parameters Firm ID (required), and Agent ID (optional)
Response information: same as the single with repeating the policyIncome block for each policy number that falls within the search criteria
•	Data saved to a file and accessed through a secure protocol. (Secure protocol tbd based on implementations)
•	Response options: Polling and WebHook  

## Implementation Notes: 
-	Near-accurate income means that some nuances may not be included but nuances will be called out in the disclaimer.
-	Payment amount (net and gross) started means, any living benefit that generates an income stream, payout or distribution, or annuitization (Systematic income related to a guarantee). To account for both and an indicator on what it is from, we landed on isIncomeRiderActivated and isAnnuitied.
-	Data the FP needs to know must be present:
-	Must know the payment schedule: last payment, amount of last payment and frequency. That number will be replicated for the frequency to get a near-accurate view of the income as it is known at that time. (see below feed back from FPs)
-	isIncomeRiderActivated: True or False
-	isAnnuitized: True or False
-	Last payment date
-	Net payment amount (required)
-	Gross payment amount (optional)
-	Frequency: (Annual -1, Semi-annual -2, Quarterly - 4, Monthly -12)
-	Nice to have: ContractAnniversaryDate – These values will be addressed in a micro-service for contract details at a later time. For day 1, the implementors have links to the positions file so this is not needed. 
- This data does not change during the day so it is not a real-time calculation that is needed. The data is needed for 1 policy or a group/bulk set of policies. It may be requested real-time or requested at night. 
-	Include in the request Policy number and cusip as optional to identify the policy uniquely. This is because there are rare situations where the same carrier has the policy number two times. Example: Policy number and cusip. If the policy is requested without the cusip and there is a duplicate policy at the carrier, respond back with error – duplicate policy, Please rerequest with cusip and policy. (TBD by Governance)

## Implementation Considerations
The sender and receiver will be defined by the implementors to address authorization and authentication. 

## Business Owners 
- Carrier Business Owner: Prudential - Christina Cuffari christina.cuffari@prudential.com; Amy Iliescu amy.iliescu@prudential.com, Corebridge - Tina Haley tina.haley@corebridgefinancial.com, Athene - Lana Nelson LNelson@athene.com, New York Life - Craig Fernicola Craig_Fernicola@newyorklife.com
- Carrier Technical Owners: Raja Kumarasamy raja.kumarasamy@corebridgefinancial.com; Raja Ganesan raja.ganesan@corebridgefinancial.com; Jessica Gideon jessica.gideon@prudential.com: Larry Hunt lhunt@athene.com
- Solution Provider Business Owner: SS& C- Justin Wayne justin.wayne@sscinc.com ; Liz Lanahan liz.lanahan@sscinc.com iCapital - Abhishek Damaraju Abhishek.Damaraju@icapitalnetwork.com;
- DTCC: Smith, Jeanann F. <jsmith@dtcc.com>; Costanzo, Tony <tcostanzo@dtcc.com>


## How to engage, contribute, and give feedback
- These working groups are occuring on ....
- Please contact the business owners or IRI (Hannah Pikus hpikus@irionline.org, Tammy Tibbs ttibbs@irionline.org; Katherine Dease kdease@irionline.org) to get added to the working group discussions. 

## Change subsmissions and reporting issues and bugs

Security issues and bugs should be reported directly to Katherine Dease kdease@irionline.org. Issues and bugs can be reported directly within the issues tab of a repository. Change requests should follow the standards governance workflow outlined on the [main page](https://github.com/Insured-Retirement-Institute).

## Code of conduct

See [style guide](https://github.com/Insured-Retirement-Institute/Style-Guide)
