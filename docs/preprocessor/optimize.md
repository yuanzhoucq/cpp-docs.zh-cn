---
title: "optimize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.optimize"
  - "optimize_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "优化杂注"
  - "杂注, 优化"
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# optimize
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定要对每个函数执行的优化。  
  
## 语法  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## 备注  
 **optimize** 杂注必须在函数的外部出现，并且在杂注显示后定义的第一个函数处生效。  **on** 和 **off** 参数将打开或关闭在 *optimization\-list* 中指定的选项。  
  
 *optimization\-list* 可以为下表中显示的零个或多个参数。  
  
### optimize 杂注的参数  
  
|参数|优化的类型|  
|--------|-----------|  
|**g**|启用全局优化。|  
|**s** 或 **t**|指定机器码的短或快速序列。|  
|**y**|在程序堆栈上生成帧指针。|  
  
 这些是与 [\/O](../build/reference/o-options-optimize-code.md) 编译器选项一起使用的相同字母。  例如，以下杂注等效于 **\/Os** 编译器选项：  
  
```  
#pragma optimize( "ts", on )  
```  
  
 将 **optimize** 杂注与空字符串 \(**""**\) 一起使用是指令的特殊形式：  
  
 在使用 **off** 参数时，它会关闭本主题前面的表中所列的优化。  
  
 在使用 **on** 参数时，它会将优化重置为使用 [\/O](../build/reference/o-options-optimize-code.md) 编译器选项指定的优化。  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)