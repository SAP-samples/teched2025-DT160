# Getting Started

In this exercise, you will make yourself familiar the system landscape setup required for this Hands-on Workshop

### Landscape / System Access

[**SAP Build Lobby - Joule Studio**](https://dt160-map4x9xc.eu10.build.cloud.sap/lobby)


### SAP Cloud ERP System
[SAP Cloud ERP System](https://my426786.s4hana.cloud.sap/ui)

### Joule Studio in SAP Build

Refer
[Extend Joule with Joule Studio - Reference Architecture](https://architecture.learning.sap.com/docs/ref-arch/06ff6062dc)
[Identity Management for Joule  - Reference Architecture](https://architecture.learning.sap.com/docs/ref-arch/20c6b29b1e/4)


## Level 2 Heading

After completing these module you are familar with the provided system and landscape setup.
1.	Click here.
<br>![](/exercises/ex0/images/00_00_0010.png)

2.	Insert this code.
``` abap
 DATA(params) = request->get_form_fields(  ).
 READ TABLE params REFERENCE INTO DATA(param) WITH KEY name = 'cmd'.
  IF sy-subrc <> 0.
    response->set_status( i_code = 400
                     i_reason = 'Bad request').
    RETURN.
  ENDIF.
```

## Summary

Now that you have ... 
Continue to - [Exercise 1 - Exercise 1 Description](../ex1/README.md)
