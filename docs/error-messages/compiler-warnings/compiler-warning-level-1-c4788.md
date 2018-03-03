---
title: "编译器警告 (等级 1) C4788 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6f876dada851f46b7708ef1b34da4bae6f96dc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4788"></a>编译器警告（等级 1）C4788
identifier： 标识符被截断为 number 个字符  
  
 编译器限制程序函数名称中允许的最大长度。 当编译器生成 funclets EH/SEH 代码时，程序集的 funclet 名称形成通过预先计算函数名称加上一些文本，例如"__catch"，"\__unwind"，或另一个字符串。  
  
 生成的 funclet 名称可以是太长，并且编译器会将其截断，并生成 C4788。  
  
 若要解决此警告，请缩短原始函数名称。 如果该函数的 c + + 模板函数或方法，将 typedef 用于名称的一部分。 例如:  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 可以替换为：  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 此警告仅在 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译器中发生。