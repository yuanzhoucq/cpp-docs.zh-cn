---
title: "为 CLR 项目创建的文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, CLR programming
- .NET applications, C++
ms.assetid: 59ae9020-5f26-4ad0-bbdd-97c2e2023a20
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4abf5415e9b252a7cc92408fb273d226106fc16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="files-created-for-clr-projects"></a>为 CLR 项目创建的文件
当你使用 Visual c + + 模板创建你的项目时，会创建多个文件，具体取决于哪个模板中，你将使用。 下表列出由.NET Framework 项目的项目模板创建的所有文件。  
  
|文件名|文件说明|  
|---------------|----------------------|  
|AssemblyInfo.cpp|包含的文件信息 （即，特性、 文件、 资源、 类型、 版本控制信息、 签名信息和等等） 用于修改项目的程序集元数据。 有关详细信息请参阅[程序集概念](/dotnet/framework/app-domains/assembly-contents)。|  
|*projname*.asmx|引用托管封装 XML Web 服务的功能的类的文本文件。|  
|*projname*.cpp|主源文件和入口点到应用程序 Visual Studio 为你创建。 标识项目的.dll 文件和项目命名空间。 在此文件中提供你自己的代码。|  
|*projname*.vsdisco|XML 部署文件包含描述 XML Web 服务的其他资源的链接。|  
|*projname*.h|对于项目，其中包含所有声明、 全局符号，主要包含文件和`#include`指令的其他标头文件。|  
|*projname*.sln|在开发环境中用于将你的项目的所有元素都组织到一个解决方案的解决方案文件。|  
|*projname*.suo|在开发环境中使用的解决方案选项文件。|  
|*projname*.vcxproj|在开发环境中存储的信息特定于此项目使用的项目文件。|  
|ReadMe.txt|描述使用由模板创建的实际文件名为项目中每个文件的文件。|