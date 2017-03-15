---
title: "Manifest Resources | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "manifest resources"
  - "resources [Visual Studio], manifest"
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Manifest Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

清单资源是描述应用程序所使用的依赖项的 XML 文件。 例如，在 Visual Studio 中，MFC 向导生成的清单文件定义应用程序应使用的 Windows 公共控件 DLL 是 5.0 版还是 6.0 版：  
  
```  
<description>Your app description here</description> <dependency> <dependentAssembly> <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="X86" publicKeyToken="6595b64144ccf1df" language="*" /> </dependentAssembly> </dependency>   
```  
  
 对于 Windows XP 或 Windows Vista 应用程序，清单资源不仅指定应用程序使用 Windows 公共控件的最新版本（v6.0，如上所示），还支持 [Syslink 控件](http://msdn.microsoft.com/library/windows/desktop/bb760706)。  
  
 若要查看清单资源中包含的版本和类型信息，可在 XML 查看器或 Visual Studio [文本编辑器](http://msdn.microsoft.com/zh-cn/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)中打开该文件。 有关详细信息，请参阅[在 Visual Studio 文本编辑器中打开清单资源](../windows/how-to-open-a-manifest-resource.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 限制  
 每个模块只能有一个清单资源。  
  
## 要求  
 Win32  
  
## 请参阅  
 [控件](../mfc/controls-mfc.md)   
 [Working with Resource Files](../mfc/working-with-resource-files.md)