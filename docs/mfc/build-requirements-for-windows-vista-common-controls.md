---
title: Windows Vista 公共控件的生成要求
ms.date: 11/04/2016
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: 1a2e79d91a41ea178eeb6f74ec7fa7b22588b277
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386247"
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Windows Vista 公共控件的生成要求

Microsoft 基础类 (MFC) 库支持 Windows 公共控件版本 6.1。 公共控件包含在 Windows Vista 中，库包含在 Visual Studio SDK。 库提供了增强现有类和新的类的新方法和支持 Windows Vista 公共控件的方法。 在生成应用程序时，应该遵循后续章节中所述的编译和迁移需求。

## <a name="compilation-requirements"></a>编译需求

### <a name="supported-versions"></a>支持的版本

一些新类和方法支持仅 Windows Vista 和更高版本，而其他方法还支持早期版本的操作系统。 请注意，在`Requirements`的每个方法主题部分指定当所需的最低操作系统是 Windows Vista。

即使您的计算机不会运行 Windows Vista，您可以生成将在 Windows Vista 运行，如果您有 6.1 版 MFC 标头文件在计算机上的 MFC 应用程序。 但是，专为 Windows Vista 设计的公共控件仅对该系统中，并忽略早期版本的操作系统。

### <a name="supported-character-sets"></a>支持的字符集

新 Windows 公共控件仅支持 Unicode 字符集，不支持 ANSI 字符集。 如果您在命令行中生成应用程序，请使用以下两个 define (/D) 编译器选项指定 Unicode 字符集作为基础字符集：

```
/D_UNICODE /DUNICODE
```

如果您生成应用程序在 Visual Studio 集成的开发环境 (IDE) 中，指定**Unicode 字符集**的选项**字符集**中的属性**常规**的项目属性的节点。

从 Windows 公共控件 6.1 版开始，某些 MFC 方法的 ANSI 版本已被弃用。 有关详细信息，请参阅[已弃用的 ANSI Api](../mfc/deprecated-ansi-apis.md)。

## <a name="migration-requirements"></a>迁移需求

如果您使用 Visual Studio IDE 生成使用 Windows 公共控件 6.1 版的新 MFC 应用程序，IDE 将自动声明适当的清单。 但是，如果您从早期版本的 Visual Studio 迁移到现有 MFC 应用程序，并且您要使用新的公共控件，IDE 不会自动提供用来升级应用程序清单信息。 相反，必须手动插入以下源代码中的您**stdafx.h**文件：

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

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)<br/>
[层次结构图](../mfc/hierarchy-chart.md)<br/>
[弃用的 ANSI API](../mfc/deprecated-ansi-apis.md)
