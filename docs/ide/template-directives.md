---
title: "模板指令 | Microsoft Docs"
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
  - "[!else] 模板指令"
  - "[!endif] 模板指令"
  - "[!endloop] 模板指令"
  - "[!if] 模板指令"
  - "[!loop] 模板指令"
  - "[!output] 模板指令"
  - "自定义向导, 模板指令"
  - "指令, 模板指令"
  - "else 指令 ([!else])"
  - "endif 指令 ([!endif])"
  - "endloop 指令 ([!endloop])"
  - "if 指令 ([!if])"
  - "loop 指令 ([!loop])"
  - "output 指令 ([!output])"
  - "模板指令"
ms.assetid: b6204153-813a-423c-b044-e39c352cc5af
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 模板指令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以在向导 [模板文件](../ide/template-files.md) 和 [Templates.inf 文件](../ide/templates-inf-file.md)中使用以下模板指令自定义向导。  
  
|指令|说明|  
|--------|--------|  
|\[\!  if \]|开始控制结构以检查条件。|  
|\[\!  else \]|\[ \!if \]   if \] 控制结构的一部分。  检查另一个条件。|  
|\[\!  endif \]|结束 \[\!  if \] 控制结构的一部分。|  
|\[\!  output \]|可通过下列两种方式使用：<br /><br /> -   \[\!  output "string" \] 提供字符串。<br />-   \[\!  output SYMBOL\_STRING \] 提供符号 SYMBOL\_STRING 的值。|  
|\[\!  loop \]|可通过下列两种方式使用：<br /><br /> -   \[\!  loop \= 5 \]<br />-   \[\!  loop \= *NUM\_OF\_PAGES* \]，其中 *NUM\_OF\_PAGES* 是具有数值的符号。|  
|\[\!  endloop \]|结束循环结构。|  
  
 紧跟一个惊叹号 \(\!\) 的左括号 \(\[\) 表示模板指令开始。  右括号表示模板指令结束。  这是所需的语法：  
  
```  
[!directive params]  
```  
  
 只有在 *directive* 和 *params* 之间才需要一个空格或非标识符字符。  
  
## 示例  
  
```  
[!if SAMPLE_RADIO_OPTION1]  
You have checked the option 'Sample radio button option 1'  
[!else]  
You have checked the option 'Sample radio button option 2'  
[!endif]  
```  
  
 下列运算符可以在模板文件中与以上指令一起使用。  
  
```  
+  
-     
=  
!=     
==     
||     
&&    
!  
```  
  
## 示例  
  
```  
[!if SYMBOL_STRING != 0]  
```  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)