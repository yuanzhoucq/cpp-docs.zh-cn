---
title: "用公共 JScript 函数自定义 C++ 向导 | Microsoft Docs"
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
  - "向导 JScript 方法, 创建 C++ 向导"
ms.assetid: c602978f-a2c4-462f-85c3-50b5897bec46
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用公共 JScript 函数自定义 C++ 向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用[自定义向导](../ide/creating-a-custom-wizard.md)创建向导项目时，项目包含 Common.js。  如果为向导指定用户界面，则项目还包含 HTML 页，这些页指定 JScript 脚本语言并包含文件 Common.js，如下所示：  
  
```  
<SCRIPT ID="INCLUDE_COMMON" LANGUAGE ="JSCRIPT"></SCRIPT>  
```  
  
 向导还创建名为 Default.js 的唯一文件。  可以在 Default.js 中自定义您自己的 JScript 函数。  有关更多信息，请参见 [JScript 文件](../ide/jscript-file.md)。  
  
 Common.js 包含可以从每个向导的 HTML 页和 Default.js 调用的函数。  如果要在不同的向导中使用相同的函数，则可以将这些函数放在 Common.js 中。  
  
## 请参阅  
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)