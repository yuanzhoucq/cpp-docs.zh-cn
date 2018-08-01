---
title: 标点符号 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1602857896745daae6e7af969add76ca2c1e1ead
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406749"
---
# <a name="punctuators-c"></a>标点符号 （C++）
在 C++ 中，标点符号相对于编译器来说具有语法意义和语义含义，但是它们本身不会指定一个产生数值的操作。 某些标点符号（单独或组合）也可以是 C++ 运算符或对预处理器很重要。  

 以下任意字符都被视为标点符号：  

```  
! % ^ & * ( ) - + = { } | ~  
[ ] \ ; ' : " < > ? , . / #  
```  

 标点符号 **[ ]**，**（ )**，和 **{ }** 必须成对出现在[翻译阶段](../preprocessor/phases-of-translation.md)4。   

## <a name="see-also"></a>请参阅  
 [词法约定](../cpp/lexical-conventions.md)