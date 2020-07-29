---
title: /EXPORT（导出函数）
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
ms.openlocfilehash: a55b2a4ce72de644fe426894ab389f62bd29b204
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232685"
---
# <a name="export-exports-a-function"></a>/EXPORT（导出函数）

从程序按名称或序号或数据导出函数。

## <a name="syntax"></a>语法

> **/Export：**<em>entryname</em>[**， \@ **<em>ordinal</em>[**，NONAME**]] [**，DATA**]

## <a name="remarks"></a>备注

**/Export**选项指定要从程序导出的函数或数据项，以便其他程序可以调用函数或使用数据。 通常，导出是在 DLL 中定义的。

*Entryname*是函数或数据项的名称，因为它将由调用程序使用。 *序数*指定导出表中1到65535范围内的索引;如果未指定*序数*，则 LINK 分配一个。 **NONAME**关键字只将函数作为序号导出，而不包含*entryname*。

**Data**关键字指定导出项为数据项。 必须使用**extern __declspec （dllimport）** 声明客户端程序中的数据项。

有四种导出定义的方法，按建议使用顺序列出：

1. 源代码中的[__declspec （dllexport）](../../cpp/dllexport-dllimport.md)

1. .Def 文件中的[导出](exports.md)语句

1. LINK 命令中的 /EXPORT 规范

1. 源代码中的[注释](../../preprocessor/comment-c-cpp.md)指令，其形式为 `#pragma comment(linker, "/export: definition ")` 。

所有这些方法都可以在同一程序中使用。 当 LINK 生成包含导出的程序时，它还会创建一个导入库，除非在生成中使用 exp 文件。

LINK 使用标识符的修饰形式。 编译器在创建 .obj 文件时修饰标识符。 如果将*entryname*指定给链接器的未修饰形式（如源代码中显示的那样），则 LINK 尝试匹配该名称。 如果找不到唯一匹配项，则 LINK 发出错误消息。 需要将[DUMPBIN](dumpbin-reference.md)工具指定给链接器时，可使用工具获取该标识符的[修饰名称](decorated-names.md)格式。

> [!NOTE]
> 不要指定已声明或的 C 标识符修饰形式 **`__cdecl`** **`__stdcall`** 。

如果需要导出未修饰的函数名称，并且具有不同的导出（具体取决于生成配置（例如，在32位或64位生成中），则可以对每个配置使用不同的 .DEF 文件。 （.DEF 文件中不允许使用预处理器条件指令。）作为替代方法，可以 `#pragma comment` 在函数声明之前使用指令，如下所示，其中 `PlainFuncName` 是未修饰的名称， `_PlainFuncName@4` 是函数的修饰名：

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性**  >  **链接器**  >  **命令行**" 属性页。

1. 在 "**附加选项**" 框中输入选项。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
