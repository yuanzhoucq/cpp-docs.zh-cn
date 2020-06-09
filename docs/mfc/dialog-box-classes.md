---
title: 对话框类
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 2399b27fc081dcc810277079729b0e62ef80d603
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616938"
---
# <a name="dialog-box-classes"></a>对话框类

类 `CDialog` 及其派生类封装了对话框功能。 因为对话框是一种特殊的窗口，所以 `CDialog` 派生自 `CWnd` 。 从派生对话框类 `CDialog` ，或使用标准对话框的一个通用对话框，例如打开或保存文件、打印、选择字体或颜色、启动搜索和替换操作或执行各种与 OLE 相关的操作。

[CDialog](reference/cdialog-class.md)<br/>
所有对话框的基类，均为模式和无模式。

[CDataExchange](reference/cdataexchange-class.md)<br/>
为对话框提供数据交换和验证信息。

## <a name="common-dialogs"></a>通用对话框

这些对话框类封装 Windows 公共对话框。 它们提供了易于使用的复杂对话框实现。

[CCommonDialog](reference/ccommondialog-class.md)<br/>
所有常见对话框的基类。

[CFileDialog](reference/cfiledialog-class.md)<br/>
提供用于打开或保存文件的标准对话框。

[CColorDialog](reference/ccolordialog-class.md)<br/>
提供用于选择颜色的标准对话框。

[CFontDialog](reference/cfontdialog-class.md)<br/>
提供用于选择字体的标准对话框。

[CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
为搜索和替换操作提供标准对话框。

[CPrintDialog](reference/cprintdialog-class.md)<br/>
提供用于打印文件的标准对话框。

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
提供 Windows 打印属性表。

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
封装由 "Windows 公共页面设置" 对话框提供的服务以及对设置和修改打印边距的额外支持。

## <a name="ole-common-dialogs"></a>OLE 通用对话框

OLE 将几个常见对话框添加到 Windows。 这些类封装了 OLE 通用对话框。

[COleDialog](reference/coledialog-class.md)<br/>
由框架使用，旨在包含所有 OLE 对话框的常见实现。 用户界面类别中的所有对话框类都派生自此基类。 `COleDialog` 无法直接使用。

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
显示“插入对象”对话框，即用于插入新的 OLE 链接项或嵌入项的标准用户界面。

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
显示“选择性粘贴”对话框，即用于实现“编辑选择性粘贴”命令的标准用户界面。

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
显示“编辑链接”对话框，即用于修改有关链接项的信息的标准用户界面。

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
显示“更改图标”对话框，即用于更改与 OLE 嵌入项或链接项关联的图标的标准用户界面。

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
显示“转换”对话框，即用于将 OLE 项从一种类型转换为另一种类型的标准用户界面。

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
封装“Windows 公共 OLE 属性”对话框。 “公共 OLE 属性”对话框提供了一个简单方法，使您能够采用与 Windows 标准一致的方式来显示和修改 OLE 文档项的属性。

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
显示“更新”对话框，即用于更新文档中的所有链接的标准用户界面。 对话框包含一个进度指示器，用来指示更新过程还有多久完成。

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
显示“更改源”对话框，即用于更改链接的目标或源的标准用户界面。

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
显示“服务器忙”和“服务器不响应”对话框，即用于处理对繁忙的应用程序的调用的标准用户界面。 通常由[COleMessageFilter](reference/colemessagefilter-class.md)实现自动显示。

## <a name="property-sheet-classes"></a>属性表类

属性表类允许你的应用程序使用属性表，也称为选项卡式对话框。 属性表是在单个对话框中组织大量控件的有效方法。

[CPropertyPage](reference/cpropertypage-class.md)<br/>
提供属性表中的各个页面。 从中派生一个类，以便 `CPropertyPage` 添加到属性表中的每一页。

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
为多个属性页提供框架。 从派生属性表类 `CPropertySheet` ，以快速实现属性表。

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
显示图形界面（与对话框类似）中的 OLE 控件的属性。

## <a name="html-based-dialog-classes"></a>基于 HTML 的对话框类

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
用于创建使用 HTML 而非对话框资源实现其用户界面的对话框。

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
按顺序显示多个 HTML 页并处理每页中的事件。

## <a name="related-classes"></a>相关类

这些类不是每个 se 都具有的对话框，但使用的是对话框模板，并且有许多对话框行为。

[CDialogBar](reference/cdialogbar-class.md)<br/>
基于对话框模板的控件条。

[CFormView](reference/cformview-class.md)<br/>
其布局在对话框模板中定义的滚动视图。 从派生一个类 `CFormView` ，以实现基于对话框模板的用户界面。

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
提供直接连接到数据访问对象（DAO）记录集对象的窗体视图。 与所有窗体视图一样， `CDaoRecordView` 是基于对话框模板的。

[CRecordView](reference/crecordview-class.md)<br/>
提供直接连接到开放式数据库连接（ODBC）记录集对象的窗体视图。 与所有窗体视图一样， `CRecordView` 是基于对话框模板的。

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
包含打印或打印预览作业相关信息的结构。 由[CView](reference/cview-class.md)打印体系结构使用。

## <a name="see-also"></a>另请参阅

[类概述](class-library-overview.md)
