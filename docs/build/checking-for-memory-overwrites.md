---
title: 检查内存改写
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342257"
---
# <a name="checking-for-memory-overwrites"></a>检查内存改写

如果在调用堆操作函数时出现访问冲突，则可能是程序损坏了堆。 这种情况的一个常见症状是：

```
Access Violation in _searchseg
```

[_heapchk](../c-runtime-library/reference/heapchk.md) 函数可在调试和发布版本（仅 Windows NT）中用于验证运行时库堆的完整性。 可以按照与 `AfxCheckMemory` 函数大致相同的方式来使用 `_heapchk` 隔离堆覆盖，例如：

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

如果此函数失败，则需要隔离堆损坏的位置。

## <a name="see-also"></a>请参阅

[修复发行版本问题](fixing-release-build-problems.md)
