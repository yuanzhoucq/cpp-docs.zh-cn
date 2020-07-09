---
title: /HEAP
description: MSVC 链接器或 EDITBIN/HEAP 选项设置堆总大小，还可以选择附加堆块的大小。
ms.date: 07/07/2020
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: 7976ae2927ca731c83fa42e87da182fee4df3d7c
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127833"
---
# `/HEAP`

设置堆的大小（以字节为单位）。 此选项仅适用于可执行文件。

## <a name="syntax"></a>语法

> **`/HEAP:`**_`reserve`_\[**`,`**_`commit`_]

## <a name="remarks"></a>备注

*`reserve`* 自变量指定虚拟内存中的初始堆分配总量。 **`/HEAP`** 链接器或[EDITBIN](editbin-reference.md)选项将指定的值向上舍入到4个字节的最接近倍数。 默认情况下，堆大小为 1 MB。

可选 *`commit`* 参数受操作系统的解释。 在 Windows 操作系统中，它指定要分配的初始物理内存量。 它还指定扩展堆时要分配的内存量。 已提交的虚拟内存会导致在页面文件中保留空间。 *`commit`* 如果值较大，则在应用需要更多堆空间时，系统更少地分配内存，但会增加内存需求，并且可能会增加应用程序的启动时间。 *`commit`* 该值必须小于或等于 *`reserve`* 值。 默认值为 4 KB。

*`reserve`* *`commit`* 以十进制、C 语言十六进制或八进制表示法指定和值。 例如，值 1 MB 可指定为十进制的 1048576、十六进制的 0x100000 或八进制的 04000000。 默认值与选项等效 **`/HEAP:1048576,4096`** 。

### <a name="example"></a>示例

此示例 link 命令将创建一个具有 2 MB 堆保留的可执行*main.exe* 。 初始堆和更高版本堆扩展采用 64 KB 的块：

**`link /heap:0x200000,0x10000 main.obj`**

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中设置此链接器选项

1. 打开项目“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**"  >  **链接器**  >  **系统**属性页。

1. 设置**堆预留大小**和**堆提交大小**属性，然后选择 **"确定" 或 "** **应用**" 保存所做的更改。

## <a name="see-also"></a>另请参阅

[EDITBIN 选项](editbin-options.md)\
[MSVC 链接器选项](linker-options.md)
