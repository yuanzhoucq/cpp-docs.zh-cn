---
title: "Templates.inf 文件 | Microsoft Docs"
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
  - "自定义向导, 模板文件"
ms.assetid: 93d60d27-2402-4dc8-a829-e97417ccea49
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Templates.inf 文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Templates.inf 是一个文本文件，包含为项目呈现的模板列表。  
  
 Templates.inf 本身是一个[模板文件](../ide/template-files.md)，因此可以使用指令指示包含在项目中的文件，具体取决于用户的选择。  有关可在此文件中使用的指令列表，请参见[模板指令](../ide/template-directives.md)。  
  
## 示例  
  
```  
Template1.txt  
Template2.txt  
  [!if TYPE_A]  
TemplateOptionA.h  
TemplateOptionA.cpp  
  [!else]  
TemplateOptionB.h  
TemplateOptionB.cpp  
  [!endif]  
```  
  
 **CreateCustomInfFile** 将 Templates.inf 呈现到一个临时文本文件中，而该文件必须在处理完文件后删除。  
  
## 示例  
  
```  
var InfFile = CreateCustomInfFile();  
AddFilesToProject(selProj, strProjectName, InfFile);  
InfFile.Delete();  
```  
  
 有关更多信息，请参见 [JScript 文件](../ide/jscript-file.md)。  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)