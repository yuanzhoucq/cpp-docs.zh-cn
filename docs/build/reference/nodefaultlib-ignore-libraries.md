---
title: /NODEFAULTLIB（忽略库）
ms.date: 03/26/2019
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
ms.openlocfilehash: 24528eb4c387c4cd0921ab089370d72b076ad640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320509"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB（忽略库）

> **/NODEFAULTLIB**[__:__*库*]

## <a name="arguments"></a>自变量

*library*<br/>
您希望链接器解析外部引用时忽略的库。

## <a name="remarks"></a>备注

/NODEFAULTLIB 选项通知链接器从其解析外部引用时搜索的库列表中删除一个或多个默认库。

若要创建不包含对默认库引用的.obj 文件，请使用[/Zl （省略默认库名）](zl-omit-default-library-name.md)。

默认情况下，/NODEFAULTLIB 从其解析外部引用时搜索的库列表中删除所有默认库。 可选*库*参数允许你从其解析外部引用时搜索的库列表中删除指定的库。 指定你想要排除的每个库 /NODEFAULTLIB 选项。

链接器通过在显式指定，则在指定的默认库使用的库中的第一次搜索解析对外部定义的引用[/DEFAULTLIB:](defaultlib-specify-default-library.md)选项，然后在默认库名为.obj 中文件。

/NODEFAULTLIB:*库*重写 /DEFAULTLIB:*库*时相同*库*中同时指定名称。

如果使用 /NODEFAULTLIB 以生成无 C 运行时库的应用程序，您可能需要也使用[/ENTRY](entry-entry-point-symbol.md)可在程序中指定的入口点函数。 有关详细信息，请参阅 [ CRT 库功能](../../c-runtime-library/crt-library-features.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **输入**属性页。

1. 选择**忽略所有默认库**属性。 或者，指定你想要在中忽略的库之间用分号分隔的列表**忽略特定默认库**属性。 **命令行**属性页显示了对这些属性进行的更改的效果。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参见 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
