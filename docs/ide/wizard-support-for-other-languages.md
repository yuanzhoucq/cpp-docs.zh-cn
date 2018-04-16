---
title: "其他语言的向导支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef95c252621aa7f725098dfcd08c7b5b3620826
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="wizard-support-for-other-languages"></a>其他语言的向导支持
在安装 Visual Studio 时，安装应用程序检测到你的系统中列出的区域设置，并安装相应的语言模板或该区域设置的模板。 例如，对于西方欧洲区域设置，安装程序将安装英语、 法语、 意大利语、 西班牙语和德语。 这些语言出现在**资源语言**列表上[应用程序类型](../mfc/reference/application-type-mfc-application-wizard.md)MFC 应用程序向导页。  
  
## <a name="language-templates"></a>语言模板  
 并非所有的模板被安装在所有系统上，因为模板是基于 ANSI 编码，和可以在所有系统上编辑并非所有资源。 例如，默认情况下，无法编辑日语法语系统上的资源。  
  
 如果你使用的 Windows 2000 或更高版本，并且你想要在另一种语言中创建 MFC 应用程序，则必须复制适当的语言的模板目录从 Visual Studio 安装程序介质 (磁盘 1) 对你的系统。  
  
> [!NOTE]
>  若要编辑已创建的项目，你必须设置为所选语言的相应区域设置的系统区域设置。  
  
 模板是每个分配 \Microsoft Visual Studio.NET 2003\Vc7\VCWizards\mfcappwiz\templates\ 目录中中的文件夹下表中列出。 若要访问所需的语言模板，将相应文件夹复制到你的计算机上的 \mfcappwiz\templates\ 目录。 语言后已复制文件夹，将显示在**资源语言**列表上**应用程序类型**MFC 应用程序向导页。  
  
### <a name="language-templates-provided-in-visual-studio-net"></a>Visual Studio.NET 中提供的语言模板  
  
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
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Visual c + + 向导生成的文件格式  
 已安装的语言版本的 Visual Studio 与系统区域设置不匹配时，Visual c + + 向导将在 Unicode 中生成项目。 例如，如果已设置为日语以外的任何语言的区域设置的计算机上安装 Visual Studio 的日语版本，Visual c + + 向导将生成项目组成 Unicode 文件。 这是常见使用 Windows 多语言 (MUI) 包设置的计算机上。  
  
 此行为不同于设置以便系统区域设置是语言版本的 Visual Studio 相同的系统。 在这种情况下，项目将在创建文件采用 ANSI 的系统代码页。  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)   
 [创建和管理 Visual C++ 项目](../ide/creating-and-managing-visual-cpp-projects.md)