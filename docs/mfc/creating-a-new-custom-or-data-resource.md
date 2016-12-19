---
title: "Creating a New Custom or Data Resource | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.binary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "custom resources [C++]"
  - "data resources [C++]"
  - "resources [Visual Studio], creating"
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Creating a New Custom or Data Resource
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以通过以下方式来创建新的自定义资源或数据资源：在使用标准资源脚本 \(.rc\) 文件语法的独立文件中放置资源，然后在解决方案资源管理器中右键单击项目并单击快捷菜单上的**资源包含**来包含文件。  
  
### 创建新的自定义资源或数据资源  
  
1.  [创建 .rc 文件](../windows/how-to-create-a-resource-script-file.md)（其中包含自定义资源或数据资源）。  
  
     可以在 .rc 文件中键入自定义数据，格式为以 null 结尾的带引号的字符串，或十进制、十六进制或八进制格式的整数。  
  
2.  在“解决方案资源管理器”中，右键单击项目的 .rc 文件，然后在快捷方式菜单中单击“资源包含”。  
  
3.  在“编译时指令”框中，键入 **\#include** 语句，为包含自定义资源的文件命名。 例如：  
  
    ```  
    #include mydata.rc  
    ```  
  
     请确保所键入内容的语法和拼写正确。 在“编译时指令”框中键入时，其内容会插入到资源脚本文件中。  
  
4.  单击“确定”以记录所做的更改。  
  
 创建自定义资源的另一种方法是将外部文件导入为自定义资源。 有关详细信息，请参阅[导入和导出资源](../windows/how-to-import-and-export-resources.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Binary Editor](../mfc/binary-editor.md)