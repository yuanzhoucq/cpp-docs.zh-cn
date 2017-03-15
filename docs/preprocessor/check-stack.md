---
title: "check_stack | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.check_stack"
  - "check_stack_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "check_stack 杂注"
  - "杂注, check_stack"
  - "杂注, check_stack 使用表"
ms.assetid: f18e20cc-9abb-48b7-ad62-8d384875b996
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# check_stack
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示编译器在指定了 **off**（或 **–**）时关闭堆栈探测或在指定了 **on**（或 **\+**）时打开堆栈探测。  
  
## 语法  
  
```  
  
      #pragma check_stack([ {on | off}] )  
#pragma check_stack{+ | –}  
```  
  
## 备注  
 如果未给定参数，则根据默认设置处理堆栈探测。  此杂注出现后，当定义了第一个函数时，它就会生效。  堆栈探测既不是宏的一部分也不是以内联方式生成的函数的一部分。  
  
 如果为 **check\_stack** 杂注提供参数，堆栈检查将还原为在命令行上指定的行为。  有关详细信息，请参阅[编辑器引用](../build/reference/compiler-options.md)。  **\#pragma check\_stack** 和 [\/Gs](../build/reference/gs-control-stack-checking-calls.md) 选项的交互在下表中进行了汇总。  
  
### 使用 check\_stack 杂注  
  
|语法|是否使用<br /><br /> \/Gs 选项进行编译？|操作|  
|--------|---------------------------|--------|  
|**\#pragma check\_stack\( \)** 或<br /><br /> **\#pragma check\_stack**|是|为后面的函数关闭堆栈检查|  
|**\#pragma check\_stack\( \)** 或<br /><br /> **\#pragma check\_stack**|否|为后面的函数打开堆栈检查|  
|**\#pragma check\_stack\(on\)**<br /><br /> 或 **\#pragma check\_stack \+**|是或否|为后面的函数打开堆栈检查|  
|**\#pragma check\_stack\(off\)**<br /><br /> 或 **\#pragma check\_stack –**|是或否|为后面的函数关闭堆栈检查|  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)