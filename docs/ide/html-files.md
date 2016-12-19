---
title: "HTML 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义向导, HTML 文件"
  - "自定义向导, 用户界面"
  - "文件 [C++], “自定义向导”创建的"
  - "HTML 页面, 自定义向导的用户界面"
  - "向导用户界面"
  - "向导 [C++], 自定义向导的用户界面"
ms.assetid: 3b6ed080-6560-418b-b908-d84d71bdf145
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HTML 文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

向导可以包含用户界面，该界面是 HTML 界面。  除了 Default.htm 之外，向导还可以包含任意数目的 .htm 文件，可以在 [“自定义向导”](../ide/custom-wizard.md) 的**“页数”**框中指定此数目。  每个 .htm 文件均表示向导的一个 HTML 页，可以使用 `Next` 和“后退”按钮、选项卡或在向导设计时指定的任何其他格式来访问此 HTML 页。  
  
 HTML 包含：  
  
-   SYMBOL 标记，标识用户定义选项的默认值。  当用户单击“完成”时，符号写入符号表，如：  
  
```  
<SYMBOL NAME='HEADER_FILE' VALUE='MyHeader.h' TYPE=text></SYMBOL>  
```  
  
 在向导的用户界面 \(UI\) 中，符号表中标识为“HEADER\_FILE”的文本框包含默认文本“MyHeader.h”。  可以在向导 UI 中更改该值，当单击“完成”时，结果值写入项目的符号表，如：  
  
```  
<SYMBOL NAME='CHECKBOX1' TYPE=checkbox VALUE=false></SYMBOL>  
```  
  
 在向导 UI 中，默认情况下清除符号表中标识为“CHECKBOX1”的复选框。  可以在 HTML UI 中选择此框，当单击“完成”时，结果值写入符号表。  
  
 每个 .htm 文件均将用户选择记录到符号表中。  
  
-   包含 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)（它包含常用的和有帮助的 JScript 函数）和 Default.js。  
  
-   对要显示在 HTML 中的项目图像的引用。  
  
-   自定义向导的用户界面外观的 HTML 文本和格式设置。  
  
-   访问 Visual C\+\+ 向导对象模型以从向导内提供自定义行为的 JScript 函数。  这些函数位于标头为 \<SCRIPT LANGUAGE\='JSCRIPT'\> 的 HTML 页节，如下例所示。  
  
    > [!NOTE]
    >  若要从 HTML 访问向导和环境对象模型，请在对象模型项前预置“window.external”。  
  
    ```  
    function InitDocument(document)  
    {  
       setDirection();  
  
       if (window.external.FindSymbol('DOCUMENT_FIRST_LOAD'))  
       {  
          // This function sets the default symbols based   
          // on the values specified in the SYMBOL tags above  
          //  
          window.external.SetDefaults(document);  
       }  
  
       // Load the document and initialize the controls   
       // with the appropriate symbol values  
       //  
       window.external.Load(document);  
    }  
    ```  
  
 以下是一个控制台应用程序向导示例：  
  
```  
<SYMBOL NAME='WIZARD_DIALOG_TITLE' TYPE=text VALUE='Console Application Wizard'></SYMBOL>  
  
<SYMBOL NAME='EMPTY_PROJECT' TYPE=checkbox VALUE=false></SYMBOL>  
<SYMBOL NAME='SUPPORT_ATL' TYPE=checkbox VALUE=false></SYMBOL>  
<SYMBOL NAME='SUPPORT_MFC' TYPE=checkbox VALUE=false></SYMBOL>  
```  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)