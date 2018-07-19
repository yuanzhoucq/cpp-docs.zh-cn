---
title: noexcept （C++） |Microsoft 文档
ms.custom: ''
ms.date: 01/12/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noexcept_cpp
dev_langs:
- C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8eb8e6900dc12e4f176daf63bb711198f5e41429
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939284"
---
# <a name="noexcept-c"></a>noexcept (C++)
**C++ 11:** 指定函数是否可能引发异常。  
  
## <a name="syntax"></a>语法  
  
> *noexcept 表达式*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept(** *constant-expression* **)**  
  
### <a name="parameters"></a>参数  
 *constant-expression*  
 类型的常量表达式**bool**表示潜在的异常类型集是否为空。 无条件版本相当于`noexcept(true)`。  
  
## <a name="remarks"></a>备注  
 一个*noexcept 表达式*是一种类型的*异常规范*，后缀表示一组可通过退出任何异常的异常处理程序相匹配的类型的函数声明函数。 一元条件运算符`noexcept(` *constant_expression* `)`其中*constant_expression* yeilds **true**，及其无条件同义词`noexcept`，指定可以退出函数的潜在异常类型的集为空。 即，该函数从不引发异常并永远不会允许异常传播其作用域之外。 运算符`noexcept(` *constant_expression* `)`其中*constant_expression* yeilds **false**，或不存在的异常规范（以外的析构函数或释放函数），指示可以退出该函数的潜在异常组的所有类型的集合。  
 
 将标记一个函数作为`noexcept`仅当调用，直接或间接的所有函数都都还`noexcept`或**const**。 编译器不一定会检查异常可能归因于每个代码路径`noexcept`函数。 如果异常 does 退出标记的函数的外部作用域`noexcept`， [std:: terminate](../standard-library/exception-functions.md#terminate)立即调用，则将调用的任何范围内对象的析构函数不能保证。 使用`noexcept`而不是动态的异常说明符`throw()`，该标准中现已弃用。 我们建议您应用`noexcept`永远不会允许异常传播到调用堆栈的任何函数。 声明的函数是`noexcept`，它使编译器能够在多种不同的上下文中生成更高效的代码。 有关详细信息，请参阅[异常规范](exception-specifications-throw-cpp.md)。   
  
## <a name="example"></a>示例  
可能会声明复制其自变量的模板函数`noexcept`前提是要复制的对象是普通的旧数据类型 (POD)。 此类函数可以如下声明：  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>请参阅  
 [C++ 异常处理](cpp-exception-handling.md)[异常规范 （throw，noexcept）](exception-specifications-throw-cpp.md)