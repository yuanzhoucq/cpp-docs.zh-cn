---
title: / SOURCELINK （包括 Sourcelink PDB 文件） |Microsoft Docs
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /sourcelink
dev_langs:
- C++
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dff53f7a4db12e32bca2494ba99f5b3b8203d48f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706662"
---
# <a name="sourcelink-include-sourcelink-file-in-pdb"></a>/ SOURCELINK （包括 Sourcelink PDB 文件）

指定要由链接器生成的 PDB 文件中包含的 SourceLink 配置文件。

## <a name="syntax"></a>语法

> **/ SOURCELINK:**_文件名_

## <a name="arguments"></a>自变量

*filename*<br/>
指定的 JSON 格式配置文件包含 Url 的本地文件路径的简单映射，可以检索源文件由调试器的显示。 此文件的格式的详细信息，请参阅[源链接 JSON 架构](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema)。

## <a name="remarks"></a>备注

SourceLink 是提供源调试二进制文件的语言和源代码管理不可知系统。 本机 c + + 二进制文件从 Visual Studio 2017 版本 15.8 支持 SourceLink。 SourceLink 的概述，请参阅[源链接](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md)。 有关如何在项目中使用 SourceLink 以及如何为你项目的一部分生成 SourceLink 文件的信息，请参阅[使用 SourceLink](https://github.com/dotnet/sourcelink#using-sourcelink)。

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>在 Visual Studio 中设置 /SOURCELINK 链接器选项

1. 打开**属性页**项目对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在中**其他选项**框中，添加 **/SOURCELINK:**_filename_ ，然后选择**确定**或**应用**若要保存所做的更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项不具有编程等效项。

## <a name="see-also"></a>请参阅

[设置链接器选项](../../build/reference/setting-linker-options.md)<br/>
[链接器选项](../../build/reference/linker-options.md)
