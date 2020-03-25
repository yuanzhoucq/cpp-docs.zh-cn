---
title: 错误 C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203617"
---
# <a name="fatal-error-c1189"></a>错误 C1189

> **\#错误：** *用户提供的错误消息*

## <a name="remarks"></a>备注

C1189 是由 `#error` 指令生成的。 编码指令的开发人员指定错误消息的文本。 有关详细信息，请参阅[#error 指令（CC++/）](../../preprocessor/hash-error-directive-c-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C1189。 在此示例中，开发人员发出自定义错误消息，因为未定义 `_WIN32` 标识符：

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>另请参阅

[#define 指令 (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)
