---
sidebar_position: 6
slug: /LabDeveloper/AuthoringLabGuides
---

# Authoring Lab Guides

## Overview

You can now directly embed Git markdown documents into the CloudLabs platform using its easy-to-use self service capabilities. In this documentation we will explore some of the best practices while making lab guide documentation using Git markdown and how to structure it most effectively. 


## About Git Markdown

Markdown is a way to style text on the web. You control the display of the document; format words as **bold** or *italics*, add images and screenshots, and how to create lists. These are just a few of the things we can do with Markdown. Mostly, Markdown is just regular text with a few non-alphabetic characters thrown in, like # or *.
Please go through this documentation if you need to get familiar with Git Markdown.

## Mastering Markdown · GitHub Guides

### Structuring: Folder/Files
 
First thing you would want to do before you start writing lab guides is to structure the content. Meaning, you need to segregate the content in a structure that maintains a logical flow and is also easy to navigate. It also helps to keep things organized for later editing.

> **Let us take a scenario to understand this**. You are trying to create two modules : **Module 1- Data** and **Module 2- AI**. Now let's say each of them has **2** exercises, you can structure it as follows in the repository 

 
![](/img/LabDeveloper/LabGuide/file.png)

**Folder** - As you can see in the above folder structure, the Instructions for each Module are included within a folder for better classification.

**File** - And it is always a best practice to include each exercises as different files.Benefit of doing this in CloudLabs is that each exercise gets shown as an individual page in platform, providing an easy navigation panel to learners. 

**Images** - In this folder, which is under the Instructions folder, you can store all the screenshot images. The naming convention for the images can be followed as given here if you have modules.

> For example, m2-ex2-st-20-vmcreate.png - this name will indicate that this image is from Module 2 -> Exercise 2 - Step -> 20 -> Action being performed.

### Structuring: Lab Guides

Right after you are done structuring the folder and files, you are ready to start with the actual documentation part. However, before you begin there are some best practices that would help you maintain effeciency. 

1. It is recommended to have the **first page** as an **overview** about the technology that they are going to learn as part of the lab.

Refer this document: https://github.com/CloudLabsAI-Azure/AVW-Arc-enabled-dataservices/blob/aiw-arc/Instructions/README.md

Here the documentation is on Azure Arc and as you can see there is an introduction on Azure Arc followed by what the workshop is going to cover. Finally we talk about in context of the lab.

> **A GOOD overview helps the labs to stand out and set the context right. It is the first file an attendee will see when they start with the lab, so it should be fairly written and well-structured so as the other files**

2. Second page is typically the information about the pre-provisioned environment in the labs and is followed by more instructions on how to access it. Then an overview about the pre-provisioned resources and where they will need it.

Here is a sample you can refer: https://github.com/CloudLabsAI-Azure/AVW-Arc-enabled-dataservices/blob/aiw-arc/Instructions/HOL%201/01-Getting-Started-with-Azure-Arc.md
 
3. In the subsequent pages, you can provide the actual exercises.

The purpose of any instructional documentation is how effective it is for the readers. It is very important to write instructional guides that is easy to understand and follow, even if the reader has no prior knowledge on the subject.



 
## Best Practices:

Here are some of the best practices that you should keep in mind while developing the content. We will be presenting some example with the **Incorrect Method** followed by the **Correct Method** for better understanding.
 
### Writing Tips

1. There shouldn't be multiple actions defined in a single step. Always make it a habit to split the steps to ensure that each step is easy to understand.

Example:

**Incorrect Method**:
 
![](/img/LabDeveloper/LabGuide/image02.png)

**Correct Method**
 
![](/img/LabDeveloper/LabGuide/image03.png)



2. There should not be any undefined headings after which the numbering restarts
 
Example:
 
**Incorrect Method:**    

Task 1:
        Step 1
        Step 2

Heading

       Step 1
       Step 2
 
**Correct Method**:

Task 1:
        Step 1
        Step 2

Task 1.1: Heading

       Step 1
       Step 2
 

 
3. There should be a good overview section at the beginning and summary of each exercise

4. The wait times after a step should be called out clearly. There should not be any ambiguous statements.

Example:

**Incorrect:** This step will take some time to get completed.
**Correct:** This step will take around 5 minutes to complete. In the meantime, you can go through this document.

5. Entire document should be verified from Grammarly to ensure there are no unnoticed grammar errors or incorrect spelling.

6. If you are providing an information, do not add it as a step, instead keep it as a note or info


### Additional Tips

1. If screenshots cannot clearly explain the actions to be performed, it is recommended to use a GIFs.

2. Instead of using UniqueID, we should use inject keys for the deployment wherever possible.

3. The values that attendees have to copy from the lab guide should be given in a key-value format and the key should be exact name as in the portal/the UI they see.
 
4. Additional information or links can be added for attendees' reference.
 
 
5. If RDP over HTTPS with Jump VM is provided, the lab guide should be written with RDP over HTTPs experience. If the lab can be performed from the browser, do not perform the lab from within your local browser and prepare the documentation as the experience might vary in the two scenarios.
 
 
## Samples

