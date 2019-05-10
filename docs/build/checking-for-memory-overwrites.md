---
title: 检查内存改写
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342257"
---
# <a name="checking-for-memory-overwrites"></a>检查内存改写

如果在将堆操作函数调用收到访问冲突，就可以在程序已经损坏堆。 将这种情况下的一个常见症状：

```
Access Violation in _searchseg
```

[_Heapchk](../c-runtime-library/reference/heapchk.md)函数是适用于这两个调试和发布版本 (仅适用于 Windows NT) 验证在运行的时库堆的完整性。 可以使用`_heapchk`方法与大致相同`AfxCheckMemory`函数来隔离出堆覆盖，例如：

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

如果此函数失败，您需要找出堆已损坏的位置。

## <a name="see-also"></a>请参阅

[修复发行版本问题](fixing-release-build-problems.md)
