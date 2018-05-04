---
title: bool （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2af648b2b93d2d01eaf66f5b642b6514063577d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="bool-c"></a>bool (C++)

此关键字是内置类型。 此类型的变量可以具有值[true](../cpp/true-cpp.md)和[false](../cpp/false-cpp.md)。 条件表达式不仅具有类型 `bool`，还具有类型 `bool` 的值。 例如，`i!=0`现在具有**true**或**false**根据的值`i`。  

**Visual Studio 2017 15.3 及更高版本**(适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)): 操作数的后缀或前缀递增或递减运算符不能为类型**bool**。 换而言之，给定变量**b**类型的**bool**，不再允许这些表达式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```
  
值**true**和**false**具有以下关系：  
  
```cpp  
!false == true  
!true == false  
```  
  
在下面的语句中：  
  
```cpp  
if (condexpr1) statement1;   
```  
  
如果`condexpr1`是**true**，`statement1`始终执行; 如果`condexpr1`是**false**，`statement1`永远不会执行。  
  
当后缀或前缀**++** 运算符应用于类型的变量的**bool**，则变量设置为**true**。 
**Visual Studio 2017 15.3 及更高版本**: operator + + 为**bool**已从语言删除并且不再受支持。

后缀或前缀**--** 运算符不能应用于此类型的变量。  
  
 **Bool**类型参与了整型提升。 类型的右值**bool**可以转换为右值的类型**int**，与**false**变为 0 和**true**变为 1。 作为截然不同的类型， **bool**参与重载决策。  
  
## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[基本类型](../cpp/fundamental-types-cpp.md)<br/>
