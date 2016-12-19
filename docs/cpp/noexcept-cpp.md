---
title: "noexcept (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noexcept_cpp"
dev_langs: 
  - "C++"
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# noexcept (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+11：**指定函数是否可能会引发异常。  
  
## 语法  
  
```vb  
ReturnType FunctionName(params) noexcept;  
ReturnType FunctionName(params) noexcept(noexcept(expression);  
```  
  
#### 参数  
 表达式  
 计算结果是 True 或 False 的常量表达式。  无条件版本相当于 noexcept\(true\)。  
  
## 备注  
 `noexcept`（及其同义词 `noecept(true)`）指定函数绝不会引发异常，或允许从异常直接或间接调用的任何其他函数传播异常。  更具体地说，`noexcept` 意味着，仅当调用的所有函数也为 noexcept 或 const 并且没有要求运行时检查、应用于类型为多态类类型的 glvalue 表达式的 typeid 表达式或 throw 表达式的潜在已评估转换时，该函数才是 `noexcept`。  但是，编译器不一定会检查可能归因于 `noexcept` 函数的异常的每个代码路径。  如果异常确实到达标记为 `noexcept` 的函数，则会立即调用 [std::terminate](../Topic/terminate%20\(%3Cexception%3E\).md)，并且不会保证将调用任何范围内对象的析构函数。  
  
 使用条件 noexcept 声明的且计算结果为 noexcept\(false\) 的函数指定它确实允许传播异常。  例如，当要复制的对象是普通的旧数据类型 \(POD\) 时，可将复制其参数的函数声明为 noexcept。  此类函数可以如下声明：  
  
```  
#include <type_traits>  
  
template <typename T>  
T copy_object(T& obj) noexcept(std::is_pod<T>)  
{  
 //. . .   
}  
  
```  
  
 使用 `noexcept` 代替异常说明符 `throw`，后者在 C\+\+11 和更高版本中已弃用。  当你确信函数绝不允许异常传播到调用堆栈时，我们建议你将 `noexcept` 应用到函数。  使用 `noexcept` 声明的函数使编译器可以在多种不同的上下文中生成更高效的代码。  
  
## 请参阅  
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)