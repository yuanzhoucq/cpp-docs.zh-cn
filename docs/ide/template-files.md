---
title: "模板文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义向导, 模板文件"
  - "文件 [C++], “自定义向导”创建的"
  - "模板 [C++], 对于向导"
ms.assetid: 48fae3d8-3a53-4f62-8010-144c5ffe334e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 模板文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

组成向导的模板是文本文件的集合，这些文本文件包含某些[简单指令](../ide/template-directives.md)，并根据用户输入分析、呈现和添加到初始项目中。  获取用于分析模板的适当信息的方法是直接访问向导控件的符号表。  
  
 下面的示例是一个很简单的向导模板文件，它询问用户是选择 A 还是选择 B。  
  
## 示例  
  
```  
This file has been created by My Custom wizard.  
You selected:  
[!if TYPE_A]  
Type A  
[!else]  
Type B  
[!endif]  
The name of this project is [!output PROJECT_NAME].root.cpp:  
```  
  
 如果用户选择 Type B，则上面的模板将呈现为：  
  
  **已使用“My Custom”向导创建了此文件。  选定的内容：**  
**键入 B**  
**该项目的名称为 MyApp8。**    
## Output  
  
```  
This file has been created by My Custom wizard.  
You selected:  
Type B  
The name of this project is MyApp8.  
```  
  
 **注意** 上面的语法是 Visual C\+\+ .NET 中的新内容。  Visual C\+\+ .NET 不支持 Visual C\+\+ 早期版本中的语法。  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [Templates.inf 文件](../ide/templates-inf-file.md)