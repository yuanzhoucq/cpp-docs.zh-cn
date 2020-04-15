---
title: /SOURCELINK（在 PDB 中包含 Sourcelink）
description: 微软C++/SOURCELINK链接器选项的参考指南。
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336069"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK（在 PDB 中包括源链接文件）

指定要包含在链接器生成的 PDB 文件中的源链接配置文件。

## <a name="syntax"></a>语法

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>参数

*文件名*<br/>
指定一个 JSON 格式的配置文件，该文件包含本地文件路径的简单映射到 URL，以便源文件在调试器中显示。 有关此文件格式的详细信息，请参阅[源链接 JSON 架构](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema)。

## <a name="remarks"></a>备注

源链接是一个语言和源代码管理无关的系统，用于为二进制文件提供源调试。 源链接支持从 Visual Studio 2017 版本 15.8 开始的本机C++二进制文件。 有关源链接的概述，请参阅[源链接](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md)。 有关如何在项目中使用源链接以及如何将 SourceLink 文件生成作为项目的一部分的信息，请参阅[使用源链接](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects)。

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>在可视化工作室中设置 /SOURCELINK 链接器选项

1. 打开项目**的属性页**对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择**配置属性** > **链接器** > **命令行**属性页。

1. 在"**其他选项**"框中，**`/SOURCELINK:`**_`filename`_ 添加然后选择 **"确定"** 或 **"应用"** 以保存更改。

### <a name="to-set-this-linker-option-programmatically"></a>以编程方式设置此链接器选项

- 此选项没有编程等效项。

## <a name="see-also"></a>另请参阅

[MSVC 链接器参考](linking.md)<br/>
[MSVC 链接器选项](linker-options.md)
