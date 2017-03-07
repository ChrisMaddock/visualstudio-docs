---
title: "How to: Retrieve the SharePoint Project Service | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project service"
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Retrieve the SharePoint Project Service
  You can access the SharePoint project service in the following types of solutions:  
  
-   An extension of the SharePoint project system, such as a project extension, project item extension, or project item type definition. For more information about these types of extensions, see [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   An extension of the **SharePoint Connections** node in **Server Explorer**. For more information about these types of extensions, see [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Another type of Visual Studio extension, such as an add-in or a VSPackage.  
  
## Retrieving the Service in Project System Extensions  
 In any extension of the SharePoint project system, you can access the project service by using the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> property of an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> object.  
  
 You can also retrieve the project service by using the following procedures.  
  
#### To retrieve the service in a project extension  
  
1.  In your implementation of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface, locate the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> method.  
  
2.  Use the *projectService* parameter to access the service.  
  
     The following code example demonstrates how to use the project service to write a message to the **Output** window and **Error List** window in a simple project extension.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-cs[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     For more information about creating project extensions, see [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### To retrieve the service in a project item extension  
  
1.  In your implementation of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface, locate the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> method.  
  
2.  Use the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> property of the *projectItemType* parameter to retrieve the service.  
  
     The following code example demonstrates how to use the project service to write a message to the **Output** window and **Error List** window in a simple extension of the **List Definition** project item.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-cs[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     For more information about creating project item extensions, see [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### To retrieve the service in a project item type definition  
  
1.  In your implementation of the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface, locate the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> method.  
  
2.  Use the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> property of the *typeDefinition* parameter to retrieve the service.  
  
     The following code example demonstrates how to use the project service to write a message to the **Output** window and **Error List** window in a simple project item type definition.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-cs[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     For more information about defining project item types, see [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Retrieving the Service in Server Explorer Extensions  
 In an extension of the **SharePoint Connections** node in **Server Explorer**, you can access the project service by using the <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> property of an <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> object.  
  
#### To retrieve the service in a Server Explorer extension  
  
1.  Get an <xref:System.IServiceProvider> object from the <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> property of an <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> object in your extension.  
  
2.  Use the <xref:System.IServiceProvider.GetService%2A> method to request an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> object.  
  
     The following code example demonstrates how to use the project service to write a message to the **Output** window and **Error List** window from a shortcut menu that the extension adds to list nodes in **Server Explorer**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-cs[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     For more information about extending the **SharePoint Connections** node in **Server Explorer**, see [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Retrieving the Service in Other Visual Studio Extensions  
 You can retrieve the project service in a VSPackage, or in any Visual Studio extension that has access to a <xref:EnvDTE80.DTE2> object in the automation object model, such as an add-in or a project template wizard that implements the <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
 In a VSPackage, you can request an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> object by using one of the following methods:  
  
-   The <xref:System.IServiceProvider.GetService%2A> method of a managed VSPackage that derives from the <xref:Microsoft.VisualStudio.Shell.Package> class. For more information, see [How to: Get a Service](../Topic/How%20to:%20Get%20a%20Service.md).  
  
-   The static <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> method. For more information, see [How to: Use GetGlobalService](../Topic/How%20to:%20Use%20GetGlobalService.md).  
  
 In a Visual Studio extension that has access to a <xref:EnvDTE80.DTE2> object, you can request an <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> object by using the <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> method of a <xref:Microsoft.VisualStudio.Shell.ServiceProvider> object. For more information, see [How to: Get a Service from the DTE Object](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md).  
  
### Example  
 The following code example demonstrates how to retrieve the project service in a Visual Studio add-in. To use this code, run it from the `Connect` class in an add-in project. The `_applicationObject` object is automatically generated in add-in projects; this object is an instance of the <xref:EnvDTE80.DTE2> interface.  
  
 [!code-cs[SPExtensibility.ProjectService.FromDTE#1](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#1)]  
  
 This example requires:  
  
-   A Visual Studio add-in project. For more information, see [How to: Create an Add-In](../Topic/How%20to:%20Create%20an%20Add-In.md).  
  
-   References to the Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell and Microsoft.VisualStudio.SharePoint assemblies.  
  
## See Also  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Create an Add-In](../Topic/How%20to:%20Create%20an%20Add-In.md)   
 [How to: Get a Service](../Topic/How%20to:%20Get%20a%20Service.md)   
 [How to: Get a Service from the DTE Object](../Topic/How%20to:%20Get%20a%20Service%20from%20the%20DTE%20Object.md)   
 [How to: Use Wizards with Project Templates](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)  
  
  