---
title: "MFC 宏和全局 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- MFC, global functions and variables
- MFC, macros
- global functions, MFC
- macros, MFC
- global functions
- global variables, MFC
- Afx naming convention
- macros
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d26b374e233326ac5acc97486edc8d38e6bf5d81
ms.openlocfilehash: 75db28c7be1ab497ba9656136d22b114b488c4ae
ms.lasthandoff: 02/24/2017

---
# <a name="mfc-macros-and-globals"></a>MFC 宏和全局函数
Microsoft 基础类库可以分为两个主要部分: （1） 的 MFC 类和 （2） 宏和全局。 如果函数或变量不是类的成员，则全局函数或变量。  
  
 MFC 库和活动模板库 (ATL) 共享字符串转换宏。 有关详细信息，请参阅[字符串转换宏](../../atl/reference/string-conversion-macros.md)ATL 文档中。  
  
 MFC 宏和全局函数提供了下列类别中的功能。  
  
## <a name="general-mfc"></a>常规 MFC  
  
-   [数据类型](../../mfc/reference/data-types-mfc.md)  
  
-   [MFC 类对象的类型强制转换](../../mfc/reference/type-casting-of-mfc-class-objects.md)  
  
-   [运行时对象模型服务](../../mfc/reference/run-time-object-model-services.md)  
  
-   [诊断服务](../../mfc/reference/diagnostic-services.md)  
  
-   [异常处理](../../mfc/reference/exception-processing.md)  
  
-   [CString 格式设置和消息框显示](../../mfc/reference/cstring-formatting-and-message-box-display.md)  
  
-   [消息映射](../../mfc/reference/message-map-macros-mfc.md)  
  
-   [应用程序信息和管理](../../mfc/reference/application-information-and-management.md)  
  
-   [标准命令和窗口 Id](../../mfc/reference/standard-command-and-window-ids.md)  
  
-   [集合类帮助器](../../mfc/reference/collection-class-helpers.md)  
  
-   [灰色和抖色位图函数](../../mfc/reference/gray-and-dithered-bitmap-functions.md)  
  
-   [标准对话框数据交换 (DDX) 例程](../../mfc/reference/standard-dialog-data-exchange-routines.md)  
  
-   [标准对话框数据验证 (DDV) 例程](../../mfc/reference/standard-dialog-data-validation-routines.md)  
  
-   [AFX 消息](../../mfc/reference/afx-messages.md)  
  
-   [工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)  
  
-   [Cmfcimagepaintarea:: Image_edit_mode 枚举](cmfcimagepaintarea-image-edit-mode-enumeration.md)  

  
## <a name="database"></a>数据库  
  
-   [记录字段交换 (RFX) 函数](../../mfc/reference/record-field-exchange-functions.md)和[批量记录字段交换 (bulk RFX) 函数](../../mfc/reference/record-field-exchange-functions.md)MFC ODBC 类  
  
-   [记录字段交换 (DFX) 函数](../../mfc/reference/record-field-exchange-functions.md)MFC DAO 类  
  
-   [CRecordView 和 CDaoRecordView 的对话框数据交换 (DDX) 函数](../../mfc/reference/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)（MFC ODBC 和 DAO 类）  
  
-   [OLE 控件的对话框数据交换 (DDX) 函数](../../mfc/reference/dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [宏和全局函数来帮助进行直接调用开放式数据库连接 (ODBC) API 函数](../../mfc/reference/database-macros-and-globals.md)  
  
-   [DAO 数据库引擎初始化和终止](../../mfc/reference/dao-database-engine-initialization-and-termination.md)  
  
## <a name="internet"></a>Internet  
  
-   [Internet URL 分析全局函数](../../mfc/reference/internet-url-parsing-globals.md)  
  
## <a name="dhtml--dhtml-event-maps"></a>DHTML / DHTML 事件映射  
  
-   [DHTML 对话框数据交换 (DDX) 帮助器宏](../../mfc/reference/ddx-dhtml-helper-macros.md)  
  
-   [DHTML 事件映射](../../mfc/reference/dhtml-event-maps.md)  
  
## <a name="ole"></a>OLE  
  
-   [OLE 初始化](../../mfc/reference/ole-initialization.md)  
  
-   [应用程序控件](../../mfc/reference/application-control.md)  
  
-   [调度映射](../../mfc/reference/dispatch-maps.md)  
  
 此外，MFC 提供了一个名为函数[AfxEnableControlContainer](http://msdn.microsoft.com/library/7aa0b9d2-5329-4bc3-9d41-856e30fe2c2b)启用使用 MFC 4.0，若要完全支持开发的任何 OLE 容器嵌入 OLE 控件。  
  
## <a name="ole-controls"></a>OLE 控件  
  
-   [变量参数类型常量](../../mfc/reference/variant-parameter-type-constants.md)  
  
-   [类型库访问](../../mfc/reference/type-library-access.md)  
  
-   [属性页](../../mfc/reference/property-pages-mfc.md)  
  
-   [事件映射](../../mfc/reference/event-maps.md)  
  
-   [事件接收器映射](../../mfc/reference/event-sink-maps.md)  
  
-   [连接映射](../../mfc/reference/connection-maps.md)  
  
-   [注册 OLE 控件](../../mfc/reference/registering-ole-controls.md)  
  
-   [类工厂和许可](../../mfc/reference/class-factories-and-licensing.md)  
  
-   [OLE 控件的持久性](../../mfc/reference/persistence-of-ole-controls.md)  
  
 本部分的第一部分简要介绍了每一个先前的类别并列出的全局函数和宏的位置中的类别，以及功能的简短说明。 以下是全局函数、 全局变量和宏 MFC 库中的说明。  
  
> [!NOTE]
>  许多全局函数以前缀"Afx"开头，但某些，例如，对话框数据交换 (DDX) 函数和许多数据库的功能，请遵循此约定。 所有全局变量的"afx"开头，作为前缀。 宏不以任何特殊前缀开头，但它们以大写首字母。  
  
## <a name="see-also"></a>另请参阅  
 [类概述](../../mfc/class-library-overview.md)




