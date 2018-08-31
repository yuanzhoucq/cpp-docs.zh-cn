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
ms.openlocfilehash: e1520cd301fa46fb4d9521fd6d4180ebd3710f67
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218245"
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

对于 Windows XP 或 Windows Vista 的应用程序，清单资源不仅指定应用程序使用的最新版本的 Windows 公共控件 (v6.0，如上图所示)，但它也支持[Syslink 控件](/windows/desktop/Controls/syslink-overview)。

若要查看的版本和类型包含在清单资源的信息，可以打开该文件，在 XML 查看器或 Visual Studio 中[文本编辑器](https://msdn.microsoft.com/508e1f18-99d5-48ad-b5ad-d011b21c6ab1)。 有关详细信息，请参阅 [在 Visual Studio 文本编辑器中打开清单资源](../windows/how-to-open-a-manifest-resource.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[演练： Using Resources for Localization with ASP.NET](https://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="limitations"></a>限制

每个模块只能有一个清单资源。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[控件](../mfc/controls-mfc.md)  
[使用资源文件](../windows/working-with-resource-files.md)