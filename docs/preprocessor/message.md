---
title: message 杂注
ms.date: 08/29/2019
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: 48605fbef3b6d81c140e663e950429cd3dcf9b19
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218793"
---
# <a name="message-pragma"></a>message 杂注

在未结束编译的情况下将字符串发送到标准输出。

## <a name="syntax"></a>语法

> **#pragma 消息 (** *消息字符串* **)**

## <a name="remarks"></a>备注

**消息**杂注的典型用法是在编译时显示信息性消息。

*消息字符串*参数可以是扩展到字符串文字的宏, 你可以使用任意组合将此类宏与字符串文字连接起来。

如果在**消息**杂注中使用预定义的宏, 宏应返回一个字符串。 否则, 你必须将宏的输出转换为字符串。

下面的代码片段使用**消息**杂注在编译过程中显示消息:

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

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
