---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 89591a9d0a7f19422275b6bce6f4c5a7a723e800
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647695"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>备注

此选项以字节为单位设置堆栈大小，并采用十进制或 C 语言表示法的参数。 /STACK 选项仅适用于可执行文件。

*保留*参数指定的总堆栈分配虚拟内存中。 EDITBIN 调高到最接近的 4 个字节指定的值。

可选`commit`参数是取决于操作系统的解释。 在 Windows NT、 Windows 95 和 Windows 98`commit`指定一次分配的物理内存量。 提交的虚拟内存后，在分页文件为保留的空间。 更高`commit`值节省的时间，当应用程序需要更多堆栈空间但会增加内存需求并可能延长启动时间。

## <a name="see-also"></a>请参阅

[EDITBIN 选项](../../build/reference/editbin-options.md)