---
title: Windows 公共控件的生成要求
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: cf2139e04d2f72feb7951010caa351d67ccc5a93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619746"
---
# <a name="build-requirements-for-windows-common-controls"></a>Windows 公共控件的生成要求

Microsoft 基础类（MFC）库支持[Windows 公共控件](/windows/win32/controls/common-controls-intro)。 公共控件包含在 Windows 中，库包含在 Visual Studio 中。 MFC 库提供了增强现有类的新方法，以及支持 Windows 公共控件的其他类和方法。 在生成应用程序时，应该遵循后续章节中所述的编译和迁移需求。

## <a name="compilation-requirements"></a>编译需求

### <a name="supported-versions"></a>支持的版本

MFC 支持所有版本的公共控件。 有关 Windows 公共控件版本的信息，请参阅[公共控件版本](/windows/win32/controls/common-control-versions)。

### <a name="supported-character-sets"></a>支持的字符集

Windows 公共控件仅支持 Unicode 字符集，而不支持 ANSI 字符集。 如果您在命令行中生成应用程序，请使用以下两个 define (/D) 编译器选项指定 Unicode 字符集作为基础字符集：

```
/D_UNICODE /DUNICODE
```

如果在 Visual Studio 集成开发环境（IDE）中生成应用程序，请在项目属性的 "**常规**" 节点中指定 "**字符集**" 属性的 " **Unicode 字符集**" 选项。

## <a name="migration-requirements"></a>迁移需求

如果使用 Visual Studio IDE 生成使用 Windows 公共控件的新 MFC 应用程序，IDE 将自动声明相应的清单。 但是，如果从 Visual Studio 2005 或更早版本迁移现有 MFC 应用程序，并且想要使用公共控件，IDE 不会自动提供清单信息来升级应用程序。 相反，您必须在预编译头文件中手动插入以下源代码：

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>另请参阅

[常规 MFC 主题](general-mfc-topics.md)<br/>
[层次结构图](hierarchy-chart.md)<br/>
[弃用的 ANSI API](deprecated-ansi-apis.md)
