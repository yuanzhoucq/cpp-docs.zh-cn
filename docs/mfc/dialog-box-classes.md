---
title: "对话框类 | Microsoft Docs"
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
  - "vc.classes.dialog"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用对话框类"
  - "对话框类"
  - "OLE 通用对话框类"
  - "属性表类"
  - "选项卡对话框"
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 对话框类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CDialog` 类及其派生类封装对话框功能。  因为对话框是特定窗口，`CDialog` 派生自 `CWnd`。  从 `CDialog` 类派生对话框或提供标准对话框使用的通用对话框类，例如打开或保存文件，打印，选择字体或颜色，开始搜索和替换操作或执行多种 OLE 关联的操作。  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 所有对话框的基类，控件模式和无模式。  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 提供的对话框数据交换和验证信息。  
  
## 通用对话框  
 这些对话框类封装 Windows 通用对话框"  这些提供复杂对话框的易于使用的实现。  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 所有通用对话框的基类。  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 用于打开或保存文件提供标准对话框。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 用于选择颜色提供标准对话框。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 为选择字体提供标准对话框。  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 搜索和替换操作提供标准对话框。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 打印文件为提供标准对话框。  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 提供了 Windows 2000 的属性表。  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 封装 Windows 公用页设置对话框中提供的其他服务支持设置和修改边距的打印。  
  
## OLE 通用对话框  
 OLE 添加几个通用对话框的窗口。  这些类封装 OLE 通用对话框"  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 用于 OLE 对话框由框架包含所有常见的实现。  以用户界面类的所有对话框类从该基类派生。  无法直接使用`COleDialog`。  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 查看插入对话框，插入的新链接的或嵌入的 OLE 项标准的用户界面。  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 将显示特殊的编辑粘贴命令，对话框实现特定标准的用户界面。  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 显示编辑链接标准对话框，用户接口有关链接的更改的信息。  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 显示更改图标对话框中，更改的标准图标用户界面与 OLE 嵌入式或链接的项。  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 显示对话框转换，转换的标准 OLE 项用户界面从一个类型到另一个。  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 封装 Windows 常用 OLE 属性对话框。  通用 OLE 属性对话框提供一种简便方法来显示和修改一个 OLE 文档项的一些属性与 Windows 标准。  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 显示更新对话框，更新所有链接的标准的用户界面在文档。  对话框包含一个进度指示器输出指示关闭进程与完成。  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 显示源更改对话框，将链接的目标或源标准的用户界面。  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 显示不响应服务器忙碌和的服务器对话框，处理的调用标准的用户界面为正忙应用程序。  通常自动显示已被 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md) 实现。  
  
## 属性表类  
 属性表类允许应用程序使用属性表，也称为选项卡式对话框。  属性表是一个有效方法组织在一个对话框中大量控件。  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 提供在属性表中的单个页。  从每页的 `CPropertyPage` 派生的类中添加一个属性表。  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 对于多个属性页提供框架。  从 `CPropertySheet` 派生类属性表快速实现属性表。  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 显示一个 OLE 控件的属性了一个图形界面的，类似于对话框。  
  
## 基于 HTML 的对话框类  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 用于创建实现它们与 HTML 的用户界面而不是对话框的对话框资源。  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 显示多个行句柄从 HTML 页和每页的事件。  
  
## 相关类  
 这些类也不是其本身而言对话框，但是，它们使用对话框模板并有许多对话框行为。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 基于对话框模板的控件条。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 布局是在对话框模板定义的滚动视图。  从 `CFormView` 派生的类来实现基于对话框模板的用户界面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供直接连接的一个窗体向视图数据访问对象 \(DAO\) \(DAO\) 记录集对象。  同所有窗体视图中，`CDaoRecordView` 基于对话框模板。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供直接连接的一个窗体向视图开放式数据库连接 \(ODBC\) 记录集对象。  同所有窗体视图中，`CRecordView` 基于对话框模板。  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 包含有关打印或打印预览作业的结构信息。  使用 [CView](../mfc/reference/cview-class.md)体系结构由打印。  
  
## 请参阅  
 [类概述](../mfc/class-library-overview.md)