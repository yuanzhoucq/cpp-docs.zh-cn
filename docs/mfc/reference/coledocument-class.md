---
title: COleDocument 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocument
- AFXOLE/COleDocument
- AFXOLE/COleDocument::COleDocument
- AFXOLE/COleDocument::AddItem
- AFXOLE/COleDocument::ApplyPrintDevice
- AFXOLE/COleDocument::EnableCompoundFile
- AFXOLE/COleDocument::GetInPlaceActiveItem
- AFXOLE/COleDocument::GetNextClientItem
- AFXOLE/COleDocument::GetNextItem
- AFXOLE/COleDocument::GetNextServerItem
- AFXOLE/COleDocument::GetPrimarySelectedItem
- AFXOLE/COleDocument::GetStartPosition
- AFXOLE/COleDocument::HasBlankItems
- AFXOLE/COleDocument::OnShowViews
- AFXOLE/COleDocument::RemoveItem
- AFXOLE/COleDocument::UpdateModifiedFlag
- AFXOLE/COleDocument::OnEditChangeIcon
- AFXOLE/COleDocument::OnEditConvert
- AFXOLE/COleDocument::OnEditLinks
- AFXOLE/COleDocument::OnFileSendMail
- AFXOLE/COleDocument::OnUpdateEditChangeIcon
- AFXOLE/COleDocument::OnUpdateEditLinksMenu
- AFXOLE/COleDocument::OnUpdateObjectVerbMenu
- AFXOLE/COleDocument::OnUpdatePasteLinkMenu
- AFXOLE/COleDocument::OnUpdatePasteMenu
dev_langs:
- C++
helpviewer_keywords:
- COleDocument [MFC], COleDocument
- COleDocument [MFC], AddItem
- COleDocument [MFC], ApplyPrintDevice
- COleDocument [MFC], EnableCompoundFile
- COleDocument [MFC], GetInPlaceActiveItem
- COleDocument [MFC], GetNextClientItem
- COleDocument [MFC], GetNextItem
- COleDocument [MFC], GetNextServerItem
- COleDocument [MFC], GetPrimarySelectedItem
- COleDocument [MFC], GetStartPosition
- COleDocument [MFC], HasBlankItems
- COleDocument [MFC], OnShowViews
- COleDocument [MFC], RemoveItem
- COleDocument [MFC], UpdateModifiedFlag
- COleDocument [MFC], OnEditChangeIcon
- COleDocument [MFC], OnEditConvert
- COleDocument [MFC], OnEditLinks
- COleDocument [MFC], OnFileSendMail
- COleDocument [MFC], OnUpdateEditChangeIcon
- COleDocument [MFC], OnUpdateEditLinksMenu
- COleDocument [MFC], OnUpdateObjectVerbMenu
- COleDocument [MFC], OnUpdatePasteLinkMenu
- COleDocument [MFC], OnUpdatePasteMenu
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6317d7c14f76355df908c9809df633533df3fb61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="coledocument-class"></a>COleDocument 类
支持可视编辑的 OLE 文档的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|构造 `COleDocument` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|将项添加到保留在文档中的项的列表。|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|在文档中设置用于所有客户端项的打印目标设备。|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|导致要存储使用 OLE 结构化存储文件格式的文档。|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|返回是当前处于就地活动状态的 OLE 项。|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|获取循环的下一步的客户端项目。|  
|[COleDocument::GetNextItem](#getnextitem)|获取循环的下一步的文档项。|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|获取循环的下一步的服务器项目。|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|返回文档中的主选定的 OLE 项。|  
|[COleDocument::GetStartPosition](#getstartposition)|获取开始迭代的初始位置。|  
|[COleDocument::HasBlankItems](#hasblankitems)|检查文档中的空白项目。|  
|[COleDocument::OnShowViews](#onshowviews)|调用文档时，可见或不可见。|  
|[COleDocument::RemoveItem](#removeitem)|从保留的文档的项列表中移除一个项。|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|将文档标记为已修改如果修改了任何包含的 OLE 项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|处理中的更改图标菜单命令的事件。|  
|[COleDocument::OnEditConvert](#oneditconvert)|处理从一种类型到另一个嵌入或链接的对象的转换。|  
|[COleDocument::OnEditLinks](#oneditlinks)|处理编辑菜单上的链接命令中的事件。|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|将一封电子邮件发送与附加的文档。|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|由框架调用以更新命令 UI 的编辑/更改图标菜单选项。|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|由框架调用以更新命令 UI 编辑/链接菜单选项。|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|由框架用于编辑的更新命令 UI 调用 / *ObjectName*菜单选项，然后从编辑访问的谓词子菜单 / *ObjectName*。|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|由框架调用以更新命令 UI 的选择性粘贴菜单选项。|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|由框架调用以更新命令 UI 粘贴菜单选项。|  
  
## <a name="remarks"></a>备注  
 `COleDocument` 派生自**CDocument**，这样，OLE 应用程序，可使用由 Microsoft 基础类库提供的文档/视图体系结构。  
  
 `COleDocument` 将文档的集合视为[CDocItem](../../mfc/reference/cdocitem-class.md)对象以处理 OLE 项。 容器和服务器应用程序需要这种体系结构，因为其文档必须能够包含 OLE 项。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)类都派生自`CDocItem`，管理应用程序和 OLE 项之间的交互。  
  
 如果你正在编写简单的容器应用程序，派生您的文档类从`COleDocument`。 如果你正在编写的容器应用程序支持将链接到其文档中包含的嵌入项，派生您的文档类从[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)。 如果你正在编写服务器应用程序或组合容器/服务器，派生您的文档类从[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)。 `COleLinkingDoc` 和`COleServerDoc`派生自`COleDocument`，因此这些类都继承中可用的所有服务`COleDocument`和**CDocument**。  
  
 若要使用`COleDocument`、 从其派生一个类并添加功能来管理应用程序的非 OLE 数据以及嵌入项或者链接项。 如果你定义`CDocItem`-派生类来存储应用程序的本机数据，你可以使用所定义的默认实现`COleDocument`来存储您的 OLE 和非 OLE 数据。 你还可以设计自己的数据结构的存储非 OLE 数据分开 OLE 项。 有关详细信息，请参阅文章[容器： 复合文件](../../mfc/containers-compound-files.md)...  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 `COleDocument` 已更新[OnFileSendMail](#onfilesendmail)若要正确处理复合文档。 有关详细信息，请参阅文章[MAPI](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="additem"></a>  COleDocument::AddItem  
 调用此函数可将项添加到文档。  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要添加的文档项的指针。  
  
### <a name="remarks"></a>备注  
 不需要显式调用此函数，它被调用时`COleClientItem`或`COleServerItem`接受指向文档的指针的构造函数。  
  
##  <a name="applyprintdevice"></a>  COleDocument::ApplyPrintDevice  
 调用此函数可更改打印目标设备的所有嵌入[COleClientItem](../../mfc/reference/coleclientitem-class.md)应用程序的容器文档中的项。  
  
```  
BOOL ApplyPrintDevice(const DVTARGETDEVICE* ptd);  
BOOL ApplyPrintDevice(const PRINTDLG* ppd);
```  
  
### <a name="parameters"></a>参数  
 `ptd`  
 指向**DVTARGETDEVICE**数据结构，其中包含有关新的打印目标设备的信息。 可以是**NULL**。  
  
 `ppd`  
 指向**PRINTDLG**数据结构，其中包含有关新的打印目标设备的信息。 可以是**NULL**。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数更新打印目标设备的所有项，但不刷新这些项的演示文稿缓存。 若要更新项的演示文稿缓存，调用[COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。  
  
 此函数的自变量包含 OLE 使用来标识目标设备的信息。 [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)结构包含 Windows 用来初始化通用的打印对话框的信息。 用户关闭对话框后，Windows 将返回此结构中的信息的用户的选择。 `m_pd`的成员[CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象是**PRINTDLG**结构。  
  
 有关详细信息，请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) Windows SDK 中的结构。  
  
 有关详细信息，请参阅[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) Windows SDK 中的结构。  
  
##  <a name="coledocument"></a>  COleDocument::COleDocument  
 构造 `COleDocument` 对象。  
  
```  
COleDocument();
```  
  
##  <a name="enablecompoundfile"></a>  COleDocument::EnableCompoundFile  
 如果你想要存储使用复合文件格式的文档，请调用此函数。  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是启用还是禁用复合文件的支持。  
  
### <a name="remarks"></a>备注  
 这也称为结构化的存储。 通常从的构造函数中调用此函数你`COleDocument`-派生类。 有关复合文档的详细信息，请参阅文章[容器： 复合文件](../../mfc/containers-compound-files.md)...  
  
 如果不调用此成员函数，则文档将存储在一种非结构化的 （"简单"） 文件格式。  
  
 复合文件的支持是启用还是禁用文档后，应不会在文档的生存期内更改设置。  
  
##  <a name="getinplaceactiveitem"></a>  COleDocument::GetInPlaceActiveItem  
 在包含由视图的框架窗口中的位置中当前激活调用此函数可获取 OLE 项`pWnd`。  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向显示容器文档窗口的指针。  
  
### <a name="return-value"></a>返回值  
 指向单个、 处于就地活动 OLE 项;**NULL**如果没有 OLE 项当前处于"处于就地活动状态"状态。  
  
##  <a name="getnextclientitem"></a>  COleDocument::GetNextClientItem  
 调用此函数重复可访问每个文档中的客户端项。  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**值设置到的以前调用`GetNextClientItem`; 初始值由返回`GetStartPosition`成员函数。  
  
### <a name="return-value"></a>返回值  
 对在文档中下, 一步的客户端项的指针或**NULL**如果没有更多的客户端项。  
  
### <a name="remarks"></a>备注  
 每个调用的值后`pos`为在文档中，可能会也可能不是客户端项的下一项设置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#1](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="getnextitem"></a>  COleDocument::GetNextItem  
 调用此函数重复可访问每个文档中的项。  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**值设置到的以前调用`GetNextItem`; 初始值由返回`GetStartPosition`成员函数。  
  
### <a name="return-value"></a>返回值  
 指向位于指定位置的文档项的指针。  
  
### <a name="remarks"></a>备注  
 每个调用的值后`pos`设置为**位置**的文档中的下一项的值。 检索的元素是否在文档中，新值的最后一个元素`pos`是**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer#2](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="getnextserveritem"></a>  COleDocument::GetNextServerItem  
 调用此函数重复可访问每个服务器项在文档中。  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**值设置到的以前调用`GetNextServerItem`; 初始值由返回`GetStartPosition`成员函数。  
  
### <a name="return-value"></a>返回值  
 在文档中下, 一步的服务器项的指针或**NULL**如果没有更多的服务器项。  
  
### <a name="remarks"></a>备注  
 每个调用的值后`pos`为在文档中，可能会也可能不是服务器项的下一项设置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleServer#2](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="getprimaryselecteditem"></a>  COleDocument::GetPrimarySelectedItem  
 由框架调用以检索指定的视图中的当前所选的 OLE 项。  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>参数  
 `pView`  
 显示文档的活动视图对象的指针。  
  
### <a name="return-value"></a>返回值  
 指向单，选择 OLE 项;**NULL**如果没有 OLE 选择项目，或如果多个一个处于选中状态。  
  
### <a name="remarks"></a>备注  
 默认实现为单个的选定项的项的包含 OLE 列表中搜索，并将指针返回到它。 如果没有项选择，或如果多个选定的项，则该函数返回**NULL**。 必须重写`CView::IsSelected`此函数可工作的视图类中的成员函数。 如果你有自己的存储包含的 OLE 项的方法，重写此函数。  
  
##  <a name="getstartposition"></a>  COleDocument::GetStartPosition  
 调用此函数可获取了文档中的第一项的位置。  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 A**位置**可用于循环访问文档的项; 开始的值**NULL**如果文档没有任何项。  
  
### <a name="remarks"></a>备注  
 返回到的值传递`GetNextItem`， `GetNextClientItem`，或`GetNextServerItem`。  
  
##  <a name="hasblankitems"></a>  COleDocument::HasBlankItems  
 调用此函数可确定文档是否包含任何空白项。  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果文档包含任何空白项; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 空白项是其矩形为空。  
  
##  <a name="oneditchangeicon"></a>  COleDocument::OnEditChangeIcon  
 显示 OLE 更改图标对话框中，并更改用户选择在对话框中的图标表示当前所选的 OLE 项的图标。  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>备注  
 `OnEditChangeIcon` 创建并启动`COleChangeIconDialog`更改图标对话框。  
  
##  <a name="oneditconvert"></a>  COleDocument::OnEditConvert  
 显示 OLE 转换对话框中和将转换或激活根据用户选择在对话框中当前选定的 OLE 项。  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>备注  
 `OnEditConvert` 创建并启动`COleConvertDialog`转换对话框。  
  
 转换的示例将 Microsoft Word 文档转换为写字板文档。  
  
##  <a name="oneditlinks"></a>  COleDocument::OnEditLinks  
 显示 OLE 编辑/链接对话框。  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>备注  
 `OnEditLinks` 创建并启动`COleLinksDialog`链接对话框中，用户可以更改所链接的对象。  
  
##  <a name="onfilesendmail"></a>  COleDocument::OnFileSendMail  
 发送消息通过常驻邮件主机 （如果有） 与文档作为附件。  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>备注  
 `OnFileSendMail` 调用`OnSaveDocument`（保存） 到一个临时文件，然后通过电子邮件发送的未命名和修改文档序列化。 如果文档未进行修改，则不需要的临时文件;发送原始。 `OnFileSendMail` 加载 MAPI32。如果尚未加载的 DLL。  
  
 与不同的实现`OnFileSendMail`为**CDocument**，此函数可以正确处理复合文件。  
  
 有关详细信息，请参阅[MAPI 主题](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)文章...  
  
##  <a name="onshowviews"></a>  COleDocument::OnShowViews  
 框架调用此函数后文档的可见性状态更改。  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>参数  
 `bVisible`  
 表示文档已变得可见或不可见。  
  
### <a name="remarks"></a>备注  
 此函数的默认版本没有任何影响。 如果你的应用程序必须执行任何特殊处理，该文档的可见性更改时，重写它。  
  
##  <a name="onupdateeditchangeicon"></a>  COleDocument::OnUpdateEditChangeIcon  
 由框架调用以更新编辑菜单上的更改图标命令。  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`若要更新的用户界面。  
  
### <a name="remarks"></a>备注  
 `OnUpdateEditChangeIcon` 更新了命令的用户界面，具体取决于有效的图标存在文档中。 重写此函数可更改的行为。  
  
##  <a name="onupdateeditlinksmenu"></a>  COleDocument::OnUpdateEditLinksMenu  
 由框架调用以更新编辑菜单上的链接命令。  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`若要更新的用户界面。  
  
### <a name="remarks"></a>备注  
 与在文档中，第一个 OLE 项启动`OnUpdateEditLinksMenu`访问每个项，测试是否项是一个链接，并且如果它是一个链接，可以让链接命令。 重写此函数可更改的行为。  
  
##  <a name="onupdateobjectverbmenu"></a>  COleDocument::OnUpdateObjectVerbMenu  
 由框架更新调用*ObjectName*命令编辑菜单和谓词子菜单从访问*ObjectName*命令，其中*ObjectName*是的名称在文档中嵌入的 OLE 对象。  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`若要更新的用户界面。  
  
### <a name="remarks"></a>备注  
 `OnUpdateObjectVerbMenu` 更新*ObjectName*具体取决于有效的对象是否存在文档中的命令的用户界面。 如果存在的对象， *ObjectName*启用编辑菜单上的命令。 选择此菜单命令时，将显示谓词子菜单。 谓词子菜单包含可用于对象，如编辑、 属性和等等的所有谓词命令。 重写此函数可更改的行为。  
  
##  <a name="onupdatepastelinkmenu"></a>  COleDocument::OnUpdatePasteLinkMenu  
 由框架调用以确定是否可以从剪贴板粘贴链接的 OLE 项。  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`若要更新的用户界面。  
  
### <a name="remarks"></a>备注  
 启用或禁用具体取决于是否项可将粘贴到文档或不选择性粘贴的菜单命令。  
  
##  <a name="onupdatepastemenu"></a>  COleDocument::OnUpdatePasteMenu  
 由框架调用以确定是否可以从剪贴板粘贴嵌入的 OLE 项。  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 指向的指针`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`若要更新的用户界面。  
  
### <a name="remarks"></a>备注  
 启用或禁用具体取决于是否项可将粘贴到文档或不粘贴菜单命令和按钮。  
  
##  <a name="removeitem"></a>  COleDocument::RemoveItem  
 调用此函数可从文档中移除一个项。  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 指向要删除的文档项的指针。  
  
### <a name="remarks"></a>备注  
 通常不需要显式; 调用此函数它由的析构函数进行调用`COleClientItem`和`COleServerItem`。  
  
##  <a name="updatemodifiedflag"></a>  COleDocument::UpdateModifiedFlag  
 调用此函数可将该文档标记为已修改如果修改了任何包含的 OLE 项。  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>备注  
 这样，框架以提示用户在结束之前，保存文档，即使尚未修改文档中的本机数据。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例容器](../../visual-cpp-samples.md)   
 [MFC 示例 MFCBIND](../../visual-cpp-samples.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



