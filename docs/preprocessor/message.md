---
title: "消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs: C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad91fdc0fb024fe87c2096f91962f715c0835262
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="message"></a>消息
在未结束编译的情况下将字符串发送到标准输出。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma message( messagestring )  
```  
  
## <a name="remarks"></a>备注  
 一个典型用途**消息**杂注是在编译时显示信息性消息。  
  
 *Messagestring*参数可以是到字符串文本，扩展的宏，并且您可以将此类宏与字符串文字的任意组合。  
  
 如果使用中的预定义的宏**消息**杂注时，该宏应返回一个字符串，否则你将需要将该宏的输出转换为字符串。  
  
 下面的代码片段使用**消息**杂注在编译期间显示消息：  
  
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
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)