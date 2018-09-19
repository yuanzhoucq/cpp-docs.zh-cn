---
title: 检查内存改写 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 246f625e899016080662f27a5901962c1c62f1a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718636"
---
# <a name="checking-for-memory-overwrites"></a>检查内存改写

如果在将堆操作函数调用收到访问冲突，就可以在程序已经损坏堆。 将这种情况下的一个常见症状：

```
Access Violation in _searchseg
```

[_Heapchk](../../c-runtime-library/reference/heapchk.md)函数是适用于这两个调试和发布版本 (仅适用于 Windows NT) 验证在运行的时库堆的完整性。 可以使用`_heapchk`方法与大致相同`AfxCheckMemory`函数来隔离出堆覆盖，例如：

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

如果此函数失败，您需要找出堆已损坏的位置。

## <a name="see-also"></a>请参阅

[修复发行版本问题](../../build/reference/fixing-release-build-problems.md)