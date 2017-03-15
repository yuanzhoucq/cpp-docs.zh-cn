---
title: "“MFC 添加类向导”的文档模板字符串 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.simple.doctemp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC 添加类向导，文档控制字符串"
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# “MFC 添加类向导”的文档模板字符串
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

该向导页仅对符合以下条件的类可用：  
  
-   MFC 项目支持文档\/视图结构。  
  
-   新类的基类为 [CFormView](../../mfc/reference/cformview-class.md)。  
  
-   复选框“生成 DocTemplate 资源”在 [MFC 类向导](../../mfc/reference/mfc-add-class-wizard.md)的**“名称”**区域被选中。  
  
 该向导提供以下值的默认设置，以帮助窗体视图的设计、管理和本地化。  因为大多数文档模板字符串都可见并被窗体的用户使用，它们被本地化为创建项目时在“MFC 应用程序向导”的[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页中指示的“资源语言”。  
  
> [!NOTE]
>  该向导不为从 `CFormView` 派生的类提供自动打印支持。  
  
 有关更多信息，请参见[文档模板和文档\/视图的创建过程](../../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 非本地化字符串  
 应用于创建用户文档的应用程序。  如果文档类型有文件扩展名和文件类型 ID，则用户可以更容易地打开和保存文档。  这些项未本地化，因为它们供系统使用而非用户。  
  
 **文件扩展名**  
 设置与此窗体应用程序的文档类型关联的文件扩展名。  文件扩展名默认情况下基于类名。  例如，如果新的 MFC 类名为 **CWidget**，默认情况下，文件扩展名为 .wid。  文件扩展名在文件筛选器以及“打开”和“另存为”对话框中使用。  
  
 如果更改文件扩展名，更改反映在“筛选器名”框中。  
  
> [!NOTE]
>  如果更改默认文件扩展名，不要包括句点。  
  
 **文件类型 ID**  
 在系统注册表中设置文档类型的标签。  
  
## 本地化字符串  
 产生与应用程序的用户读取和使用的窗体和文档关联的字符串，因此字符串被本地化。  
  
 **文档类型名称**  
 标识应用程序的文档可归入的文档类型。  默认情况下，它基于类名。  例如，如果新的 MFC 类名为 **CWidget**，默认情况下，文档类型名为 Widget。  更改默认值不会更改此对话框中的任何其他选项。  
  
 **筛选器名**  
 设置用户可以用来指示查找指定文件类型的文件的名称。  从标准 Windows“打开”和“另存为”对话框的“文件类型”和**“另存类型”**选项中可以访问此选项。  默认情况下，此名称基于项目名称加上 Files，后跟“文件扩展名”中指示的扩展名。  例如，如果项目名称为 Widget，文件扩展名为 .wid，则默认 **Filter name** 为 Widget Files \(\*.wid\)。  
  
 **文件的新简称**  
 如果项目有多个文档模板，设置显示在标准 Windows“新建”\(`New`\) 对话框中的名称。  如果应用程序是[自动化服务器](../../mfc/automation-servers.md)，则此名称用作自动化对象的简称。  默认情况下，此名称基于类名。  
  
 **文件类型全名**  
 在系统注册表中设置文件类型名称。  如果应用程序是自动化服务器，则此名称用作自动化对象的全称。  默认情况下，此名称基于类名加上 .Document。  例如，如果类名为 **CWidget**，则 **File type long name** 为 Widget Document。  
  
 **文档类**  
 指示项目的文档类。  默认情况下，该类为主应用程序的文档类，列在“MFC 应用程序向导”的[查看生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页中。  如果在项目中添加了其他的文档类，可以从列表中选择另一个文档类。  
  
## 请参阅  
 [MFC 添加类向导](../../mfc/reference/mfc-add-class-wizard.md)   
 [MFC 类](../../mfc/reference/adding-an-mfc-class.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)