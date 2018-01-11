---
title: "版本信息编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.version.F1
dev_langs: C++
helpviewer_keywords:
- Version Information editor, about Version Information editor
- editors, Version Information
- resource editors, Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c221120bf7170025506fe49fe2ab6419ce66044
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="version-information-editor"></a>版本信息编辑器
版本信息包括公司和产品标识、产品发行版号以及版权与商标通知。 使用版本信息编辑器，可以创建和维护存储在版本信息资源中的这些数据。 虽然应用程序不需要版本信息资源，但它是收集应用程序标识信息的有用位置。 安装 API 也使用版本信息。  
  
 版本信息资源有一个上部块和一个或多个下部块：顶部有一个固定信息块，底部有一个或多个版本信息块（适用于其他语言和/或字符集）。 顶部块设有可编辑的数字框和可选择的下拉列表。 下部块仅包含可编辑的文本框。  
  
> [!NOTE]
>  Windows 标准是只具有一个名为 VS_VERSION_INFO 的版本资源。  
  
 使用“版本信息”编辑器，可以：  
  
-   [编辑版本信息资源中的字符串](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [添加其他语言的版本信息（新版本信息块）](../windows/adding-version-information-for-another-language.md)  
  
-   [删除版本信息块](../windows/deleting-a-version-information-block.md)  
  
-   [在程序内访问版本信息](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  使用版本信息编辑器时，在许多情况下可以单击鼠标右键以显示资源命令的快捷菜单。 例如，如果你在指向块头条目时单击鼠标，快捷菜单将显示“新建版本块信息”和“删除版本块信息”命令。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [资源编辑器](../windows/resource-editors.md)   
 [菜单和其他资源](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

