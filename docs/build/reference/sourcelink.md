---
title: / SOURCELINK （包括 Sourcelink PDB 文件）
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: 1643727d8f556a905eccbfa9626d1aaa8ea63cbf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317947"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/ SOURCELINK （包括源链接 PDB 文件）

指定要包含在链接器生成的 PDB 文件中的源链接配置文件。

## <a name="syntax"></a>语法

> **/ SOURCELINK:**_文件名_

## <a name="arguments"></a>自变量

*filename*<br/>
指定的 JSON 格式配置文件包含 Url 的本地文件路径的简单映射，可以检索源文件由调试器的显示。 此文件的格式的详细信息，请参阅[源链接 JSON 架构](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema)。

## <a name="remarks"></a>备注

源链接是提供源调试二进制文件的语言和源代码管理不可知系统。 源链接支持本机C++在 Visual Studio 2017 版本 15.8 中启动的二进制文件。 源链接的概述，请参阅[源链接](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md)。 有关如何在项目中使用源链接以及如何为你项目的一部分生成 SourceLink 文件的信息，请参阅[使用源链接](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects)。

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>在 Visual Studio 中设置 /SOURCELINK 链接器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在中**其他选项**框中，添加 **/SOURCELINK:**_filename_ ，然后选择**确定**或**应用**若要保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项不具有编程等效项。

## <a name="see-also"></a>请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
