---
title: 消息
ms.date: 11/04/2016
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: e9383238fd308ec59a9767f56af1c07fc3cfcf07
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030201"
---
# <a name="message"></a>消息
在未结束编译的情况下将字符串发送到标准输出。

## <a name="syntax"></a>语法

```
#pragma message( messagestring )
```

## <a name="remarks"></a>备注

一个典型用途**消息**杂注是在编译时显示信息性消息。

*Messagestring*参数可以是字符串文字，到扩展的宏，并可以将此类宏与字符串的任意组合串联起来。

如果您使用在预定义的宏**消息**杂注，该宏应返回一个字符串，否则需要将宏的输出转换为字符串。

使用下面的代码段**消息**杂注在编译期间显示消息：

```cpp
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