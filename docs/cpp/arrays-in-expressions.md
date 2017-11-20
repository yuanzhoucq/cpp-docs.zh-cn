---
title: "表达式中的数组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6f4bceac05f72c609c7aef8702c6313572ed6db5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="arrays-in-expressions"></a>表达式中的数组
当数组类型的标识符出现在表达式中除`sizeof`，地址的 (**&**)，或初始化的引用，它将转换为指向第一个数组元素的指针。 例如:   
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 指针 `psz` 指向数组 `szError1` 的第一个元素。 请注意，与指针不同，数组不是可修改的左值。 因此，以下赋值是非法的：  
  
```  
szError1 = psz;  
```  
  
## <a name="see-also"></a>另请参阅  
 [阵列](../cpp/arrays-cpp.md)