---
title: "message | Microsoft Docs"
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
  - "message_CPP"
  - "vc-pragma.message"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "消息杂注"
  - "杂注, message"
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# message
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在未结束编译的情况下将字符串发送到标准输出。  
  
## 语法  
  
```  
  
#pragma message( messagestring )  
```  
  
## 备注  
 **message** 杂注的典型用途是在编译时显示信息性消息。  
  
 *messagestring* 参数可以是扩展到字符串的宏，您可以通过任意组合将此类宏与字符串串联起来。  
  
 如果在 **message** 杂注中使用预定义的宏，则该宏应返回字符串，否则必须将该宏的输出转换为字符串。  
  
 以下代码段使用 **message** 杂注在编译过程中显示消息：  
  
```  
// pragma_directives_message1.cpp  
// compile with: /LD  
#if _M_IX86 >= 500  
#pragma message("_M_IX86 >= 500")  
#endif  
  
#pragma message("")  
  
#pragma message( "Compiling " __FILE__ )   
#pragma message( "Last modified on " __TIMESTAMP__ )  
  
#pragma message("")  
  
// with line number  
#define STRING2(x) #x  
#define STRING(x) STRING2(x)  
  
#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")  
  
#pragma message("")  
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)