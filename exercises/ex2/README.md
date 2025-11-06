# Exercise 2 - Create your first custom AI Agent in Joule Studio

In this exercise, we will first adjust our skills that have been created in the [previous exercise](/exercises/ex1/README.md) in order to build a custom Sales Order Completeness Agent. On top of that, the agent should be able to research potential shipping risks by performing a web search with our Perplexity API. We want to explicitly check for the following conditions in our sales order:
- Best Run Status should be set to completed
- IncotermLocation1 should not be empty
- The pricing date should not be older than 14 days.

In the end, the summary of our agent analysis will be saved into the custom field 'AI Remark' of the sales order.

## 💡 Understanding Joule Agents

**Joule Agents** represent the next evolution of enterprise automation — intelligent, autonomous systems that **plan, reason, and act** across multiple tools and systems to achieve complex goals.  
While **Joule Skills** execute predefined, deterministic operations, Joule Agents handle **multi-step, adaptive workflows**, deciding *what to do, when, and how* based on business context and user intent.

Functioning as orchestration layers, Joule Agents combine analytical reasoning with real-time decision-making. They use **Large Language Models (LLMs)** to interpret user requests, dynamically select relevant tools (including Joule Skills), and generate contextual responses — enabling **goal-oriented, conversational automation**.

Each Joule Agent is built around four key cognitive abilities:

1. **Planning** – The agent determines the best sequence of actions to achieve a business goal, orchestrating multiple tools or Joule Skills as needed.  
2. **Reflection** – The agent evaluates its own steps, identifies errors or missing data, and self-corrects to reach the desired outcome.  
3. **Tool Usage** – The agent dynamically invokes SAP Build Actions, Joule Skills, or other APIs to perform operations, retrieve data, or trigger systems.  
4. **Collaboration** – Agents can cooperate with other agents or human users, engaging in dialogue, confirmation, or validation when business logic requires oversight.

## Exercise 2.1 Modify the Joule Skills and create a new Joule Skill

After completing these steps, we will have adjusted our skills from exercise 1 in a minimal way to make the data consumable for the agent. For example, instead of just using the custom field in the skill, we now want to have an agent that is able to analyze all of the header fields from a sales order. 

1. Let's first open the skill for retrieval of sales order fields.
<br>![](/exercises/ex2/images/ex2.1-1.png)

2. For our agentic use case, we need to add an additional input to our skill.
<br>![](/exercises/ex2/images/ex2.1-2.png)

3. The agent needs to be able to read the country of the business partner from the sales order. For that, we need to add the expand parameter as a Skill Input. It is not need to set this input to required. 
<br>![](/exercises/ex2/images/ex2.1-3_new.png)

4. Now we need to again put the expand into the relevant input parameter of our action.
<br>![](/exercises/ex2/images/ex2.1-4.png)

5. Close the action details and delete the 'Send Message' tile as we want to provide all the sales order information to the agent instead of only selected header fields.
<br>![](/exercises/ex2/images/ex2.1-5.png)

6. Turn on the Joule-generated response.
<br>![](/exercises/ex2/images/ex2.1-6.png)

7. Open the 'Write Custom Field' skill. This time we want to write into our other custom sales order field. Open the trigger, go to 'Parameters' and click on 'Configure'.
<br>![](/exercises/ex2/images/ex2.1-7_neu.png)

8. Change the Best Run Status to 'AI Remark Query' and apply the changes.
<br>![](/exercises/ex2/images/ex2.1-8.png)

9. Now go to the action and click on the 'AI Remark Query' as the input for the parameter 'YY_AI_Remark_SDH'.
<br>![](/exercises/ex2/images/ex2.1-9.png)

10. The next step is to click on the 'Send Message' tile and open the message editor to adapt the custom message.
<br>![](/exercises/ex2/images/ex2.1-10.png)

11. Adapt the custom message to tell Joule that the custom field has been successfully written. This time, select the context from the Start Event instead of the API response.
<br>![](/exercises/ex2/images/ex2.1-11_neu.png)

12. The next step is to create a new Skill for our Perplexity API. Go to the 'Overview' section of our project, click on 'Create' and then 'Create Joule Skill'.
<br>![](/exercises/ex2/images/ex2.1-12.png)

13. Write the below description into the Skill.
<br>![](/exercises/ex2/images/ex2.1-13.png)

14. Let's first change the Skill Input Parameter in the 'Trigger' tile. Click on 'Configure'.
<br>![](/exercises/ex2/images/ex2.1-14.png)

15. We call the input parameter 'query', because we want the agent to formulate the relevant search query from the context. Click on 'Apply' to go back to the Trigger Parameters.
<br>![](/exercises/ex2/images/ex2.1-15.png)

16. In the Skill Outputs section, we define the response from the LLM as the output parameter. Click on 'Apply' to save the changes.
<br>![](/exercises/ex2/images/ex2.1-16.png)

17. Back in our skill, we need to add a new tile by clicking on the '+' button. Then, select 'Call Action'.
<br>![](/exercises/ex2/images/ex2.1-17.png)

18. If the action is not shown in the list, click on 'Browse All Actions'.
<br>![](/exercises/ex2/images/ex2.1-18.png)

