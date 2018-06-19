---
title: 对话框类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.dialog
dev_langs:
- C++
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d33289d8025d7cdcaf4f6f69062230730b958c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351684"
---
# <a name="dialog-box-classes"></a>对话框类
类`CDialog`和及其派生的类封装对话框功能。 对话框中是一种特殊的窗口中，由于`CDialog`派生自`CWnd`。 派生对话框类从`CDialog`或使用其中一个标准对话框框中，例如打开或保存文件、 打印、 选择字体或颜色，通用对话框类的初始化搜索和替换操作中，或执行各种 OLE 相关操作。  
  
 [CDialog](../mfc/reference/cdialog-class.md)  
 所有对话框，模式和无模式的基类。  
  
 [CDataExchange](../mfc/reference/cdataexchange-class.md)  
 提供对话框数据交换和验证信息。  
  
## <a name="common-dialogs"></a>通用对话框  
 这些对话框类封装 Windows 公共对话框。 它们提供易于使用的复杂的对话框中的实现。  
  
 [CCommonDialog](../mfc/reference/ccommondialog-class.md)  
 所有通用对话框的基类。  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 提供的标准对话框打开或保存文件。  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 提供标准对话框中选择一种颜色。  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 提供标准对话框中选择一种字体。  
  
 [CFindReplaceDialog](../mfc/reference/cfindreplacedialog-class.md)  
 搜索和替换操作提供的标准对话框。  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 为打印文件中提供的标准对话框。  
  
 [CPrintDialogEx](../mfc/reference/cprintdialogex-class.md)  
 提供 Windows 打印属性表。  
  
 [CPageSetupDialog](../mfc/reference/cpagesetupdialog-class.md)  
 封装由 Windows 公共页面设置对话框提供的额外支持，以及对于设置和修改打印边距的服务。  
  
## <a name="ole-common-dialogs"></a>OLE 通用对话框  
 OLE 将几个通用对话框添加到 Windows。 这些类封装了 OLE 通用对话框。  
  
 [COleDialog](../mfc/reference/coledialog-class.md)  
 由框架使用，旨在包含所有 OLE 对话框的常见实现。 用户界面类别中的所有对话框类都派生自此基类。 `COleDialog` 无法直接使用。  
  
 [COleInsertDialog](../mfc/reference/coleinsertdialog-class.md)  
 显示“插入对象”对话框，即用于插入新的 OLE 链接项或嵌入项的标准用户界面。  
  
 [COlePasteSpecialDialog](../mfc/reference/colepastespecialdialog-class.md)  
 显示“选择性粘贴”对话框，即用于实现“编辑选择性粘贴”命令的标准用户界面。  
  
 [COleLinksDialog](../mfc/reference/colelinksdialog-class.md)  
 显示“编辑链接”对话框，即用于修改有关链接项的信息的标准用户界面。  
  
 [COleChangeIconDialog](../mfc/reference/colechangeicondialog-class.md)  
 显示“更改图标”对话框，即用于更改与 OLE 嵌入项或链接项关联的图标的标准用户界面。  
  
 [COleConvertDialog](../mfc/reference/coleconvertdialog-class.md)  
 显示“转换”对话框，即用于将 OLE 项从一种类型转换为另一种类型的标准用户界面。  
  
 [COlePropertiesDialog](../mfc/reference/colepropertiesdialog-class.md)  
 封装“Windows 公共 OLE 属性”对话框。 “公共 OLE 属性”对话框提供了一个简单方法，使您能够采用与 Windows 标准一致的方式来显示和修改 OLE 文档项的属性。  
  
 [COleUpdateDialog](../mfc/reference/coleupdatedialog-class.md)  
 显示“更新”对话框，即用于更新文档中的所有链接的标准用户界面。 对话框包含一个进度指示器，用来指示更新过程还有多久完成。  
  
 [COleChangeSourceDialog](../mfc/reference/colechangesourcedialog-class.md)  
 显示“更改源”对话框，即用于更改链接的目标或源的标准用户界面。  
  
 [COleBusyDialog](../mfc/reference/colebusydialog-class.md)  
 显示“服务器忙”和“服务器不响应”对话框，即用于处理对繁忙的应用程序的调用的标准用户界面。 通常会自动显示[COleMessageFilter](../mfc/reference/colemessagefilter-class.md)实现。  
  
## <a name="property-sheet-classes"></a>属性表类  
 属性表类允许你应用程序使用属性表，也称为选项卡式对话框。 属性表是一种高效的方式来组织大量的单个对话框中的控件。  
  
 [CPropertyPage](../mfc/reference/cpropertypage-class.md)  
 提供在属性表内的各个页面。 从派生类`CPropertyPage`为每个页后，可以添加到属性表。  
  
 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)  
 为多个属性页中提供的框架。 派生属性表类中的从`CPropertySheet`快速实现属性表。  
  
 [COlePropertyPage](../mfc/reference/colepropertypage-class.md)  
 显示图形界面（与对话框类似）中的 OLE 控件的属性。  
  
## <a name="html-based-dialog-classes"></a>基于 HTML 的对话框类  
 [CDHtmlDialog](../mfc/reference/cdhtmldialog-class.md)  
 用于创建实现自己的 HTML，而不是对话框资源的用户界面的对话框。  
  
 [CMultiPageDHtmlDialog](../mfc/reference/cmultipagedhtmldialog-class.md)  
 按顺序显示多个 HTML 页并处理每个页中的事件。  
  
## <a name="related-classes"></a>相关的类  
 这些类不是对话框本身，但它们使用对话框模板并且大部分的对话框行为。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 基于对话框模板控件条。  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 在对话框模板中定义其布局滚动视图。 从派生类`CFormView`可以实现基于对话框模板的用户界面。  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 提供了一种直接连接到数据访问对象 (DAO) 记录集对象的视图。 如所有窗体视图中，`CDaoRecordView`基于对话框模板。  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 提供了一种直接连接到开放式数据库连接 (ODBC) 记录集对象的视图。 如所有窗体视图中，`CRecordView`基于对话框模板。  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 包含有关打印或打印预览作业的信息的结构。 使用的打印体系结构[CView](../mfc/reference/cview-class.md)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

