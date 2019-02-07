---
title: 清单资源 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 2d135cb2d512313f107eef7e95ec90d7972b68b4
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850185"
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

将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

若要查看的版本和类型包含在清单资源的信息，可以在 XML 查看器或 Visual Studio 文本编辑器中打开该文件。 如果从 [资源视图](../windows/resource-view-window.md)打开清单资源，则资源将以二进制格式打开。 若要以可视效果更好的格式查看清单资源的内容，必须打开的资源**解决方案资源管理器**。

## <a name="to-open-a-manifest-resource-in-the-text-editor"></a>若要在文本编辑器中打开清单资源

1. 在中打开项目**解决方案资源管理器**，展开**资源文件**文件夹。

1. 双击 .manifest 文件。

   在中打开清单资源**文本编辑器**。

## <a name="to-open-a-manifest-resource-in-another-editor"></a>若要在另一个编辑器中打开清单资源

1. 在中**解决方案资源管理器**，右键单击该.manifest 文件，然后选择**打开方式...** 从快捷菜单。

1. 在中**打开**对话框框中，指定想要使用选择的编辑器**打开**。

## <a name="limitations"></a>限制

每个模块只能有一个清单资源。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[控件](../mfc/controls-mfc.md)<br/>
[使用资源文件](../windows/working-with-resource-files.md)