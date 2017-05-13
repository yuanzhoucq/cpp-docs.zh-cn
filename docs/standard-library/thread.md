---
title: "&lt;线程&gt;|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <thread>
dev_langs:
- C++
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
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
ms.openlocfilehash: 496269689428e73dc78893092844afb1650da20d
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltthreadgt"></a>&lt;thread&gt;
包括标准标头\<线程 > 定义类`thread`和各种支持的函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  通过使用编译的代码中**/clr**，阻止此标头。  
  
 `__STDCPP_THREADS__`宏定义为非零值以指示线程是否支持通过此标头。  
  
## <a name="members"></a>成员  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[thread 类](../standard-library/thread-class.md)|定义用于发现和管理的应用程序中的执行线程的对象。|  
  
### <a name="public-structures"></a>公共结构  
  
|名称|描述|  
|----------|-----------------|  
|[hash 结构（C++ 标准库）](../standard-library/hash-structure-stl.md)|定义一个成员函数返回一个值，由唯一确定`thread::id`。 成员函数定义[哈希](../standard-library/hash-class.md)适用于类型的映射值的函数`thread::id`索引值的分布。|  
  
### <a name="public-functions"></a>公共函数  
  
|名称|描述|  
|----------|-----------------|  
|[get_id](../standard-library/thread-functions.md#get_id)|唯一标识当前的执行线程。|  
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|阻止调用线程。|  
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|阻止调用线程，至少直到指定的时间。|  
|[swap](../standard-library/thread-functions.md#swap)|交换两个状态`thread`对象。|  
|[yield](../standard-library/thread-functions.md#yield)|表示要运行其他线程的操作系统，即使当前线程会照常继续运行。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[运算符 > = 运算符](../standard-library/thread-operators.md#op_gt_eq)|确定一个 `thread::id` 对象是否大于或等于另一个。|  
|[运算符 > 运算符](../standard-library/thread-operators.md#op_gt)|确定一个 `thread::id` 对象是否大于另一个。|  
|[运算符 < = 运算符](../standard-library/thread-operators.md#op_lt_eq)|确定一个 `thread::id` 对象是否小于或等于另一个。|  
|[运算符 < 运算符](../standard-library/thread-operators.md#op_lt)|确定一个 `thread::id` 对象是否小于另一个。|  
|[运算符 ！ = 运算符](../standard-library/thread-operators.md#op_neq)|比较两个 `thread::id` 对象是否相等。|  
|[运算符 = = 运算符](../standard-library/thread-operators.md#op_eq_eq)|比较两个 `thread::id` 对象是否相等。|  
|[运算符 << 运算符](../standard-library/thread-operators.md#op_lt_lt)|将 `thread::id` 对象的文本表示形式插入流。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


