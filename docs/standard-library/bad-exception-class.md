---
title: "bad_exception 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.bad_exception"
  - "bad_exception"
  - "std::bad_exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_exception 类"
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# bad_exception 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类描述可从意外处理程序引发的异常。  
  
## <a name="syntax"></a>语法  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>备注  
 [意外](../Topic/%3Cexception%3E%20functions.md#unexpected) 将引发 `bad_exception` 而不是终止或而不是调用另一个使用指定的函数 [set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected) 如果 `bad_exception` 包含在函数引发列表。  
  
 返回的值 **什么** 是实现定义的 C 字符串。 无成员函数引发任何异常。  
  
 有关由继承的成员的列表 `bad_exception` 类，请参阅 [异常类](../standard-library/exception-class1.md)。  
  
## <a name="example"></a>示例  
 请参阅 [set_unexpected](../Topic/%3Cexception%3E%20functions.md#set_unexpected) 有关的使用示例 [意外](../Topic/%3Cexception%3E%20functions.md#unexpected) 引发 `bad_exception`。  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 异常>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
[异常类](../standard-library/exception-class1.md)
 [c + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

