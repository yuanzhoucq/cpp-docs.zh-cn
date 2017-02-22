---
title: "&lt;exception&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<exception>"
  - "std::<exception>"
  - "std.<exception>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exception 标头"
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;exception&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义与异常处理相关的若干类型和函数。 异常处理用于系统可从错误中恢复的情形。 它提供了将控制权从函数返回给程序的一种方法。 合并异常处理的目标是提高程序的可靠性，同时提供一种有序地从错误中恢复的方法。  
  
## <a name="syntax"></a>语法  
  
```  
#include <exception>  
  
```  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[exception_ptr](../Topic/%3Cexception%3E%20typedefs.md#exception_ptr)|该类型描述指向异常的指针。|  
|[terminate_handler](../Topic/%3Cexception%3E%20typedefs.md#terminate_handler)|该类型描述指向适合用作 `terminate_handler` 的函数的指针。|  
|[unexpected_handler](../Topic/%3Cexception%3E%20typedefs.md#unexpected_handler)|该类型描述指向适合用作 `unexpected_handler` 的函数的指针。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[current_exception](../Topic/%3Cexception%3E%20functions.md#current_exception)|获取指向当前异常的指针。|  
|[get_terminate](../Topic/%3Cexception%3E%20functions.md#get_terminate)|获取当前的 `terminate_handler` 函数。|  
|[get_unexpected](../Topic/%3Cexception%3E%20functions.md#get_unexpected)|获取当前的 `unexpected_handler` 函数。|  
|[make_exception_ptr](../Topic/%3Cexception%3E%20functions.md#make_exception_ptr)|创建保留异常副本的 `exception_ptr` 对象。|  
|[rethrow_exception](../Topic/%3Cexception%3E%20functions.md#rethrow_exception)|引发作为参数传递的异常。|  
|[set_terminate](../Topic/%3Cexception%3E%20functions.md#set_terminate)|建立程序终止时要调用的新 `terminate_handler`。|  
|[set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected)|建立遇到意外异常时要调用的新 `unexpected_handler`。|  
|[终止](../Topic/%3Cexception%3E%20functions.md#terminate)|调用终止处理程序。|  
|[uncaught_exception](../Topic/%3Cexception%3E%20functions.md#uncaught_exception)|返回 **true** 仅当当前正在处理引发的异常。|  
|[意外](../Topic/%3Cexception%3E%20functions.md#unexpected)|调用意外处理程序。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[bad_exception 类](../standard-library/bad-exception-class.md)|该类描述可从 `unexpected_handler` 引发的异常。|  
|[exception 类](Exception%20Class.xml)|该类用作某些表达式和标准 C++ 库所引发的所有异常的基类。|  
  
## <a name="see-also"></a>请参阅  
 [标头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

