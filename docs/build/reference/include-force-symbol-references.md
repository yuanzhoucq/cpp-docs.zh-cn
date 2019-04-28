---
title: /INCLUDE（强制符号引用）
ms.date: 11/04/2016
f1_keywords:
- /include
- VC.Project.VCLinkerTool.ForceSymbolReferences
helpviewer_keywords:
- INCLUDE linker option
- force symbol references linker option
- symbol references linker force
- /INCLUDE linker option
- symbols, add to symbol table
- -INCLUDE linker option
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
ms.openlocfilehash: 1f7a443e32ed20550e3017c7e6ce70f4adf5137d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269865"
---
# <a name="include-force-symbol-references"></a>/INCLUDE（强制符号引用）

```
/INCLUDE:symbol
```

## <a name="parameters"></a>参数

*symbol*<br/>
指定要添加到符号表中的符号。

## <a name="remarks"></a>备注

/INCLUDE 选项告知链接器将指定的符号添加到符号表。

若要指定多个符号，请键入逗号 （，）、 分号 （;） 或符号名之间有空格。 在命令行中，指定 /INCLUDE:`symbol`一次针对每个符号。

链接器解析`symbol`通过添加包含该程序的符号定义的对象。 此功能可用于包括库对象，否则将不会链接到该程序。

使用此选项指定一个符号，将覆盖由该符号的移除[/opt: ref](opt-optimizations.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击**链接器**文件夹。

1. 单击**输入**属性页。

1. 修改**强制符号引用**属性。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
