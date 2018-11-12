---
title: XML 文档 (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: 380fe73bba71d08bb9315e218f5946a7cf935108
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523881"
---
# <a name="xml-documentation-visual-c"></a>XML 文档 (Visual C++)

在 Visual C++ 中，可将注释添加到要被处理为 .xml 文件的源代码中。 之后，可在为代码中的类创建文档的进程中输入此文件。

在 Visual C++ 代码文件中，XML 文档注释必须位于方法或类型定义之前。 下述情况下，可在 IntelliSense QuickInfo 数据提示中填写注释：

1. 将代码编译成带 .winmd 文件的 Windows 运行时组件时

1. 当前项目包含源代码时

1. 在其类型声明和实现位于同一头文件的库中

> [!NOTE]
>  在当前发布版本中，不在模板或包含模板类型的任何内容（例如将参数作为模板的函数）上处理代码注释。 添加此类注释将导致未定义的行为。

若要详细了解如何创建带文档注释的 .xml 文件，请参阅以下主题。

|有关以下内容的信息|查看|
|---------------------------|---------|
|要使用的编译器选项|[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|
|可用于在文档中提供常用功能的标记|[建议的文档注释标记](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|
|编译器生成的用于标识代码中构造的 ID 字符串|[处理 .xml 文件](../ide/dot-xml-file-processing.md)|
|如何分隔文档标记|[Visual C++ 文档标记的分隔符](../ide/delimiters-for-visual-cpp-documentation-tags.md)|
|基于一个或多个 .xdc 文件生成 .xml 文件。|[XDCMake 参考](../ide/xdcmake-reference.md)|
|与 Visual Studio 功能区有关的 XML 相关信息的链接|[Visual Studio 中的 XML](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

如果需要在文档注释的文本中添加 XML 特殊字符，必须使用 XML 实体或 CDATA 节。

## <a name="see-also"></a>请参阅

[适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)