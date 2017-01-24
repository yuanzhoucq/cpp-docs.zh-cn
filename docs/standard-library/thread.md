---
title: "&lt; 线程 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<thread>"
dev_langs: 
  - "C++"
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; 线程 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包括标准标头 \< 线程> 定义类 `thread` 和各种支持的函数。  
  
## <a name="syntax"></a>语法  
  
```cpp  
#include <thread>  
```  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  通过使用编译的代码中 **/clr** 或 **/clr: pure**, ，阻止此标头。  
  
  `__STDCPP_THREADS__` 宏定义为非零值以指示线程是否支持通过此标头。  
  
## <a name="members"></a>成员  
  
### <a name="public-classes"></a>公共类  
  
|名称|描述|  
|----------|-----------------|  
|[thread 类](../standard-library/thread-class.md)|定义用于发现和管理的应用程序中的执行线程的对象。|  
  
### <a name="public-structures"></a>公共结构  
  
|名称|描述|  
|----------|-----------------|  
|[hash 结构 (STL)](../standard-library/hash-structure-stl.md)|定义一个成员函数返回一个值，由唯一确定 `thread::id`。 成员函数定义 [哈希](../standard-library/hash-class.md) 适用于类型的映射值的函数 `thread::id` 索引值的分布。|  
  
### <a name="public-functions"></a>公共函数  
  
|名称|描述|  
|----------|-----------------|  
|[get_id 函数](../Topic/%3Cthread%3E%20functions.md#get_id_function)|唯一标识当前执行的线程。|  
|[sleep_for 函数](../Topic/%3Cthread%3E%20functions.md#sleep_for_function)|阻止调用线程。|  
|[sleep_until 函数](../Topic/%3Cthread%3E%20functions.md#sleep_until_function)|阻止调用线程，至少直到指定的时间。|  
|[swap 函数](../Topic/%3Cthread%3E%20functions.md#swap_function)|交换两个状态 `thread` 对象。|  
|[yield 函数](../Topic/%3Cthread%3E%20functions.md#yield_function)|即使当前线程通常将继续运行，则指示要运行其他线程的操作系统。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[运算符 > = 运算符](../Topic/%3Cthread%3E%20operators.md#operator_gt__eq)|确定一个 `thread::id` 对象是否大于或等于另一个。|  
|[运算符 > 运算符](../Topic/%3Cthread%3E%20operators.md#operator_gt_)|确定一个 `thread::id` 对象是否大于另一个。|  
|[运算符 < = 运算符](../Topic/%3Cthread%3E%20operators.md#operator_lt__eq)|确定一个 `thread::id` 对象是否小于或等于另一个。|  
|[运算符 < 运算符](../Topic/%3Cthread%3E%20operators.md#operator_lt_)|确定一个 `thread::id` 对象是否小于另一个。|  
|[运算符 ！ = 运算符](../Topic/%3Cthread%3E%20operators.md#operator_neq)|比较两个 `thread::id` 对象是否相等。|  
|[运算符 = = 运算符](../Topic/%3Cthread%3E%20operators.md#operator_eq_eq)|比较两个 `thread::id` 对象是否相等。|  
|[运算符 << 运算符](../Topic/%3Cthread%3E%20operators.md#operator_lt__lt_)|将文本表示形式插入 `thread::id` 对象插入流。|  
  
## <a name="see-also"></a>请参阅  
 [标头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

