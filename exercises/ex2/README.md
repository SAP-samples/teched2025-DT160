# Exercise 2 - Exercise 2 Description

In this exercise, we will adjust our skills that we created in exercise 1 in order to build a custom Sales Order Completeness Agent. Our goal is to retrieve the sales order information and apply specific checks on some of the fields. On top of that, the agent will gather information about the country of our business partner and then apply a web search to look for the latest news surrounding this country. The summary of the completeness check from our agent will be saved into the custom field 'AI Remark' of the sales order.

## Exercise 2.1 Modify the Skills

After completing these steps you will have created...

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
