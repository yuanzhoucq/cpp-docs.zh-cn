---
title: "MFC 宏和全局函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Afx 命名约定"
  - "全局函数"
  - "全局函数, MFC"
  - "全局变量, MFC"
  - "宏"
  - "宏, MFC"
  - "MFC, 全局函数和变量"
  - "MFC, 宏"
ms.assetid: add4e33f-0e62-4d27-be14-896cb8675d22
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 宏和全局函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基于基础选件类库可分为两个主要部分：\(1\) MFC 选件类和 \(2\) 宏和全局变量。  如果函数或变量不是选件类的成员，则它是全局函数或变量。  
  
 MFC 库和活动模板库 \(ATL\) 共享字符串翻译宏。  有关更多信息，请参见 ATL 文档中的[String Conversion Macros](../../atl/reference/string-conversion-macros.md)。  
  
 MFC 宏和 globals 提供了以下类别的功能。  
  
## 常规 MFC  
  
-   [数据类型](../../mfc/reference/data-types-mfc.md)  
  
-   [MFC 类对象的类型强制转换](../../mfc/reference/type-casting-of-mfc-class-objects.md)  
  
-   [运行时对象模型服务](../../mfc/reference/run-time-object-model-services.md)  
  
-   [诊断服务](../../mfc/reference/diagnostic-services.md)  
  
-   [异常处理](../../mfc/reference/exception-processing.md)  
  
-   [CString 格式设置和消息框显示](../../mfc/reference/cstring-formatting-and-message-box-display.md)  
  
-   [消息映射](../../mfc/reference/message-map-macros-mfc.md)  
  
-   [应用程序信息和管理](../../mfc/reference/application-information-and-management.md)  
  
-   [标准命令和窗口 ID](../../mfc/reference/standard-command-and-window-ids.md)  
  
-   [集合类帮助器](../../mfc/reference/collection-class-helpers.md)  
  
-   [灰色和抖色位图函数](../../mfc/reference/gray-and-dithered-bitmap-functions.md)  
  
-   [标准对话框数据交换（DDX）常式](../../mfc/reference/standard-dialog-data-exchange-routines.md)  
  
-   [标准对话框数据验证（DDV）例程](../../mfc/reference/standard-dialog-data-validation-routines.md)  
  
-   [AFX 消息](../../mfc/reference/afx-messages.md)  
  
-   [工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)  
  
-   [CMFCImagePaintArea::IMAGE\_EDIT\_MODE 枚举](../../mfc/reference/cmfcimagepaintarea-image-edit-mode-enumeration.md)  
  
## 数据库  
  
-   MFC ODBC类[Record Field Exchange \(RFX\) 函数](../../mfc/reference/record-field-exchange-functions.md) 和 [Bulk Record Field Exchange \(bulk RFX\) 函数](../../mfc/reference/record-field-exchange-functions.md)  
  
-   [Record field exchange \(DFX\) functions](../../mfc/reference/record-field-exchange-functions.md)的MFC DAO类  
  
-   [Dialog data exchange \(DDX\)函数为CRecordView的和CDaoRecordView](../../mfc/reference/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md)（MFC ODBC和DAO类）  
  
-   [对于OLE控件对话框数据交换（DDX）函数](../../mfc/reference/dialog-data-exchange-functions-for-ole-controls.md)  
  
-   [宏和全局性为帮助在调用开放式数据库连接 \(odbc\) API 直接函数](../../mfc/reference/database-macros-and-globals.md)  
  
-   [DAO 数据库引擎初始化和终止](../../mfc/reference/dao-database-engine-initialization-and-termination.md)  
  
## Internet  
  
-   [Internet URL 分析全局函数](../../mfc/reference/internet-url-parsing-globals.md)  
  
## DHTML\/DHTML 事件映射  
  
-   [DHTML 对话框数据交换 \(ddx\)帮助程序宏](../../mfc/reference/ddx-dhtml-helper-macros.md)  
  
-   [DHTML 事件映射](../../mfc/reference/dhtml-event-maps.md)  
  
## OLE  
  
-   [OLE 初始化](../../mfc/reference/ole-initialization.md)  
  
-   [应用程序控件](../../mfc/reference/application-control.md)  
  
-   [调度映射](../../mfc/reference/dispatch-maps.md)  
  
 此外，MFC提供了一个名为[AfxEnableControlContainer](../Topic/AfxEnableControlContainer.md)，使任何OLE容器使用MFC 4.0完全支持嵌入式OLE控件开发。  
  
## OLE 控件  
  
-   [变量参数类型常量](../../mfc/reference/variant-parameter-type-constants.md)  
  
-   [类型库访问](../../mfc/reference/type-library-access.md)  
  
-   [属性页](../../mfc/reference/property-pages-mfc.md)  
  
-   [事件映射](../../mfc/reference/event-maps.md)  
  
-   [事件接收器映射](../../mfc/reference/event-sink-maps.md)  
  
-   [连接映射](../../mfc/reference/connection-maps.md)  
  
-   [注册 OLE 控件](../../mfc/reference/registering-ole-controls.md)  
  
-   [类工厂和许可](../../mfc/reference/class-factories-and-licensing.md)  
  
-   [OLE 控件的持久性](../../mfc/reference/persistence-of-ole-controls.md)  
  
 本节的第一部分简要探讨了每一个类并使用功能的简要说明来列出 globals 和宏在类别中。  在这后面是MFC库中全局函数、全局变量和宏的声明。  
  
> [!NOTE]
>  许多全局函数以前缀“Afx”开头但某些不是这样的，例如，某些对话框数据交换 \(DDX\) 功能和许多数据库功能，则不遵循此约定。  所有全局变量从“afx”开头为前缀。  宏不以任何特殊前缀开头，但是，它们用大写字母编写。  
  
## 请参阅  
 [类概述](../../mfc/class-library-overview.md)