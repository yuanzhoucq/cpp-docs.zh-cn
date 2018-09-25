---
title: 其他语言的向导支持 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c33858e02fd8bad03e03a963e940f215d528157d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395121"
---
# <a name="wizard-support-for-other-languages"></a>其他语言的向导支持

安装 Visual Studio 时，安装程序会检测系统中列出的区域设置，并为该区域设置安装适当的语言模板。 例如，对于西欧区域设置，安装程序安装英语、法语、意大利语、西班牙语和德语。 这些语言显示在 MFC 应用程序向导的[应用程序类型](../mfc/reference/application-type-mfc-application-wizard.md)页上的“资源语言”列表中。

## <a name="language-templates"></a>语言模板

并非所有系统都安装了全部模板，因为模板是基于 ANSI 编码的，但部分资源在某些系统上不可编辑。 例如，默认情况下，无法在法语系统上编辑日语资源。

如果使用的是 Windows 2000 或更高版本，且希望按不同的语言创建 MFC 应用程序，必须将相应语言的模板目录从 Visual Studio 安装程序介质（磁盘 1）复制到系统中。

> [!NOTE]
>  要编辑已创建的项目，必须将系统区域设置设为所选语言的相应区域设置。

在 \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\ 目录中为每个模板分配一个文件夹，如下表所示。 要访问所需的语言模板，请将相应的文件夹复制到计算机的 \mfcappwiz\templates\ 目录中。 复制文件夹后，该语言显示在 MFC 应用程序向导的“应用程序类型”页上的“资源语言”列表中。

### <a name="language-templates-provided-in-visual-studio-net"></a>Visual Studio .NET 中提供的语言模板

|语言|模板|
|--------------|--------------|
|和 SharePoint 2010 显示的“中文(繁体)”|1028|
|中文（简体）|2052|
|英语|1033|
|法语|1036|
|德语|1031|
|意大利语|1040|
|日语|1041|
|朝鲜语|1042|
|西班牙语|3082|

## <a name="format-of-visual-c-wizard-generated-files"></a>Visual C++ 向导生成的文件的格式

已安装的 Visual Studio 语言版本与系统区域设置不匹配时，Visual C++ 向导将生成 Unicode 格式的项目。 例如，在将区域设置设为除日语外的任何语言的计算机上安装日语版 Visual Studio 时，Visual C++ 向导将生成由 Unicode 文件组成的项目。 这在使用 Windows 多语言 (MUI) 包进行设置的计算机上很常见。

此行为与系统设置不同，它将导致系统区域设置与 Visual Studio 的语言版本相同。 此情况下，将在系统代码页中创建 ANSI 格式的项目文件。

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[创建和管理 Visual C++ 项目](../ide/creating-and-managing-visual-cpp-projects.md)