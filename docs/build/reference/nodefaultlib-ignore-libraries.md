---
title: /NODEFAULTLIB（忽略库）
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: d2bac6f62f7b1a692e5fc40fcf6dea1e10a50927
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424348"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB（忽略库）

```
/NODEFAULTLIB[:library]
```

## <a name="arguments"></a>自变量

*library*<br/>
您希望链接器解析外部引用时忽略的库。

## <a name="remarks"></a>备注

/NODEFAULTLIB 选项通知链接器从其解析外部引用时搜索的库列表中删除一个或多个默认库。

若要创建不包含对默认库的引用的.obj 文件，请使用[/Zl （省略默认库名）](../../build/reference/zl-omit-default-library-name.md)。

默认情况下，/NODEFAULTLIB 从其解析外部引用时搜索的库列表中删除所有默认库。 可选*库*参数允许你从其解析外部引用时搜索的库列表中删除指定的库。 指定你想要排除的每个库 /NODEFAULTLIB 选项。

链接器通过第一次搜索的库中显式指定，则在指定的默认库使用 /DEFAULTLIB 选项，然后在默认库名为.obj 文件中解析对外部定义的引用。

/NODEFAULTLIB:*库*重写[/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*库*时相同*库*中同时指定名称。

如果使用 /NODEFAULTLIB，例如，若要生成无 C 运行时库，程序您可能必须也使用[/ENTRY](../../build/reference/entry-entry-point-symbol.md)在程序中指定的入口点 （函数）。 有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**输入**属性页。

1. 选择**忽略所有默认库**属性，或指定你想要在中忽略的库列表**忽略特定库**属性。 **命令行**属性页将显示对这些属性进行的更改的效果。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
