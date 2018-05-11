---
title: 消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs:
- C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47b9fd580d1ebabf4352104fe49f1d3c982a49e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
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