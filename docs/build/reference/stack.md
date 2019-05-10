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
ms.openlocfilehash: 6f30877800d4597054601f7459df88c78193fd3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318493"
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

[EDITBIN 选项](editbin-options.md)