19. Select the POST action with the name 'Create chat completion'.
<br>![](/exercises/ex2/images/ex2.1-19.png)

20. We need to create a new environment variable, because we are now using a different destination. 
<br>![](/exercises/ex2/images/ex2.1-20.png)

21. Give the variable a descriptive name, we call it 'perplexity' and click on 'Create'.
<br>![](/exercises/ex2/images/ex2.1-21.png)

22. In the Action Input, we need to pass our query from the Skill Input to the messages of our API call. Navigate to the 'content' parameter and select the 'query' from the Skill Input.
<br>![](/exercises/ex2/images/ex2.1-22.png)

23. Now go to the end node of the Skill and select the 'content' parameter from the API response. This is needed for Joule to access the result of the web search.
<br>![](/exercises/ex2/images/ex2.1-23.png)

## Exercise 2.2 Create the agent

In this step, we will create the agent. For this, we will need to write a prompt, choose an LLM and select the right tools for the agent.

1. In the overview section of our project, click on 'Create' and then 'Create Agent'. Give the agent a name and a description as shown below.
<br>![](/exercises/ex2/images/ex2.2-1.png)

2. The first step is to formulate Expertise and Instructions for the agent. You can experiment with different approaches, but here is a predefined prompt that you can use:

Expertise: 
```
You are an expert in reviewing a sales order for completeness and researching potential shipping risks.
```

Instructions:
```
Your goal is to check specific conditions for sales order header fields, then assess country-specific shipping risks. Write your summary into custom field `YY1_AIRemark`. Fetch the relevant data with the 'Retrieve Sales Order' tool, including the business partner information for the country of the buyer, by setting the expand parameter to '_Partner'. Then, execute the following tasks. 

Task A – Completeness:
- Best Run Status indicates closed/completed
- IncotermLocation1 not empty.
- `PricingDate` is less than 14 days old

Task B – Country news risk (last 14d):
- Use Perplexity to search: shipping delays, port congestion, customs strikes, sanctions, severe weather, conflict.
- Summarize 1–2 credible items (issue, place, date, source). Assign Risk: None/Low/Med/High with brief rationale.

Output:
- PATCH only custom field `YY1_AIRemark` via the Write Custom Field tool.
- Write one concise natural-language remark combining Task A+B using less than 200 characters. 
- No invented data. Use only provided tools and instructions.
```
  
<br>![](/exercises/ex2/images/ex2.2-2.png)

3. Now you can select the LLM of your choice. We decide to go with OpenAI as the provider, and 'GPT-4o' as the model. 
<br>![](/exercises/ex2/images/ex2.2-3.png)

4. We can enable additional pre- and post-processing steps for our agent. This will add task decomposition and output refinement as nodes for the agent reasoning. After that, we can click on the 'Add Tool' button on the right side of the screen to input our tools.
<br>![](/exercises/ex2/images/ex2.2-4.png)

5. Since we now have 3 skills in our project, we can enable these skills as tools for our agent. Finally, click on the 'Add' button to finish this part of the exercise.
<br>![](/exercises/ex2/images/ex2.2-5.png)

## Exercise 2.3 Deploy and test the Agent

In this step, we will release and deploy the agent into our user-specific environment. There, we will be first testing the agent in the standalone Joule instance before showing the results in our S/4HANA system.

1. Click on the 'Release' button on the top right of the screen.
<br>![](/exercises/ex2/images/ex2.3-1.png)

2. Click on 'Release'. 
<br>![](/exercises/ex2/images/ex2.3-2.png)

3. Make sure that you are in the released version of your project (next to the project name on the top of the screen) and click on the 'Deploy' button on the top right of the screen.
<br>![](/exercises/ex2/images/ex2.3-3.png)

4. Deploy the project into the user-specific environment and click on 'Upgrade'.
<br>![](/exercises/ex2/images/ex2.3-4.png)

5. Select the destinations as shown in the screenshot below and click on 'Deploy'.
<br>![](/exercises/ex2/images/ex2.3-5_new.png)

6. Open the Build Lobby again and go to the 'Control Tower' to open the 'Environments'.
<br>![](/exercises/ex2/images/ex2.3-6.png)

7. Open the your user-specific environment.
<br>![](/exercises/ex2/images/ex2.3-7.png)

8. Go to the 'Joule' section of the environment and open Joule Standalone by clicking on 'Launch'.
<br>![](/exercises/ex2/images/ex2.3-8.png)

9. Type in the below prompt and replace 87XXX with your specific Sales Order Number (*like Sales Order 87001*). To review the logs, click on the icon on the top right, right next to your user credentials.
```
Review Sales Order 87XXX
```
<br>![](/exercises/ex2/images/ex2.4-1.png)

11. Here you can review the logs of your agent execution.
<br>![](/exercises/ex2/images/ex2.4-2.png)

## Summary

Congratulations! 
You've now modified the already existing skills and created a new one for the Perplexity integration. In exercise 2, you created a new agent by formulating instructions and adding tools. Finally, the project was released and tested by the user.

Continue to - [Cleanup instructions](../cleanup/README.md)
