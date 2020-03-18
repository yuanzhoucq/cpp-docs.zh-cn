---
title: /HEAP（设置堆大小）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: f155ad56ec1a90479b402e38e7ec7f3e3d80e470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439522"
---
# <a name="heap-set-heap-size"></a>/HEAP（设置堆大小）

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>备注

/HEAP 选项设置堆的大小（以字节为单位）。 此选项仅在生成 .exe 文件时使用。

*Reserve*参数指定虚拟内存中的总堆分配。 默认堆大小为 1 MB。 链接器将指定的值向上舍入为最接近的4个字节。

可选 `commit` 参数指定一次分配的物理内存量。 已提交的虚拟内存会导致在页面文件中保留空间。 当应用程序需要更多堆空间时，较高的 `commit` 值可节省时间，但会增加内存需求和可能的启动时间。

以十进制或 C 语言表示法指定*reserve*和 `commit` 值。

此功能也可通过包含[HEAPSIZE](heapsize.md)的模块定义文件使用。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 单击“链接器”文件夹。

1. 单击 "**系统**" 属性页。

1. 修改 "**堆提交大小**" 属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
