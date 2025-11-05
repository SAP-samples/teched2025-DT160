# Exercise 1 - Create a Joule Skill to review and change custom fields in a sales order

In this exercise, you will learn how to work with Joule Studio to create custom Joule skills for reviewing and editing custom fields in a SAP Cloud ERP sales order. To achieve this, we are creating an environment, an action project and finally a Joule skill inside of a project.

## Exercise 1.1 Access the Build Lobby and create a new environment

After completing these steps you will have created an environment to isolate the skill development process for your specific user.

1. Click on the 'Control Tower'.
<br>![](/exercises/ex1/images/ex1.1-1.png)

2. Click on 'Environments'.
<br>![](/exercises/ex1/images/ex1.1-2.png)

3. Create a new environment.
<br>![](/exercises/ex1/images/ex1.1-3.png)

4. Create a new environment with the naming convention 'env_XXX'.
<br>![](/exercises/ex1/images/ex1.1-4.png)

5. Make sure that only your user has access to the environment by clicking on it and then the 'Share' button.
<br>![](/exercises/ex1/images/ex1.1-5.png)


## Exercise 1.2 Create the custom Joule Skills

After completing these steps, you have created two custom Joule Skills for retrieving and writing custom fields of a SAP S/4HANA Sales Order.

1. Click on the 'Create' button and then on 'Joule Skill'.
<br>![](/exercises/ex1/images/ex1.2.-1.png)

2. Create a new Joule Skill.
<br>![](/exercises/ex1/images/ex1.2.-2.png)

3. Choose the name project_XXX for the Skill and click on 'Review'.
<br>![](/exercises/ex1/images/ex1.2.-3.png)

4. Review your settings and click on 'Create'.
<br>![](/exercises/ex1/images/ex1.2.-4.png)

5. Now you created your project. Let's click again on 'Create' to either create a new Joule Skill or a Joule Agent. We will first start with a skill.
<br>![](/exercises/ex1/images/ex1.2.-5.png)

6. Give the skill a descriptive name and write a clear and concise description. This description is used by Joule during runtime to find the right skill. In our exercise, it is important that we are not interfering with the standard sales order skills, which is why we make clear that we want to access the custom fields of the sales order.
<br>![](/exercises/ex1/images/ex1.2-6.png)

7. In the Joule Skill, we can adjust the trigger of how the scenario is called. But first, we want to create our action. This can be done by clicking on the plus button.
<br>![](/exercises/ex1/images/ex1.2-7.png)

8. Then, we can click on 'Call Action'.
<br>![](/exercises/ex1/images/ex1.2-8.png)

9. Select the action 'Get entity from SalesOrder by key' to retrieve all the fields of a sales order.
<br>![](/exercises/ex1/images/ex1.2-9.png)

10. After selecting the action, we need to define a destination variable. Click on 'Create Destination Variable' on the right side of the screen.
<br>![](/exercises/ex1/images/ex1.2-10.png)

11. Give the destination variable an identifier (here: 's4') and click on 'Create'.
<br>![](/exercises/ex1/images/ex1.2-11.png)

12. Now, we will work on the trigger. Click on the respective box and then choose the column 'Parameters' on the right side. We will first configure our Skill inputs.
<br>![](/exercises/ex1/images/ex1.2-12.png)

13. In our exercise, we want to pass a Sales Order Number to Joule in order to receive the custom fields. That's why we are defining this input as in our screenshot and click on 'Apply' to continue.
<br>![](/exercises/ex1/images/ex1.2-13.png)

14. Next we are defining the Skill Outputs by clicking 'Configure' on the respective section.
<br>![](/exercises/ex1/images/ex1.2-14.png)

15. The result set from our action will be our Skill Output. For the type, we want to use the specific output schema of the action instead of some arbitrary data type. Scroll down and select the respective schema of the action. 
<br>![](/exercises/ex1/images/ex1.2-15.png)

16. Click on 'Apply' to continue.
<br>![](/exercises/ex1/images/ex1.2-16.png)

17. In this step, we want to use our Skill Input as a parameter for our action. Click on the action box and then on the 'Inputs' section. The Sales Order Number from our Skill Input should be added to the 'SalesOrder' parameter (Step 3 & 4).
<br>![](/exercises/ex1/images/ex1.2-17.png)

18. As the final step, we want to configure a custom message to the end users. Click on the plus button to add an additional step and select 'Send Response'.
<br>![](/exercises/ex1/images/ex1.2-18.png)

19. Then, click on 'Send Message'.
<br>![](/exercises/ex1/images/ex1.2-19.png)

20. Click on the 'Send Message' box and open the message editor on the right side of the screen.
<br>![](/exercises/ex1/images/ex1.2-20.png)

21. In the message editor, you can configure any kind of predefined message structure. Here, we are defining an illustrated message and add the Sales Order Number into the title by accessing the context of the Skill with the '<>' button.
<br>![](/exercises/ex1/images/ex1.2-21.png)

