---
title: '&lt;new&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<new>
- <new>
- std.<new>
dev_langs:
- C++
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
caps.latest.revision: 18
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: e804f35db459c7fe50bb36fa8eeaf795d04cc621
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltnewgt"></a>&lt;new&gt;
定义一些类型和函数，它们控制程序控件下存储空间的分配和释放。 它还定义了用于报告存储管理错误的组件。  
  
## <a name="syntax"></a>语法  
  
```  
#include <new>  
  
```  
  
## <a name="remarks"></a>备注  
 此标头中声明的一些函数是可替换的。 该实现提供了一个默认版本，其行为已在本文档中进行了描述。 但是，程序可定义具有相同签名的函数，以在链接时替换默认版本。 替换版本必须满足本文档中描述的要求。  
  
### <a name="objects"></a>对象  
  
|||  
|-|-|  
|[nothrow](../standard-library/new-functions.md#nothrow)|提供一个对象，用作 **new** 和 **delete** 的 `nothrow` 版本的自变量。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[new_handler](../standard-library/new-typedefs.md#new_handler)|一个类型，它指向适合用作新处理程序的函数。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|安装一个用户函数，当尝试分配内存再次失败时会调用该函数。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 delete](../standard-library/new-operators.md#op_delete)|由 delete 表达式调用来解除单个对象的存储空间分配的函数。|  
|[运算符 &#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|由 delete 表达式调用来解除对象数组的存储空间分配的函数。|  
|[运算符 new](../standard-library/new-operators.md#op_new)|由 new 表达式调用来为单个对象分配存储空间的函数。|  
|[运算符 new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|由 new 表达式调用来为对象数组分配存储空间的函数。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[bad_alloc 类](../standard-library/bad-alloc-class.md)|该类描述引发的异常以指示分配请求未成功。|  
|[nothrow_t Class](../standard-library/nothrow-t-structure.md)|该类用作运算符 new 的函数参数，指示函数应返回一个 null 指针来报告分配失败，而不是引发异常。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




