---
title: 类库概述
ms.date: 09/17/2019
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
ms.openlocfilehash: bf30f1b0aa83ef002337b76601f04c7103963441
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620745"
---
# <a name="class-library-overview"></a>类库概述

此概述分类并描述 Microsoft 基础类库（MFC）版本9.0 中的类。 MFC 中的类共同构成应用程序框架-应用程序框架是为 Windows API 编写的应用程序框架。 编程任务是在特定于应用程序的代码中进行填充。

库的类在以下类别中提供：

- [根类：CObject](root-class-cobject.md)

- [MFC 应用程序体系结构类](mfc-application-architecture-classes.md)

  - [应用程序和线程支持类](application-and-thread-support-classes.md)

  - [命令路由类](command-routing-classes.md)

  - [文档类](document-classes.md)

  - [视图类（体系结构）](view-classes-architecture.md)

  - [框架窗口类（体系结构）](frame-window-classes-architecture.md)

  - [文档模板类](document-template-classes.md)

- [窗口、对话框和控件类](window-dialog-and-control-classes.md)

  - [框架窗口类（Windows）](frame-window-classes-windows.md)

  - [视图类（Windows）](view-classes-windows.md)

  - [对话框类](dialog-box-classes.md)

  - [控件类](control-classes.md)

  - [控件条类](control-bar-classes.md)

- [绘制和打印类](drawing-and-printing-classes.md)

  - [输出（设备上下文）类](output-device-context-classes.md)

  - [绘图工具类](drawing-tool-classes.md)

- [简单数据类型类](simple-data-type-classes.md)

- [数组、列表和映射类](array-list-and-map-classes.md)

  - [数组、列表和映射的模板类](template-classes-for-arrays-lists-and-maps.md)

  - [随时可用的数组类](ready-to-use-array-classes.md)

  - [随时可用的列表类](ready-to-use-list-classes.md)

  - [随时可用的映射类](ready-to-use-map-classes.md)

- [文件和数据库类](file-and-database-classes.md)

  - [文件 i/o 类](file-i-o-classes.md)

  - [DAO 类](dao-classes.md)

  - [ODBC 类](odbc-classes.md)

  - [OLE DB 类](ole-db-classes.md)

- [Internet 和网络类](internet-and-networking-classes.md)

  - [Windows 套接字类](windows-sockets-classes.md)

  - [Win32 Internet 类](win32-internet-classes.md)

- [OLE 类](ole-classes.md)

  - [OLE 容器类](ole-container-classes.md)

  - [OLE 服务器类](ole-server-classes.md)

  - [OLE 拖放和数据传输类](ole-drag-and-drop-and-data-transfer-classes.md)

  - [OLE 通用对话框类](ole-common-dialog-classes.md)

  - [OLE 自动化类](ole-automation-classes.md)

  - [OLE 控件类](ole-control-classes.md)

  - [活动文档类](active-document-classes.md)

  - [OLE 相关类](ole-related-classes.md)

- [调试和异常类](debugging-and-exception-classes.md)

  - [调试支持类](debugging-support-classes.md)

  - [异常类](exception-classes.md)

"[常规类设计](general-class-design-philosophy.md)" 一节介绍了 MFC 库的设计方式。

有关框架的概述，请参阅[使用类编写适用于 Windows 的应用程序](using-the-classes-to-write-applications-for-windows.md)。 上面列出的某些类是通用类，可在框架外使用，并提供有用的抽象，如集合、异常、文件和字符串。

若要查看类的继承，请使用[类层次结构图](hierarchy-chart.md)。

除了本概述中列出的类之外，MFC 库还包含许多全局函数、全局变量和宏。 主题[Mfc Macros 和 Globals](reference/mfc-macros-and-globals.md)中提供了这些方法的概述和详细列表，它们遵循对 mfc 类的字母引用。

## <a name="see-also"></a>另请参阅

[MFC 桌面应用程序](mfc-desktop-applications.md)
