# Exercise 0: Getting Started

In this exercise, you will make yourself familiar with the provided systems, landscape setup and the solution architecture required for this Hands-on Workshop.

## Exercise 0.1: Logon and try out Joule

Open the SAP Cloud ERP System system by clicking the following link:
[SAP Cloud ERP System](https://my426786.s4hana.cloud.sap/ui)

Logon with your assigned group credentials. Replace `XXX` with your personal group number. 
<br>![](/exercises/ex0/images/ex0.1-1.png)


In SAP Cloud ERP open Joule by clicking the 💎-icon. 
<br>![](/exercises/ex0/images/ex0.1-2.png)


Enter a sample prompt like `show sales orders created in 2025`, Joule will provide a filtered list of sales orders. You can click one of them to navigate into the detail screen.  
<br>![](/exercises/ex0/images/ex0.1-3.png)

Then get details of a sales order by asking `show details for SO 53817` and click `Open in App`. We've already prepared *custom extension fields* in context of the object Sales Document and added them to the screen.
<br>![](/exercises/ex0/images/ex0.1-4.png)


Those are standard, built-in skills of Joule. You can find a full list [help.sap.com/joule -> capabilities](https://help.sap.com/docs/joule/capabilities-guide/what-s-new-for-joule-capabilities?version=CLOUD). 


While Joule is so far not aware of our extension fields "Best Run Status". In the next exercise we'll create a skill to retrieve the `best run status for a sales order`. 
<br>![](/exercises/ex0/images/ex0.1-5.png)



## Exercise 0.2 Joule Studio in SAP Build

Logon to SAP Build by clicking the following URL

[SAP Build Lobby - Joule Studio](https://dt160-map4x9xc.eu10.build.cloud.sap/lobby)



# System Setup

The system environment and subscription to all relevant services and applications as well as the system connectivity and integration has been set up already.
For details of the configuration and setup of Joule, Joule Studio in SAP Build as well as system connectivity, please refer to the optional [optional exercises in the appendix] //TODO//.



# Reference Architecture for Joule Studio

## Reference Architecture for extending Joule for SAP Cloud ERP

## General Reference Architecture for Joule Studio on SAP Architecture Center

[Extend Joule with Joule Studio - Reference Architecture](https://architecture.learning.sap.com/docs/ref-arch/06ff6062dc)
[Identity Management for Joule  - Reference Architecture](https://architecture.learning.sap.com/docs/ref-arch/20c6b29b1e/4)

## Summary

Now that you have made yourself familiar with the general setup and the architectural components for this Hands-on workshop, you can proceed with the first exercise.

Continue to - [Exercise 1 - Create a skill to review and change custom fields in a sales order](../ex1/README.md#exercise-1---create-a-skill-to-review-and-change-custom-fields-in-a-sales-order)
