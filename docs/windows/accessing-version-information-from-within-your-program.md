---
title: "内访问版本信息从你的程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.version
dev_langs: C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e9d47a4df27333afc5d267e791e20d1ed4fe8430
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-version-information-from-within-your-program"></a>从程序内访问版本信息
### <a name="to-access-version-information-from-within-your-program"></a>在程序内访问版本信息  
  
1.  如果想要在程序内访问版本信息，请使用 [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) 函数和 [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) 函数。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [版本信息编辑器](../windows/version-information-editor.md)   
 [版本信息 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

