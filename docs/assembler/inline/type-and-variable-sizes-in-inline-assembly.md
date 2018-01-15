---
title: "类型和内联程序集中的变量大小 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- length
- Type
dev_langs: C++
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee9edf9430c0333317a767e8f8c114453a6d80f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>内联程序集中的类型和变量大小
**Microsoft 专用**  
  
 **长度**，**大小**，和**类型**运算符在内联程序集中具有有限的含义。 无法将这些运算符与 `DUP` 运算符一起使用（因为您无法利用 MASM 指令或运算符定义数据）。 但是，您可以使用它们来查找 C 或 C++ 变量或类型的大小：  
  
-   **长度**运算符可返回数组中的元素数。 它为非数组变量返回值 1。  
  
-   **大小**运算符可返回 C 或 c + + 变量的大小。 变量的大小是数组的乘积其**长度**和**类型**。  
  
-   **类型**运算符可返回 C 或 c + + 类型或变量的大小。 如果变量是一个数组，**类型**返回数组的单个元素的大小。  
  
 例如，如果您的程序具有一个 8 元素 `int` 数组，  
  
```  
int arr[8];  
```  
  
 则下列 C 和程序集表达式将生成 `arr` 及其元素的大小。  
  
|__asm|C|大小|  
|-------------|-------|----------|  
|**长度**arr|`sizeof`(arr)/`sizeof`(arr[0])|8|  
|**大小**arr|`sizeof`(arr)|32|  
|**类型**arr|`sizeof`(arr[0])|4|  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [在 __asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)