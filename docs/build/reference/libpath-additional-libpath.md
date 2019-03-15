---
title: /LIBPATH（附加的 Libpath）
ms.date: 11/04/2016
f1_keywords:
- /libpath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
helpviewer_keywords:
- LIBPATH linker option
- /LIBPATH linker option
- Additional Libpath linker option
- environment library path override
- -LIBPATH linker option
- library path linker option
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
ms.openlocfilehash: ab586c788825a854e7d3cb3760da6e4e5558de3a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819878"
---
# <a name="libpath-additional-libpath"></a>/LIBPATH（附加的 Libpath）

```
/LIBPATH:dir
```

## <a name="parameters"></a>参数

*dir*<br/>
指定的路径链接器将搜索之前它将搜索 LIB 环境选项中指定的路径。

## <a name="remarks"></a>备注

使用 /LIBPATH 选项重写环境库路径。 链接器将首先在此选项指定的路径中搜索，然后在 LIB 环境变量中指定的路径中搜索。 可以指定只有一个目录输入每个 /LIBPATH 选项。 如果你想要指定多个目录，则必须指定多个 /LIBPATH 选项。 链接器然后将按顺序搜索指定的目录。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[Visual Studio 中的设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**常规**属性页。

1. 修改**附加库目录**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器引用](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
