---
title: "链接器工具警告 LNK4075 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4075"
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

忽略“option1”\(由于“option2”规范\)  
  
 第二个选项重写第一个选项。  
  
 指定互斥的链接器选项。请检查链接器选项。指定链接器选项的位置取决于生成项目的方式。  
  
-   如果在开发环境中生成，则请查看项目的链接器属性页，并了解指定两个链接器选项的位置。有关更多信息，请参见[如何：使用属性页指定项目属性](../../misc/how-to-specify-project-properties-with-property-pages.md)。  
  
-   如果在命令行中生成，则请查看此处指定的链接器选项。  
  
-   如果使用生成脚本生成，则请查阅脚本，了解指定这些链接器选项的位置。  
  
 找到指定互斥链接器选项的位置时，请移除其中的某个链接器选项。  
  
 一些特定示例：  
  
-   如果链接使用 **\/ZI**（暗示使用称为 \/EDITANDCONTINUE 的内部链接器选项）编译的模块，以及链接使用 \/OPT:REF、\/OPT:ICF 或 \/INCREMENTAL:NO（暗示不使用 \/EDITANDCONTINUE）编译的模块，则将获得 LNK4075。有关更多信息，请参见[\/Z7、\/Zi、\/ZI（调试信息格式）](../../build/reference/z7-zi-zi-debug-information-format.md)。