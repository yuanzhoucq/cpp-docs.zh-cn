---
title: 表达式中的数组 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b792bc02cf620cbd961830a99e35ae0c61898fed
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39409342"
---
# <a name="arrays-in-expressions"></a>表达式中的数组
当数组类型的标识符出现在表达式中以外`sizeof`，地址的 (**&**)，或初始化的引用，它将转换为指向第一个数组元素的指针。 例如：  
  
```cpp 
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 指针 `psz` 指向数组 `szError1` 的第一个元素。 请注意，与指针不同，数组不是可修改的左值。 因此，以下赋值是非法的：  
  
```cpp 
szError1 = psz;  
```  
  
## <a name="see-also"></a>请参阅  
 [数组](../cpp/arrays-cpp.md)