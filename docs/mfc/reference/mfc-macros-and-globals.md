---
title: MFC 宏和全局函数
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions [MFC]
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
ms.openlocfilehash: ed45fc7014bda18887be6dc8fbcdff8ba9a9c5f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373046"
---
# <a name="mfc-macros-and-globals"></a>MFC 宏和全局函数

Microsoft 基础类库可以分为两个主要部分：（1） MFC 类和 （2） 宏和全局。 如果函数或变量不是类的成员，则它是全局函数或变量。

MFC 库和活动模板库 （ATL） 共享字符串转换宏。 有关详细信息，请参阅 ATL 文档中的[字符串转换宏](../../atl/reference/string-conversion-macros.md)。

MFC 宏和全局提供以下类别的功能。

## <a name="general-mfc"></a>一般MFC

- [数据类型](data-types-mfc.md)

- [MFC 类对象的类型强制转换](type-casting-of-mfc-class-objects.md)

- [运行时对象模型服务](run-time-object-model-services.md)

- [诊断服务](diagnostic-services.md)

- [异常处理](exception-processing.md)

- [CString 格式和消息框显示](cstring-formatting-and-message-box-display.md)

- [消息映射](message-map-macros-mfc.md)

- [委托和接口映射](delegate-and-interface-maps.md)

- [模块和 DLL](extension-dll-macros.md)

- [应用程序信息和管理](application-information-and-management.md)

- [标准命令和窗口指示](standard-command-and-window-ids.md)

- [集合类帮助器](collection-class-helpers.md)

- [灰色和抖色位图函数](gray-and-dithered-bitmap-functions.md)

- [标准对话框数据交换 （DDX） 例程](standard-dialog-data-exchange-routines.md)

- [标准对话框数据验证 （DDV） 例程](standard-dialog-data-validation-routines.md)

- [AFX 消息](afx-messages.md)

- [工具栏控件样式](toolbar-control-styles.md)

- [CMFC图像绘制区域：：IMAGE_EDIT_MODE枚举](cmfcimagepaintarea-image-edit-mode-enumeration.md)

## <a name="database"></a>数据库

- MFC ODBC 类[的记录现场交换 （RFX） 功能](record-field-exchange-functions.md)和[批量记录现场交换 （批量 RFX） 功能](record-field-exchange-functions.md)

- MFC DAO 类[的记录字段交换 （DFX） 函数](record-field-exchange-functions.md)

- CRecordView 和 CDaoRecordView（MFC ODBC 和 DAO 类[）的对话数据交换 （DDX） 功能](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)

- [用于 OLE 控件的对话数据交换 （DDX） 函数](dialog-data-exchange-functions-for-ole-controls.md)

- [宏和全局，以帮助直接调用开放数据库连接 （ODBC） API 功能](database-macros-and-globals.md)

- [DAO 数据库引擎初始化和终止](dao-database-engine-initialization-and-termination.md)

## <a name="internet"></a>Internet

- [互联网 URL 解析全局](internet-url-parsing-globals.md)

## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML 事件映射

- [DHTML 对话框数据交换 （DDX） 帮助器宏](ddx-dhtml-helper-macros.md)

- [DHTML 事件映射](dhtml-event-maps.md)

## <a name="ole"></a>OLE

- [OLE 初始化](ole-initialization.md)

- [应用程序控制](application-control.md)

- [调度地图](dispatch-maps.md)

此外，MFC 还提供名为[AfxEnableControl 容器](ole-initialization.md#afxenablecontrolcontainer)的功能，使使用 MFC 4.0 开发的任何 OLE 容器能够完全支持嵌入式 OLE 控制。

## <a name="ole-controls"></a>OLE 控制

- [变量参数类型常量](variant-parameter-type-constants.md)

- [类型库访问](type-library-access.md)

- [属性页](property-pages-mfc.md)

- [事件地图](event-maps.md)

- [事件接收器映射](event-sink-maps.md)

- [连接映射](connection-maps.md)

- [注册 OLE 控件](registering-ole-controls.md)

- [类工厂和许可](class-factories-and-licensing.md)

- [OLE 控件的持久性](persistence-of-ole-controls.md)

本节的第一部分简要讨论了前面的每个类别，并列出了类别中的全局和宏，以及功能的简要说明。 以下是 MFC 库中全局函数、全局变量和宏的说明。

> [!NOTE]
> 许多全局函数以前缀"Afx"开头，但有些，例如，对话框数据交换 （DDX） 函数和许多数据库函数，不遵循此约定。 所有全局变量都以"afx"作为前缀开头。 宏不以任何特定前缀开头，但它们用大写字母编写。

## <a name="see-also"></a>另请参阅

[类概述](../../mfc/class-library-overview.md)
