---
title: MFC 桌面应用程序
ms.date: 07/28/2019
f1_keywords:
- MFC
helpviewer_keywords:
- libraries, MFC
- class libraries, MFC
- MFC, about MFC
ms.assetid: 7101cb18-a681-495c-8f2b-069ad20c72f7
ms.openlocfilehash: d26cf1e92717d2925edf3730e1ae4ec935365321
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178452"
---
# <a name="mfc-desktop-applications"></a>MFC 桌面应用程序

Microsoft 基础类 (MFC) 库针对大部分 Win32 和 COM API 提供面向对象的包装器。 虽然此包装器可用于创建极为简单的桌面应用程序，但当你需要开发具有多个控件的更复杂的用户界面时，此包装器将最为有用。 可以使用 MFC 创建带有 Office 样式用户界面的应用程序。 有关 Windows 平台本身的文档，请参阅[windows 文档](/windows/index)。 有关在C++不使用 MFC 的情况下生成 windows 应用程序的信息，请参阅[使用 Win32 API 生成桌面 Windows 应用](/windows/win32/index)。

“MFC 参考”介绍了构成 Microsoft 基础类库的类、全局函数、全局变量和宏。

每个类包含的各个层次结构图表在定位基类时很有用。 “MFC 参考”通常不说明继承的成员函数或继承的运算符。 有关这些函数的信息，请参见层次结构关系图中描述的基类。

有关每个类的文档包括类概述、成员摘要（按类别）以及有关成员函数、重载运算符和数据成员的主题。

仅记录通常用于应用程序或派生类的公共类成员和受保护类成员。 有关类成员的完整列表，请参见类头文件。

> [!IMPORTANT]
>  MFC 类及其成员不能在 Windows 运行时环境中执行的应用程序中使用。
>
>  用于多字节字符编码 (MBCS) 的 MFC 库 (DLL) 不再包含于 Visual Studio 中，但可用作 Visual Studio 加载项。 有关详细信息，请参阅[MFC MBCS DLL 加载项](mfc-mbcs-dll-add-on.md)。

## <a name="in-this-section"></a>本节内容

[概念](mfc-concepts.md)<br/>
有关 MFC 主题的概念文章。

[层次结构图](hierarchy-chart.md)<br/>
形象说明类库中的类关系。

[类概述](class-library-overview.md)<br/>
按类别列出 MFC 库中的类。

[演练](walkthroughs-mfc.md)<br/>
包含带领你完成与 MFC 库功能关联的各种任务的文章。

[技术说明](mfc-technical-notes.md)<br/>
提供 MFC 开发团队针对类库编写的专门主题的链接。

[MFC 自定义](customization-for-mfc.md)<br/>
提供有关自定义 MFC 应用程序的一些提示。

[类](reference/mfc-classes.md)<br/>
提供 MFC 类的链接和有关 MFC 类的头文件信息。

[Internal 类](reference/internal-classes.md)<br/>
MFC 内部使用。 为了保持完整性，本节将说明这些内部类，但这些内部类不在代码中直接使用。

[宏和全局](reference/mfc-macros-and-globals.md)<br/>
提供 MFC 库中的宏和全局函数的链接。

[结构、样式、回调和消息映射](reference/structures-styles-callbacks-and-message-maps.md)<br/>
提供 MFC 库所使用的结构、样式、回调和消息映射的链接。

[MFC 向导和对话框](reference/mfc-wizards-and-dialog-boxes.md)<br/>
Visual Studio 中用于创建 MFC 应用程序的功能的指南。

[使用资源文件](../windows/working-with-resource-files.md)<br/>
如何使用资源文件管理静态用户界面数据，如 UI 字符串和对话框布局。

## <a name="related-sections"></a>相关章节

[层次结构图类别](hierarchy-chart-categories.md)<br/>
按类别说明 MFC 层次结构图表。

[ATL/MFC 共享类](../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
提供 MFC 与 ATL 共享的类的链接。

[MFC 示例](../overview/visual-cpp-samples.md#mfc-samples)<br/>
提供演示如何使用 MFC 的示例的链接。

[Visual C++ 库参考](../standard-library/cpp-standard-library-reference.md)<br/>
提供 Visual C++ 附带的各种库链接，其中包括 ATL、MFC、OLE DB 模板、C 运行时库和 C++ 标准库。

[在 Visual Studio 中进行调试](/visualstudio/debugger/debugging-in-visual-studio)<br/>
提供一些链接，所涉及内容为使用 Visual Studio 调试器纠正应用程序或存储过程中的逻辑错误。

## <a name="see-also"></a>另请参阅

[MFC 和 ATL](mfc-and-atl.md)
