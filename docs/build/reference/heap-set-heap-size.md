---
title: /HEAP（设置堆大小）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 715eaa358d052d4ae646f38f2e784f0235dffccb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270349"
---
# <a name="heap-set-heap-size"></a>/HEAP（设置堆大小）

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>备注

/HEAP 选项设置堆的大小以字节为单位。 此选项是仅供使用时生成的.exe 文件。

*保留*参数指定虚拟内存中堆分配总量。 默认堆大小为 1 MB。 链接器指定到最接近的 4 个字节的值向上舍入。

可选`commit`参数指定的物理内存来分配一次。 提交的虚拟内存后，在分页文件为保留的空间。 更高`commit`值节省的时间，当应用程序需要更多堆空间，但会增加内存需求并可能延长启动时间。

指定*保留*和`commit`十进制或 C 语言表示法中的值。

此功能仍可通过使用模块定义文件[HEAPSIZE](heapsize.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**系统**属性页。

1. 修改**堆提交大小**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
