---
title: 项目和解决方案文件 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.files.projectandsolution
dev_langs:
- C++
helpviewer_keywords:
- project files [C++]
- file types [C++], makefiles
- .sdf, browsing database file
- Makefile projects
- browsing database file, .sdf
- file types [C++], project files
ms.assetid: 5823b954-36cf-42d3-8fd5-25bab3ef63d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f52041ef8049e0e7ad4b12677ac1599b2cfd5669
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408177"
---
# <a name="project-and-solution-files"></a>项目和解决方案文件

在 Visual Studio 中创建项目时，会创建以下文件。 它们用于管理解决方案中的项目文件。

|Filename|目录位置|解决方案资源管理器位置|描述|
|--------------|------------------------|--------------------------------|-----------------|
|Solname.sln|Projname|在解决方案资源管理器中不显示|*解决方案*文件。 它将一个或多个项目的所有元素组织到一个解决方案中。|
|Projname.suo|Projname|在解决方案资源管理器中不显示|解决方案选项文件。 它存储解决方案的自定义项，以便每次打开解决方案中的项目或文件时，都具有所需的外观和行为。|
|Projname.vcxproj|Projname|在解决方案资源管理器中不显示|项目文件。 它存储特定于每个项目的信息。 （在早期版本中，此文件命名为 Projname.vcproj 或 Projname.dsp。）有关 Visual C++ 项目文件的示例，请参阅[项目文件](../ide/project-files.md)。|
|Projname.vcxitems|Projname|在解决方案资源管理器中不显示|“共享项”项目文件。 不生成此项目。  相反，另一个 C++ 项目可引用该项目，其文件将成为引用项目生成过程的一部分。 这可用于与跨平台 C++ 项目共享通用代码。|
|Projname.sdf|Projname|在解决方案资源管理器中不显示|浏览数据库文件。 它支持浏览和导航功能，如“转到定义”、“查找所有引用”和“类视图”。 它是通过分析头文件生成的。|
|Projname.vcxproj.filters|Projname|在解决方案资源管理器中不显示|筛选器文件。 它指定在何处放置添加到解决方案的文件。 例如，.h 文件置于“头文件”节点中。|
|Projname.vcxproj.user|Projname|在解决方案资源管理器中不显示|迁移用户文件。 从 Visual Studio 2008 迁移项目之后，此文件包含从任何 .vsprops 文件转换的信息。|
|Projname.idl|Projname|源|（特定于项目）包含控件类型库的接口描述语言 (IDL) 源代码。 此文件由 Visual C++ 用于生成类型库。 生成的库会向其他自动化客户端公开控件的接口。 有关详细信息，请参阅 Windows SDK 中的[接口定义 (IDL) 文件](/windows/desktop/Rpc/the-interface-definition-language-idl-file)。|
|Readme.txt|Projname|项目|自述文件。 它由应用程序向导生成，描述项目中的文件。|

## <a name="see-also"></a>请参阅

[为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)