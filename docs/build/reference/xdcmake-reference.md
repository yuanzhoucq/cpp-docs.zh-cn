---
title: XDCMake 参考
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: 9970470d1feb471f9e0b8c9284a08337dac7ef0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335862"
---
# <a name="xdcmake-reference"></a>XDCMake 参考

xdcmake.exe 是一个将 .xdc 文件编译为 .xml 文件的程序。 当使用[/doc](doc-process-documentation-comments-c-cpp.md)编译源代码时，当源代码文件包含用 XML 标记标记标记的文档注释时，MSVC 编译器为每个源代码文件创建了 .xdc 文件。

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中使用 xdcmake.exe

1. 打开项目的“属性页” **** 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 打开“配置属性”文件夹****。

1. 单击“XML 文档注释”属性页****。

> [!NOTE]
> 命令行中的 xdcmake.exe 选项与在开发环境（属性页）中使用 xdcmake.exe 时的选项不同。 若要了解如何在开发环境中使用 xdcmake.exe，请参阅 [XML 文档生成器工具属性页](xml-document-generator-tool-property-pages.md)。

## <a name="syntax"></a>语法

xdcmake `input_filename options`

## <a name="parameters"></a>参数

*input_filename*<br/>
用作 xdcmake.exe 输入的 .xdc 文件的文件名。 指定一个或多个 .xdc 文件或通过 *.xdc 使用当前目录中的所有 .xdc 文件。

*选项*<br/>
零个或多个以下项：

|选项|说明|
|------------|-----------------|
|/?, /help|显示 xdcmake.exe 的帮助。|
|/assembly:*filename*|可用于在 .xml 文件中指定 \<assembly> 标记的值。  默认情况下，\<assembly> 标记的值与 .xml 文件的文件名相同。|
|/nologo|取消显示版权消息。|
|/out:*filename*|可用于指定 .xml 文件的名称。  默认情况下，.xml 文件的名称是由 xdcmake.exe 处理的第一个 .xdc 文件的文件名。|

## <a name="remarks"></a>备注

Visual Studio 将在生成项目时自动调用 xdcmake.exe。 也可在命令行调用 xdcmake.exe。

若要详细了解如何将文档注释添加到源代码文件，请参阅[建议的文档注释标记](recommended-tags-for-documentation-comments-visual-cpp.md)。

## <a name="see-also"></a>另请参阅

[XML 文档](xml-documentation-visual-cpp.md)
