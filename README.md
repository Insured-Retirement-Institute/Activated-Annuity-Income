# Visualizing Annuity Income (Phase 1 Activated Income)

Enabling annuity income to be reflected next to other sources of income for clients where financial professionals are currently showing their income.

Please refer to the [style guide](https://github.com/Insured-Retirement-Institute/Style-Guide) for technical governance of standards, data dictionary, and the code of conduct.

## Business Case
A portfolio management and reporting tool can be used for accurate income planning where the annuity short-term income (12 months) has been activated for inforce policies.  This use case shows baseline income to provide the near-accurate income for the next rolling 12 months including income that has started (income rider activated) or the contract has been annuitized . 

## User Storie1 - for Visualizing Income that has started
Day1 Use Case 1: A portfolio management and reporting tool can be used for near-accurate income planning where the annuity short-term income (12 months) has been activated for inforce policies.  This use case shows baseline income to provide the near-accurate snap-shot of income for the next rolling 12 months including income that has started (income rider activated) or the contract has been annuitized . 

User Story 1: As a financial advisor, I want to get a snapshot in time in my portfolio tool for near-accurate income planning that includes the inforce annuity to present a comprehensive look at activated income on the annuity over the next 12 months (rolling). 

As a financial advisor, I want to get a snapshot in time in my portfolio tool for near-accurate income planning that includes the inforce annuity to present a comprehensive look at activated income on the annuity over the next 12 months (rolling). 

-	Income started means, any living benefit that generates an income stream, payout or distribution, or annuitization (Systematic income related to a guarantee)
-**	Data the FP needs to know must be present:**
-	Must know the payment schedule: last payment, amount of last payment and frequency. That number will be replicated for the frequency to get a near-accurate view of the income as it is known at that time. (see below feed back from FPs)
-	Indicator and industry clear definition for payment amount gross of taxes or net of taxes (either is fine but it needs to be disclosed)
-	**Implementor notes** -	Nice to haves:
-	An indicator in the timeline of important dates related to the contract income like when a step up or anniversary is eligible.
-	Separate guaranteed income/secure income from non-guaranteed/other income so the annuity is seen as a differentiator
  
## Implementation considerations
- bulk requests (research shows that carriers have over 80000 contracts in income payout. The bulk request could be a subset of that by firm, agent, a set of contracts, an IMO, etc.)
- Individual requests
- define: parameters for the messages (by firm, agent, contract list, etc)
-	The bulk method lives alongside a synchronous response such that the API will define batch / asynchronous and the parameters; or single synchronous and the parameters. This way the methods are reusing components. 


**Open standard model**  – presented by Athene, Larry Hunt. See diagram below.
-	API Request sent to carrier for the data, bulk request parameters defined. 
-	Carrier responds with 202 message (asynchronous), providing a url to check on the status of the data retrieval.
-	Requestor will check that url for an indication that the data is done processing. 
-	When the sender has completed their data processing, they will post to that url with another secure url to retrieve the data. 


## Business Owners 
Business Champions:  SS&C BlackDiamond (Justin and Liz) and ICapital Abhishek
- Carrier Business Owners:
- Prudential - Christina Cuffari christina.cuffari@prudential.com; Amy Iliescu amy.iliescu@prudential.com,
- Corebridge - Tina Haley tina.haley@corebridgefinancial.com,
- Athene - Lana Nelson LNelson@athene.com,
- New York Life - Craig Fernicola Craig_Fernicola@newyorklife.com
Technical Writers:
•	Corebridge: raja.kumarasamy@corebridgefinancial.com, Raja.Ganesan@corebridgefinancial.com; 
•	Prudential: Bradley Safer bradley.safer@prudential.com, Jessica Gideon <jessica.gideon@prudential.com>
•	Athene: Larry Hunt lhunt@athene.com; 
•	DTCC: Smith, Jeanann F. <jsmith@dtcc.com>; Costanzo, Tony <tcostanzo@dtcc.com>
•	iCapital: Abhishek Damaraju <abhishek.damaraju@icapitalnetwork.com>
•	SS&C BlackDiamond Wealth Solutions: Liz Lanahan <liz.lanahan@sscinc.com>; Justin Wayne <justin.wayne@sscinc.com>


## How to engage, contribute, and give feedback
- These working groups are occuring on ....
- Please contact the business owners or IRI (Hannah Pikus hpikus@irionline.org, Tammy Tibbs ttibbs@irionline.org; Katherine Dease kdease@irionline.org) to get added to the working group discussions. 

## Change subsmissions and reporting issues and bugs

Security issues and bugs should be reported directly to Katherine Dease kdease@irionline.org. Issues and bugs can be reported directly within the issues tab of a repository. Change requests should follow the standards governance workflow outlined on the [main page](https://github.com/Insured-Retirement-Institute).

## Code of conduct

See [style guide](https://github.com/Insured-Retirement-Institute/Style-Guide)
