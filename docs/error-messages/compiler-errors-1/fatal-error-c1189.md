---
title: 错误 C1189 |Microsoft 文档
ms.custom: ''
ms.date: 04/27/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1189
dev_langs:
- C++
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49f227b5fda20ab0ba202d3d7eca99492509b35
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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