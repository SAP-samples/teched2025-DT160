# Exercise 2 - Exercise 2 Description

In this exercise, we will adjust our skills that we created in exercise 1 in order to build a custom Sales Order Completeness Agent. Our goal is to retrieve the sales order information and apply specific checks on some of the fields. On top of that, the agent will gather information about the country of our business partner and then apply a web search to look for the latest news surrounding this country. The summary of the completeness check from our agent will be saved into the custom field 'AI Remark' of the sales order.

## Exercise 2.1 Modify the Skills

After completing these steps, we will have adjusted our skills from exercise 1 in a minimal way to make the data consumable for the agent. For example, instead of just using the custom field in the skill, we now want to have an agent that is able to analyze all of the header fields from a sales order. 

1. Let's first open the skill for retrieval of sales order fields.
<br>![](/exercises/ex2/images/ex2.1-1.png)

2. For our agentic use case, we need to add an additional input to our skill.
<br>![](/exercises/ex2/images/ex2.1-2.png)

3. The agent needs to be able to get the business partner information from the sales order. For that, we need to set the expand parameter to '_Partner'. We don't need this all the time which is why the parameter is NOT required. 
<br>![](/exercises/ex2/images/ex2.1-3.png)

4. Now we need to again put the expand into the relevant input parameter of our action.
<br>![](/exercises/ex2/images/ex2.1-4.png)

5. Close the action details and delete the 'Send Message' tile as we want to provide all the sales order information to the agent instead of a predefined message.
<br>![](/exercises/ex2/images/ex2.1-5.png)


## Exercise 2.2 Create the agent

After completing these steps you will have...

1.	Enter this code.
```abap
DATA(lt_params) = request->get_form_fields(  ).
READ TABLE lt_params REFERENCE INTO DATA(lr_params) WITH KEY name = 'cmd'.
  IF sy-subrc = 0.
    response->set_status( i_code = 200
                     i_reason = 'Everything is fine').
    RETURN.
  ENDIF.

```

2.	Click here.
<br>![](/exercises/ex2/images/02_02_0010.png)

## Exercise 2.3 Deploy and the test the custom agent

## Summary

You've now ...

Continue to - [Exercise 3 - Excercise 3 ](../ex3/README.md)
