---
title: 错误 C1189 |Microsoft 文档
ms.custom: ''
ms.date: 04/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 051b7eb965526d12311dfacaeae7a00e4fbe4e75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1189"></a>错误 C1189

> **\#错误：** *用户提供错误消息*

## <a name="remarks"></a>备注

由生成 C1189`#error`指令。 开发人员代码指令指定的错误消息的文本。 有关详细信息，请参阅[#error 指令 （C/c + +）](../../preprocessor/hash-error-directive-c-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C1189。 在示例中，开发人员发出自定义错误消息，因为`_WIN32`未定义标识符：

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>请参阅

[#define 指令 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)