22. Additionally, we want to add an Action Button to navigate the user into the respective Sales Order. We are using the URL for changing sales orders (https://my426786.s4hana.cloud.sap/ui#SalesOrder-change?SalesOrder=<order-no>) and dynamically add the Sales Order number from our context into the URL.
<br>![](/exercises/ex1/images/ex1.2-22.png)

23. Finally, in the 'End' node we need to add the result object from our Skill Output.
<br>![](/exercises/ex1/images/ex1.2-23.png)

24. Since we have defined a predefined response structure, we can go back to our Trigger and deactivate the button that lets Joule generate the response.
<br>![](/exercises/ex1/images/ex1.2-24.png)

25. We will now repeat some of the steps to also have a skill that is writing into the custom fields of our sales order. Go back to the 'Overview' section of our Skill and create a new one as in Step 5.
<br>![](/exercises/ex1/images/ex1.2-25.png)

26. Give again a clear and descriptive description to our write Skill.
<br>![](/exercises/ex1/images/ex1.2-26.png)

27. We can again deactivate the button for Joule's embedded response generation, because we will again create a custom response.
<br>![](/exercises/ex1/images/ex1.2-27.png)

28. Add a new action to the Skill.
<br>![](/exercises/ex1/images/ex1.2-28.png)

29. This time, we will choose the PATCH endpoint 'Update entity in SalesOrder'.
<br>![](/exercises/ex1/images/ex1.2-29.png)

30. Let's define the Skill Inputs in the Trigger of our Skill.
<br>![](/exercises/ex1/images/ex1.2-30.png)

31. In addition to the Sales Order number, we will also have the name of our custom field as part of our input. This time, we don't need to define a Skill Output.
<br>![](/exercises/ex1/images/ex1.2-31.png)

32. Go to the Action Input and add the Sales Order Number into the respective API parameter ('SalesOrder'). 
<br>![](/exercises/ex1/images/ex1.2-32.png)

33. Do the same for our custom field.
<br>![](/exercises/ex1/images/ex1.2-33.png)

34. Add a new step by clicking on the plus button and choose 'Send Message' as in the first Skill.
<br>![](/exercises/ex1/images/ex1.2-34.png)

35. Open the Message Editor.
<br>![](/exercises/ex1/images/ex1.2-35.png)

36. Let's define a simple confirmation for the end user that the custom field has been written with a new value. Click on 'Save' to finalize the creation of the second custom Skill.
<br>![](/exercises/ex1/images/ex1.2-36.png)

## Exercise 1.3 Deploy the custom Skill and test it 

Once the Skill has been created, we can release and deploy the project. Then, the user will be able to first test the Skills in an isolated environment and afterwards share this environment with our S/4HANA system to experience the custom skill there.

1. In the 'Overview' section of the project, click on 'Release' on the top right of the screen.
<br>![](/exercises/ex1/images/ex1.3-1.png)

2. Click on 'Release' again. This will save a 'Snapshot' of our project before the deployment.
<br>![](/exercises/ex1/images/ex1.3-2.png)

3. Go to the released version of our project by selecting it in the drop down on the top of the screen.
<br>![](/exercises/ex1/images/ex1.3-3.png)

4. Choose your user-specific environment and deploy the project into this. 
<br>![](/exercises/ex1/images/ex1.3-4.png)

5. Select the shown destination (for dry run choose 'S4_SalesOrder_v4') and click on 'Deploy'.
<br>![](/exercises/ex1/images/ex1.3-5.png)

6. Go back to the Build Lobby, access the Control Tower and go to the 'Environments'.
<br>![](/exercises/ex1/images/ex1.3-6.png)

7. Access your user-specific environment.
<br>![](/exercises/ex1/images/ex1.3-7.png)

8. Go to the 'Joule' column of your environment and click on 'Launch'.
<br>![](/exercises/ex1/images/ex1.3-8.png)

9. Now you are accessing a standalone version of Joule. Type in a similar user prompt as in the screenshot and submit your message. 
<br>![](/exercises/ex1/images/ex1.3-9.png)

10. If we want to test the second Skill, we don't even need to define the sales order number again since Joule is able to retrieve this from the message history.
<br>![](/exercises/ex1/images/ex1.3-10.png)

11. The skills are working as expected.
<br>![](/exercises/ex1/images/ex1.3-11.png)

12. Go back to your environment and click on the 'Share' button.
<br>![](/exercises/ex1/images/ex1.3-14.png)

13. Before sharing the Skill with our S4 Joule instance, we want to make sure that only our user has access to the Skill in order not to interfere with the skills of the other participants. Click on 'Cancel' to go back to your environment.
<br>![](/exercises/ex1/images/ex1.3-15.png)

14. Now click on the settings button on the right side.
<br>![](/exercises/ex1/images/ex1.3-12.png)

15. Turn on 'Share Environment Capabilities' to deploy the Skill into our S/4HANA Joule instance.
<br>![](/exercises/ex1/images/ex1.3-13.png)

16. Go to the S/4HANA system, open the Joule chat window by clicking on the Joule icon on the top of the screen and start testing your skills.
<br>![](/exercises/ex1/images/ex1.3-16_neu.png)

## Summary

You've now created two custom Joule Skills for reading and writing custom fields of a sales order. We will use parts of these skills in our second exercise where we will create a custom agent to do a completeness check on a sales order.

Continue to - [Exercise 2 - Create your first custom AI Agent in Joule Studio](../ex2/README.md)
