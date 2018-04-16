---
title: "复合语句 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9422e3229aa5e800859f50e1ca058e32a4120074
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compound-statement-c"></a>复合语句 (C)
复合语句（也称为“块”）通常显示为另一个语句（例如 if 语句）的主体。 [声明和类型](../c-language/declarations-and-types.md)描述可在复合语句的头部出现的声明的格式和含义。  
  
## <a name="syntax"></a>语法  
 compound-statement：  
 {  declaration-list optstatement-listopt}  
  
 declaration-list：  
 declaration  
  
 declaration-list declaration  
  
 statement-list：  
 statement  
  
 statement-list statement  
  
 如果有声明，则它们必须在任何语句之前出现。 在复合语句开头声明的每个标识符的范围从其声明点扩展到块的末尾。 它在整个块中都可见，除非内部块中存在对同一标识符的声明。  
  
 复合语句中的标识符将假定 auto，除非另使用 register、static 或 `extern`（只能是 `extern` 的函数除外）显式声明。 您可停止在函数声明中使用 `extern` 说明符，但函数仍然是 `extern`。  
  
 如果在具有存储类 `extern` 的复合语句中声明了变量或函数，则将不会分配存储并且不会执行初始化。 声明引用在其他位置定义的外部变量或函数。  
  
 每当进入复合语句时，将重新分配并初始化（如有必要）在块中使用 auto 或 register 声明的变量。 在退出复合语句后将不再定义这些变量。 如果在块内声明的变量具有 static 特性，则将在程序开始执行时初始化变量并在整个程序中保留变量值。 有关 static 的信息，请参阅[存储类](../c-language/c-storage-classes.md)。  
  
 此示例演示了一个复合语句：  
  
```  
if ( i > 0 )   
{  
    line[i] = x;  
    x++;  
    i--;  
}  
```  
  
 在此示例中，如果 `i` 大于 0，则复合语句内的所有语句将按顺序执行。  
  
## <a name="see-also"></a>请参阅  
 [语句](../c-language/statements-c.md)