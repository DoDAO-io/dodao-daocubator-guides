## Header
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.

---

## Function Calls (Astro)


## What are Custom Function Calls?

## **What are Custom Function Calls?**

Every UI Dapp has in-built features that can be used to perform certain functions. However, there are some functions that are not included on the UI(to limit the scope of work) and would require calling smart contract functions(creating “custom functions” in Astro) to perform such operations.

On [AstroDAO](https://app.astrodao.com/), the interface is designed to interact with sputnik smart contracts so that DAOs can perform various functions like creating a proposal within the DAO, funding the DAO, creating polls, and creating bounties. This allows DAOs to manage their affairs more efficiently and with less hassle. These functions have been built into the interface and with the click of a button, DAOs can perform various functions (some of which have been highlighted above) that are part of the regular activities of the DAOs.

There are however cases where a DAO needs to perform other functions that are not part of what the AstroDAO interface provides such as interacting with other DAOs in terms of voting on the proposals of other DAOs or sending vote requests to other DAOs. Such functions do not have a predefined UI to complete them so they are done by creating **custom** **function calls** on AstroDAO.

An example is DAOcubator DAO voting on a proposal in another DAO such as DoDAO. In this guide, you’ll learn how to create simple custom function calls on AstroDAO.

    


---
## Evaluation





##### Which of these is a reason for having custom function calls on AstroDAO?  

- [ ]  To carry out poll voting
- [ ]  To aid creation of proposals
- [x]  To perform functions that are not available on the AstroDAO UI
- [ ]  To perform functions that are on the AstroDAO UI

    


---
## Use Case 1 - Voting on Proposals

## **Use Case 1 - Voting on Proposals**

Generally, voting is one of the key activities of DAOs and AstroDAO has provided a very simple interface that allows members of DAOs to vote on proposals by the DAO of which they are a part. There are also other cases where a DAO could be a member of the council of another DAO and therefore, has the right to vote on proposals in the other DAO. 

In this case, the AstroDAO User Interface (UI) does not provide a visual way to go through the process of voting. So, to complete this function, a custom function call has to be triggered on AstroDAO. 

**Example Use Case**
We want to create a Poll in DAOCubator University and want another DAO(DoDAO) to vote on it

Details:-
* Given - DoDAO is a council member of DAOCubator University 
* We want to now create a poll on DAOCubator University and want DoDAO(which is a DAO) to be able to vote in the poll
* For this DoDAO(a DAO) will create a proposal of type “Custom Function Call” and will populate the required information which links the DAOCubator University’s poll 
* Members vote on that “Custom Function Call” proposal, and if it passes, then it is counted as a vote on DAOCubator University’s poll  

The following steps will show you how to create a function call on DoDAO linked to a Poll created on DAOCubator University. All steps shown below are for test purposes.

**Create a Poll on DAOCubator**
1. Visit the DAOCubator page on AstroDAO and click on the green ‘+’ sign
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/create_new_proposal.jpg" alt="Add a Proposal"/>
</div>

2. Create a Poll on DAOCubator by selecting “Propose a Poll”
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/propose_a_poll.jpg" alt="Propose a Poll"/>
</div>

3. Fill in the description and click on “Propose”
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/propose_a_poll_completed.jpg" alt="Propose a Poll Completed"/>
</div>

**Create a “Function Call” proposal on DoDAO**
4. Open DoDAO and click on proposal type and select Function Call
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/function_call.jpg" alt="Function Call"/>
</div>

5. Fill in the description of the proposal, input the smart contract address, Method Name, and JSON code
* Description: Sample: Vote on this Proposal
* Link: The link to the poll created on [DAOCubator](https://app.astrodao.com/dao/test-daocubator-university.sputnik-dao.near/proposals/test-daocubator-university.sputnik-dao.near-3)
* Smart Contract Address: test-daocubator-university.sputnik-dao.near
* Method: act_proposal
* JSON: Write the JSON code using the proposal ID number when creating the proposal to vote on the proposal. You can either approve or reject by writing the following code snippet:

        For Approval:
        {

        "id": proposalId,

        "action": "VoteApprove"

        }

        For Rejection:
        {

        "id": proposalId,

        "action": "VoteReject"

        }

In this case, we will approve the proposal
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/details_on_the_function_call.jpg" alt="Details on Function Call"/>
</div>

6. Leave the value of TGas as 150 and click on “**Propose**”.

**Vote on “Function Call” Proposal**
7. Vote on the Custom Function Call Proposal created for it to be approved.
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/function_call_approved.jpg" alt="Function Call Approved"/>
</div>

**See DoDAO’s vote on DAOCubator University’s poll** 
8. Finally, see the poll and you will see DoDAO’s vote on it.
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/test_poll.jpg" alt="Completed Poll"/>
</div>

Congratulations! The voting process is complete.


    


---
## Evaluation





##### Which of these is not a pre-built function on AstroDAO?  

- [ ]  Funding a DAO
- [ ]  Creating a Poll
- [x]  Requesting votes from other DAOs
- [ ]  Creating Bounties





##### An example of a function that can be done with Custom Function Calls on AstroDAO is?  

- [x]  Voting on Proposals by a DAO on other DAOs
- [ ]  Sending funds to a NEAR wallet
- [ ]  Creating a Poll
- [ ]  Creating a DAO





##### When creating a Function Call on AstroDAO, which of these is NOT a field to be filled out?  

- [ ]  Description
- [ ]  Smart Contract Address
- [ ]  Method
- [x]  TGas

    


---
## Use Case 2 - Send Vote Request

## **Use Case 2 - Send Vote Request to other DAOs**

Another use case for a Custom Function call can be when a DAO on AstroDAO sends a voting request to another DAO to vote on a proposal by creating a custom function call. This process works for DAOs who are Council members of the DAO the proposal was created for.

For example, assuming DAOCubator is a member of the Council at DoDAO, we can send a Custom Function Call to DAOCubator to vote on a proposal created on DoDAO.

To engage in this process, follow the steps highlighted below:

1. Go to the DAO page that you want to request a vote from. In this case, that will be DAOCubator, and click on the green ‘+’ sign.
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/create_new_proposal.jpg" alt="Add a Proposal"/>
</div>

2. Select Function Call from the Proposal Type drop-down menu
<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/function_call.jpg" alt="Function Call"/>
</div>

3. Input the description of the proposal, a link to the proposal to be voted on, input the smart contract address, Method Name, and JSON code just like in the previous step
* Description: Sample: Requesting a vote from your DAO on this Proposal
* Link: This should be a link to the poll to be voted on e.g. samplelink.dodao.sputnik-dao.near/292
* Smart Contract Address: dodao.sputnik-dao.near
* Method: act_proposal
* JSON: Write the JSON code using the proposal ID number when creating the proposal to vote on the proposal. You can either approve or reject by writing the following code snippet:

        For Approval:
        {

        "id": proposalId,

        "action": "VoteApprove"

        }

        For Rejection:
        {

        "id": proposalId,

        "action": "VoteReject"

        }

<div align="center">
<img src="https://raw.githubusercontent.com/DoDAO-io/dodao-daocubator-guides/main/images/custom_function_calls/request_a_vote_from_other_DAOs.jpg" alt="Request Vote from other DAOs"/>
</div>

4. Leave the value of TGas as 150 and click on “**Propose**”.

The DAO (DAOCubator) will now be able to vote on the proposal sent for voting.


    


---
## Evaluation





##### When sending a voting request to a DAO, what information is provided in the link field?  

- [ ]  A link to the smart contract
- [x]  A link to the poll to be voted on
- [ ]  A link to the DAO
- [ ]  A link to the proposer address





##### The format for the “ID” provided in the JSON code is?  

- [ ]  Text
- [ ]  Date
- [ ]  Complex code
- [x]  Number





##### What is the value of the TGas when creating a custom function call?  

- [ ]  50
- [ ]  80
- [x]  150
- [ ]  100

    


---
## Conclusion

## **Conclusion**

We have learnt how to simply create custom function calls in this guide when it comes to voting on proposals and inviting other DAOs to vote on proposals created by the inviting DAO. For more information about how to work with Custom Function Calls on AstroDAO, kindly watch this [video](https://youtu.be/x4wxon7NX4w).

Some other use cases for function calls on Astro include:
* Buy NFT from Mintbase
* Buy NFT from Paras
* Transfer NFT from another DAO

This means that DAOs can now buy or mint NFTs directly from AstroDAO. By just writing a simple function call, the function can be performed easily. This is why function calls are quite incredible.

You can now go ahead and create your own custom function calls at any time of your choice.


    


---
## Footer
This is the course header. This will be added on top of every page. Go to [DoDAO.io](https://www.dodao.io) to know more.
    