Here are few samples to help you understand better


Example Guide : https://github.com/CloudLabsAI-Azure/AVW-Arc-enabled-dataservices/blob/aiw-arc/Instructions/02.md 

Format Guide: https://github.com/PraveenAnil/sample/blob/main/Instructions/01.md

More Samples: https://github.com/CloudLabsAI-Azure 


## Injecting Personalized Information into Guide 

Using **inject key** property, you can insert dynamic information in Lab Guide itself, such as Azure Username and password.

Below are the natively supported inject keys:
```
<inject key="AzureAdUserEmail"></inject>
<inject key="AzureAdUserPassword"></inject>
<inject key="DeploymentID" />
```
```
You can close inject key code snippet in two ways:
i) <inject key="AzureAdUserEmail"></inject> 
ii) <inject key="AzureAdUserEmail"/>

Inject key also supports additional parameters:
i) color: Using color parameter, you can add color to injected value.
ex: 
   <inject key="AzureAdUserEmail" style="color:red" />

Other supported colors are indianRed, blue, lightCoral, green.

ii) enableCopy: Setting the enableCopy parameter to "true" will provide you a copy icon next to the injected text from which you can copy the value. In contrast, setting it to "false" will disable the copy icon.
ex:
   <inject key="AzureAdUserEmail" enableCopy="true" /> 
```


### Sample Guide 
```
1. On Sign in to Microsoft Azure blade, you will see a login screen, in that enter the following email/username. 
   Email/Username: <inject key="AzureAdUserEmail" enableCopy="true" style="color:blue"></inject>

2. Now enter the following password and click on Sign in.
   Password: <inject key="AzureAdUserPassword" enableCopy="true" style="color:blue"></inject>
```

![](/img/LabDeveloper/LabGuide/injected-labguide.png)

### Inject environment outputs:

Additionally, you can inject the values from ARM template outputs such as azure resource names, VM username/password, etc. to the lab guide.

**>Example**: 

Below is the Outputs section of ARM template: 
```
"outputs": {
    "VM Name": {
      "type": "string",
      "value": "[variables('VmName')]"
    },
    "VM Admin Username": {
      "type": "string",
      "value": "[parameters('VmUsername')]"
    },
    "VM Admin Password": {
      "type": "string",
      "value": "[parameters('VMPassword')]"
    },
    "VM DNS Name": {
      "type": "string",
      "value": "[reference(resourceId('Microsoft.Network/publicIPAddresses',variables('publicIpAddressName'))).dnsSettings.fqdn]"
    }
  }
```

### Sample Guide 
```
1. Once logged into Microsoft Azure portal, search and select Virtual Machine resource. In the VM list, select the VM <inject key="VM Name"/>.

2. Download the RDP file and open it so that you can connect to the VM.

3. In the Remote Desktop Connection, provide the VM DNS name <inject key="VM DNS Name" enableCopy="true"/> and click Connect.

4. In the following "Enter Your Credential" screen, provide VM username <inject key="VM Admin Username" enableCopy="true" style="color:blue" /> and password <inject key="VM Admin Password" enableCopy="true" style="color:blue" /> and select OK followed by Yes in the next page, which will then log you into the VM.

```
After rendering of the above Sample Guide, the users will see the actual values from the ARM template outputs.

## Github Master Document:

This is a JSON-formatted document that is used to arrange the lab guide to a coherent way. We should first prepare the document in JSON format, with section-by-section raw GitHub URLs, as it only supports GitHub raw URLs.

We have a feature named _**Enable VM Access Over Http**_ which allows you to connect to the VM via browser. When your lab is ready, the environment you receive includes a VM on the left side of the browser and the Lab Guide on the right as shown below:

  ![](/img/LabDeveloper/image19.png)

For a successful setup of both the VM and the Lab Guide, we have some configurations to be done. In the next sections, we will learn more about _Enable VM Access Over Http_ feature(involves the setup of VM) and for now, we will focus on the Master document that involves Lab guide setup.

A master document contains the following information:

1. **Name:** Here you have to provide a name for your Lab.
2. **Language:** English
3. **Files:** In this section we provide the Raw File Path and Order of the file lab guide that should be available in GitHub.
    * **Raw File Path:** This is the raw URL of the pages in your lab guide.
    * **Order:** Defines the sequence of the pages in your lab guide such as what all should come first and so on.

Example: You have a lab guide in GitHub which includes - Introduction to the Lab, three Exercises to be performed, and a Summary.
Rather than preparing one lengthy document, we'll break it down into individual pages on GitHub and fetch the Raw URL for each page. 
We will add the Raw URL of the pages in _**Raw File Path**_, with respect to the order value. 

Therefore, the lab guide's final output will follow the flow shown below:
  * Introduction of the Lab
  * Exercise 1
  * Exercise 2
  * Exercise 3
  * Summary

For your reference, here is a Master document sample - **<https://cloudlabsai.blob.core.windows.net/master-doc/master-doc.json>**

  ![](/img/LabDeveloper/image18.png)
