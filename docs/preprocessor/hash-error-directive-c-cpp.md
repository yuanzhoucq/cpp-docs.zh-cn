---
title: '#error 指令 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: bfb5c18f20319e6e6d345f28d3e1850714334b71
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216119"
---
# <a name="error-directive-cc"></a>#error 指令 (C/C++)

**#Error**指令会在编译时发出用户指定的错误消息, 然后终止编译。

## <a name="syntax"></a>语法

> **#error** *标记-字符串*

## <a name="remarks"></a>备注

此指令发出的错误消息包括*标记字符串*参数。 *标记字符串*参数不受宏展开的限制。 此指令在预处理期间最有用, 通知开发人员程序不一致或约束违规。 下面的示例演示了在预处理期间进行的错误处理:

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
