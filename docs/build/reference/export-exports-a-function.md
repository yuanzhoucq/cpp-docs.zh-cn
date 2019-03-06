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
ms.openlocfilehash: 86e2dadbfcdc31d5d5f5fe3121c33f9011c14ab5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414378"
---
# <a name="export-exports-a-function"></a>/EXPORT（导出函数）

导出函数按名称或序号或数据，从您的程序。

## <a name="syntax"></a>语法

> **/EXPORT:**<em>entryname</em>[**，\@**<em>序号</em>[**，NONAME**]] [**，数据**]

## <a name="remarks"></a>备注

**/Export**选项指定要从您的程序中，以便其他程序可以调用该函数或使用的数据导出的函数或数据的项。 通常在 DLL 中定义导出。

*Entryname*是函数或数据的项的名称，因为它是由调用程序。 *序号*如果未指定范围从 1 到 65,535; 导出表中指定索引*序号*，链接将分配一个。 **NONAME**关键字仅作为序号，导出该函数不带*entryname*。

**数据**关键字指定导出的项目的数据项。 必须使用声明中的客户端程序的数据项**extern __declspec （dllimport)**。

有四种方法用于导出的定义，建议使用的顺序依次列出：

1. [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)中的源代码

1. [导出](../../build/reference/exports.md).def 文件语句

1. LINK 命令中 /EXPORT 规范

1. 一个[注释](../../preprocessor/comment-c-cpp.md)指令中的源代码的窗体`#pragma comment(linker, "/export: definition ")`。

可以在同一程序中使用所有这些方法。 当 LINK 在生成包含导出的程序时，它还创建导入库，除非生成中使用了.exp 文件。

链接使用修饰形式的标识符。 创建的.obj 文件时，编译器将修饰标识符。 如果*entryname*中其未修饰链接器指定窗体 （即显示在源代码中） 中，尝试与名称匹配链接。 如果它找不到唯一的匹配项，链接会发出一条错误消息。 使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具来获取[修饰名](../../build/reference/decorated-names.md)窗体时需要指定链接器的标识符。

> [!NOTE]
> 未指定 C 标识符声明的修饰的形式`__cdecl`或`__stdcall`。

如果你需要导出未修饰的函数名，并且具有不同的导出，具体取决于生成配置 （例如，在 32 位或 64 位版本），您可以为每个配置使用不同 DEF 文件。 （预处理器条件指令不是允许在 DEF 文件中。）作为替代方法，你可以使用`#pragma comment`指令之前的函数声明如下所示，其中`PlainFuncName`是未修饰的名称，和`_PlainFuncName@4`是该函数的修饰的名：

```cpp
#pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
BOOL CALLBACK PlainFuncName( Things * lpParams)
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此链接器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置 Visual c + + 项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 该选项输入**其他选项**框。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
