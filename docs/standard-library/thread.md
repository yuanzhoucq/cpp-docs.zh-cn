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
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 9b32de86d2ec84017157cccf1a05b9e9b6802e47
ms.lasthandoff: 02/24/2017

---
# <a name="ltthreadgt"></a>&lt;线程&gt;
包括标准标头\<线程&1;> 定义类`thread`和各种支持的功能。  
  
## <a name="syntax"></a>语法  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  在使用编译的代码中**/clr**，此标头被阻止。  
  
 `__STDCPP_THREADS__`宏被定义为非零值指示此标头支持线程。  
  
## <a name="members"></a>成员  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[thread 类](../standard-library/thread-class.md)|定义用于查看和管理应用程序中执行的线程的对象。|  
  
### <a name="public-structures"></a>公共结构  
  
|名称|说明|  
|----------|-----------------|  
|[hash 结构（C++ 标准库）](../standard-library/hash-structure-stl.md)|定义了成员函数返回一个值，由唯一地确定`thread::id`。 成员函数定义[哈希](../standard-library/hash-class.md)适用于类型的映射值的函数`thread::id`为索引值的分布。|  
  
### <a name="public-functions"></a>公共函数  
  
|名称|说明|  
|----------|-----------------|  
|[get_id 函数](../standard-library/thread-functions.md#get_id_function)|唯一标识当前的执行线程。|  
|[sleep_for 函数](../standard-library/thread-functions.md#sleep_for_function)|阻止调用线程。|  
|[sleep_until 函数](../standard-library/thread-functions.md#sleep_until_function)|阻止调用线程，至少直到指定的时间。|  
|[swap 函数](../standard-library/thread-functions.md#swap_function)|交换两个状态`thread`对象。|  
|[yield 函数](../standard-library/thread-functions.md#yield_function)|表示要运行其他线程的操作系统，即使当前线程会照常继续运行。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[运算符&1;> = 运算符](../standard-library/thread-operators.md#operator_gt__eq)|确定一个 `thread::id` 对象是否大于或等于另一个。|  
|[运算符&1;> 运算符](../standard-library/thread-operators.md#operator_gt_)|确定一个 `thread::id` 对象是否大于另一个。|  
|[运算符<=></=>](../standard-library/thread-operators.md#operator_lt__eq)|确定一个 `thread::id` 对象是否小于或等于另一个。|  
|[运算符<>](../standard-library/thread-operators.md#operator_lt_)|确定一个 `thread::id` 对象是否小于另一个。|  
|[运算符 ！ = 运算符](../standard-library/thread-operators.md#operator_neq)|比较两个 `thread::id` 对象是否相等。|  
|[运算符 = = 运算符](../standard-library/thread-operators.md#operator_eq_eq)|比较两个 `thread::id` 对象是否相等。|  
|[运算符<>](../standard-library/thread-operators.md#operator_lt__lt_)|将 `thread::id` 对象的文本表示形式插入流。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


