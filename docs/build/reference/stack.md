---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 63fcddec8ff8afd81084bb5a2786f394db594b07
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438886"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>备注

此选项设置堆栈的大小（以字节为单位），并以十进制或 C 语言表示法取参数。 /STACK 选项仅适用于可执行文件。

*Reserve*参数指定虚拟内存中的总堆栈分配。 EDITBIN 将指定的值舍入为最接近的4个字节。

可选 `commit` 参数受操作系统的解释。 在 Windows NT、Windows 95 和 Windows 98 中，`commit` 指定一次分配的物理内存量。 已提交的虚拟内存会导致在页面文件中保留空间。 当应用程序需要更多堆栈空间时，较高的 `commit` 值可节省时间，但会增加内存需求和可能的启动时间。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)
