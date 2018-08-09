---
title: 清单资源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifest resources
- resources [Visual Studio], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1546beabadda06c5433450f67e340eaaabb0aa26
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012269"
---
# <a name="manifest-resources"></a>清单资源
清单资源是描述应用程序所使用的依赖项的 XML 文件。 例如，在 Visual Studio 中，MFC 向导生成的清单文件定义应用程序应使用的 Windows 公共控件 DLL 是 5.0 版还是 6.0 版：  
  
```xml  
<description>Your app description here</description>   
<dependency>   
    <dependentAssembly>   
        <assemblyIdentity   
            type="win32"   
            name="Microsoft.Windows.Common-Controls"   
            version="6.0.0.0"   
            processorArchitecture="X86"   
            publicKeyToken="6595b64144ccf1df"   
            language="*"   
        />   
    </dependentAssembly>   
</dependency>   
```  
  
 对于 Windows XP 或 Windows Vista 应用程序，清单资源不仅指定应用程序使用 Windows 公共控件的最新版本（v6.0，如上所示），还支持 [Syslink 控件](http://msdn.microsoft.com/library/windows/desktop/bb760706)。  
  
 若要查看的版本和类型包含在清单资源的信息，可以打开该文件，在 XML 查看器或 Visual Studio 中[文本编辑器](http://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)。 有关详细信息，请参阅 [在 Visual Studio 文本编辑器中打开清单资源](../windows/how-to-open-a-manifest-resource.md)。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅  [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="limitations"></a>限制  
 每个模块只能有一个清单资源。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [控件](../mfc/controls-mfc.md)   
 [使用资源文件](../windows/working-with-resource-files.md)