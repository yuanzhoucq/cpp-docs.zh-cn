---
title: /FORCE（强制文件输出）
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: d1d85174290faa95e73c63a25f7d80c554e83ace
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079630"
---
# <a name="force-force-file-output"></a>/FORCE（强制文件输出）

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>备注

/FORCE 选项通知链接器创建有效 .exe 文件或 DLL，即使引用了符号但未定义或被多次定义也是如此。

/FORCE 选项可以采用可选参数：

- 使用/FORCE： MULTIPLE 可创建输出文件，而不管 LINK 是否找到某个符号的多个定义。

- 使用/FORCE：无法解析以创建输出文件，而不管 LINK 是否找到未定义的符号。 /FORCE：如果入口点符号未解析，则忽略未解析的。

不带参数的/FORCE 表示多重和未解析。

使用此选项创建的文件可能无法按预期运行。 指定/FORCE 选项后，链接器不会进行增量链接。

如果模块是使用 **/clr**编译的，则 **/force**将不会创建映像。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 右键单击 "**解决方案资源管理器**中的项目，然后选择"**属性**"。

1. 单击“链接器”文件夹。

1. 点击“命令行” 属性页。

1. 在 "**附加选项**" 框中键入选项。

有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
