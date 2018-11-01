---
title: 清单资源 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 081fd12a86c31973c7856ca7b9f3fcb129e2eb81
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578277"
---
# <a name="manifest-resources-c"></a>清单资源 （c + +）

在 c + + 桌面项目中，清单资源是描述应用程序使用的依赖项的 XML 文件。 例如，在 Visual Studio 中，MFC 向导生成的清单文件定义应用程序应使用的 Windows 公共控件 DLL 是 5.0 版还是 6.0 版：

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

对于 Windows XP 或 Windows Vista 应用程序，清单资源不仅指定应用程序使用 Windows 公共控件的最新版本（v6.0，如上所示），还支持 [Syslink 控件](/windows/desktop/Controls/syslink-overview)。

若要查看的版本和类型包含在清单资源的信息，可以在 XML 查看器或 Visual Studio 文本编辑器中打开该文件。 有关详细信息，请参阅 [在 Visual Studio 文本编辑器中打开清单资源](../windows/how-to-open-a-manifest-resource.md)。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

## <a name="limitations"></a>限制

每个模块只能有一个清单资源。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[控件](../mfc/controls-mfc.md)<br/>
[使用资源文件](../windows/working-with-resource-files.md)