---
title: "表达式中的数组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ec97fba837ffae0a03ff8d4fc3d85c4011aa59c6
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

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
