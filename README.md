> [!IMPORTANT]
> **Welcome to the Agent Builder Lab Preview!**
>
> You are working with a **pre-release version** of the Agent Builder in Joule Studio. This gives you an early look at our upcoming capabilities. Please keep the following in mind:
>
> *   **Features Are Subject to Change:** The user interface (UI), terminology, and functionalities you see in this lab may differ from the final, generally available (GA) product.
> *   **For Educational Use Only:** This environment is designed for learning and experimentation, not for production use.
> *   **Potential Instability:** As a preview version, you may encounter occasional instability or minor bugs. The exercises are designed to work with the current state of the platform. If you get stuck, please notify a session instructor.

# DT160 - Extend Joule with custom skills and custom agents for SAP Cloud ERP

## Description

Get maximum value from the Joule Copilot in SAP Cloud ERP by extending it with custom-built skills and intelligent agents that can plan, act, and execute tasks. Explore tools and techniques to make Joule smarter and faster while enhancing user productivity or automating complex workflows. Furthermore, get in an holistic understanding of the general architecture of unified Joule approach and extensibility scenarios.

[Session in **SAP TechEd** session catalog](https://www.sap.com/events/teched/berlin/flow/sap/te25/catalog-inperson/page/catalog/session/1749134506762001tjmW)

## Overview

This hands-on session you are through building AI-powered conversational skills as well as AI agents using Joule Studio. You'll learn how to create, configure, and deploy intelligent skills and agents that extend existing business processes, interact with backend systems and provide value to your users.

## Requirements

## Requirements & Prerequisites - already in place

All required backend systems and configurations have been pre-provisioned for this session. This includes:

1.  **Joule Studio in SAP Build**:
    - Agent Builder is enabled and accessible.

2.  **Actions & Destinations**:
    - SAP Build Action projects (`Sales Order (A2X) - v4`) are pre-built to access the SAP Cloud ERP System.
    - BTP Destinations (`S4_SalesOrder_V4` & `Perplexity_API`) are available in SAP Build.

## Exercises

- [Getting Started with Joule and Joule Studio in SAP Build](exercises/ex0/)
    - [Exercise 0.1 - Logon and try out Joule](exercises/ex0/README.md#exercise-01-logon-and-try-out-joule)
    - [Exercise 0.2 - Joule Studio in SAP Build](exercises/ex0/README.md#exercise-02-joule-studio-in-sap-build)
- [Exercise 1 - Create a Joule Skill to review and change custom fields in a sales order](exercises/ex1/README.md)
    - [Exercise 1.1 - Access the Build Lobby and create a new environment](exercises/ex1/README.md#exercise-11-access-the-build-lobby-and-create-a-new-environment)
    - [Exercise 1.2 - Create the custom Joule Skills](exercises/ex1/README.md#exercise-12-create-the-custom-joule-skills)
    - [Exercise 1.3 - Deploy the custom Skill and test it](exercises/ex1/README.md#exercise-13-deploy-the-custom-skill-and-test-it)
- [Exercise 2 - Create your first custom AI Agent in Joule Studio](exercises/ex2/README.md)
    - [Exercise 2.1 - Modify the Joule Skills and create a new Joule Skills](exercises/ex2/README.md#exercise-21-modify-the-joule-skills-and-create-a-new-joule-skills)
    - [Exercise 2.2 - Create the agent](exercises/ex2/README.md#exercise-22-create-the-agent)
    - [Exercise 2.3 - Deploy and test the Agent](exercises/ex2/README.md#exercise-23-deploy-and-test-the-agent)
- [Cleanup instructions](exercises/cleanup/README.md)

**IMPORTANT**

Your repo must contain the .reuse and LICENSES folder and the License section below. DO NOT REMOVE the section or folders/files. Also, remove all unused template assets(images, folders, etc) from the exercises folder. 

## Contributing
Please read the [CONTRIBUTING.md](./CONTRIBUTING.md) to understand the contribution guidelines.

## Code of Conduct
Please read the [SAP Open Source Code of Conduct](https://github.com/SAP-samples/.github/blob/main/CODE_OF_CONDUCT.md).

## How to obtain support

Support for the content in this repository is available during the actual time of the online session for which this content has been designed. Otherwise, you may request support via the [Issues](../../issues) tab.

## License
Copyright (c) 2024 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
