---
title: "内联程序集中的类型和变量大小 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "length"
  - "Type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "内联程序集, 运算符"
  - "LENGTH 运算符"
  - "大小"
  - "SIZE 运算符"
  - "大小, 在内联程序集中获取"
  - "TYPE 运算符"
  - "变量, length"
  - "变量, 大小"
  - "变量, 类型"
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 内联程序集中的类型和变量大小
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定**  
  
 **长度**， **大小**，和 **类型**运算符在内联程序集具有有限的意义。  它们不能用于在所有`DUP`运算符 （因为您无法定义数据使用 MASM 指令或运算符）。  但是，可用于查找 C 或 c \+ \+ 变量或类型的大小：  
  
-   **长度**运算符可返回数组中的元素的数目。  它将返回非数组变量的值为 1。  
  
-   **大小**运算符可返回一个 C 或 c \+ \+ 变量的大小。  变量的大小是积其**长度** 和 **类型**。  
  
-   **类型**运算符可返回 C 或 c \+ \+ 类型或变量的大小。  如果该变量是一个数组中， **类型**返回单个元素的数组的大小。  
  
 例如，如果程序具有 8 元素`int`数组，  
  
```  
int arr[8];  
```  
  
 下面的 C 和程序集表达式产生的大小`arr`及其元素。  
  
|\_\_asm|C|大小|  
|-------------|-------|--------|  
|**长度** arr|`sizeof`\(arr\)\/`sizeof`\(arr\[0\]\)|8|  
|**大小** arr|`sizeof`\(\) arr|32|  
|**TYPE** arr|`sizeof`\(arr\[0\]\)|4|  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)