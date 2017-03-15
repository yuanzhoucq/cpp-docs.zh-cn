---
title: "COleDocument 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDocument
dev_langs:
- C++
helpviewer_keywords:
- COleDocument class
- OLE documents, base class
- OLE containers, client items
- visual editing, OLE document base class
- OLE documents
- documents, OLE
ms.assetid: dc2ecb99-03e1-44c7-bb69-48056dd1b672
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 73bd1bc5c2c93e180b42a79cf23ab98360887c31
ms.lasthandoff: 02/24/2017

---
# <a name="coledocument-class"></a>COleDocument 类
支持可视编辑的 OLE 文档的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDocument : public CDocument  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleDocument::COleDocument](#coledocument)|构造 `COleDocument` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleDocument::AddItem](#additem)|将项添加到保留在文档中的项的列表。|  
|[COleDocument::ApplyPrintDevice](#applyprintdevice)|设置文档中的所有客户端项目的打印目标设备。|  
|[COleDocument::EnableCompoundFile](#enablecompoundfile)|使文档，以使用 OLE 结构化存储文件格式存储。|  
|[COleDocument::GetInPlaceActiveItem](#getinplaceactiveitem)|返回是当前处于就地活动状态的 OLE 项。|  
|[COleDocument::GetNextClientItem](#getnextclientitem)|获取循环的下一个客户端项目。|  
|[COleDocument::GetNextItem](#getnextitem)|获取循环的下一步的文档项。|  
|[COleDocument::GetNextServerItem](#getnextserveritem)|获取循环的下一个服务器项目。|  
|[COleDocument::GetPrimarySelectedItem](#getprimaryselecteditem)|返回的文档中的主选定的 OLE 项。|  
|[COleDocument::GetStartPosition](#getstartposition)|获取开始迭代的初始位置。|  
|[COleDocument::HasBlankItems](#hasblankitems)|检查文档中的空项。|  
|[COleDocument::OnShowViews](#onshowviews)|时，调用文档变得可见或不可见。|  
|[COleDocument::RemoveItem](#removeitem)|从在文档中保留的项列表中移除项。|  
|[COleDocument::UpdateModifiedFlag](#updatemodifiedflag)|将该文档标记为已修改，如果修改了任何所含的 OLE 项。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleDocument::OnEditChangeIcon](#oneditchangeicon)|处理中的更改图标菜单命令的事件。|  
|[COleDocument::OnEditConvert](#oneditconvert)|处理从一种类型到另一个转换嵌入或链接的对象。|  
|[COleDocument::OnEditLinks](#oneditlinks)|处理在编辑菜单上的链接命令中的事件。|  
|[COleDocument::OnFileSendMail](#onfilesendmail)|将包含附加的文档发送一封电子邮件。|  
|[COleDocument::OnUpdateEditChangeIcon](#onupdateeditchangeicon)|由框架用于更新命令 UI 的编辑 / 更改图标菜单选项调用。|  
|[COleDocument::OnUpdateEditLinksMenu](#onupdateeditlinksmenu)|由框架用于更新命令 UI 的编辑/链接菜单选项调用。|  
|[COleDocument::OnUpdateObjectVerbMenu](#onupdateobjectverbmenu)|由框架调用以更新命令 UI 以进行编辑 / *ObjectName*菜单选项和谓词子菜单从编辑访问 / *ObjectName*。|  
|[COleDocument::OnUpdatePasteLinkMenu](#onupdatepastelinkmenu)|由框架用于更新命令 UI 的选择性粘贴菜单选项调用。|  
|[COleDocument::OnUpdatePasteMenu](#onupdatepastemenu)|由框架用于更新命令 UI 粘贴菜单选项的调用。|  
  
## <a name="remarks"></a>备注  
 `COleDocument`派生自**CDocument**，这样在 OLE 应用程序，可使用由 Microsoft 基础类库提供的文档/视图体系结构。  
  
 `COleDocument`将文档视为一套[CDocItem](../../mfc/reference/cdocitem-class.md)对象以处理 OLE 项。 容器和服务器应用程序需要这样的体系结构，因为他们的文档必须能够包含 OLE 项。 [COleServerItem](../../mfc/reference/coleserveritem-class.md)和[COleClientItem](../../mfc/reference/coleclientitem-class.md)类都派生自`CDocItem`，管理应用程序和 OLE 项之间的交互。  
  
 如果您正在编写一个简单的容器应用程序，派生文档类从`COleDocument`。 如果您正在编写支持将链接到其文档所包含的嵌入项的容器应用程序，派生文档类从[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)。 如果您正在编写服务器应用程序或组合容器/服务器，派生文档类从[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)。 `COleLinkingDoc`和`COleServerDoc`派生自`COleDocument`，因此这些类都继承中可用的所有服务`COleDocument`和**CDocument**。  
  
 若要使用`COleDocument`、 从其派生一个类并添加功能来管理应用程序的非 OLE 数据以及嵌入项或者链接项。 如果您定义`CDocItem`的派生类来存储应用程序的本机数据，您可以使用所定义的默认实现`COleDocument`来存储您的 OLE 和非 OLE 数据。 您还可以设计您自己用于存储非 OLE 数据分开的 OLE 项的数据结构。 有关详细信息，请参阅文章[容器︰ 复合文件](../../mfc/containers-compound-files.md)...  
  
 **CDocument**支持将您的文档通过邮件发送邮件支持 (MAPI) 是否存在。 `COleDocument`已更新[OnFileSendMail](#onfilesendmail)以便正确地处理复合文档。 有关详细信息，请参阅文章[MAPI](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)...  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `COleDocument`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="a-nameadditema--coledocumentadditem"></a><a name="additem"></a>COleDocument::AddItem  
 调用此函数可将项添加到该文档。  
  
```  
virtual void AddItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 为将要添加的文档项的指针。  
  
### <a name="remarks"></a>备注  
 不需要显式调用此函数，调用时`COleClientItem`或`COleServerItem`接受指向文档的指针构造函数。  
  
##  <a name="a-nameapplyprintdevicea--coledocumentapplyprintdevice"></a><a name="applyprintdevice"></a>COleDocument::ApplyPrintDevice  
 调用此函数可更改所有嵌入的打印目标设备[COleClientItem](../../mfc/reference/coleclientitem-class.md)应用程序的容器文档中的项。  
  
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
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数更新打印目标设备的所有项，而不会刷新这些项的演示文稿缓存。 若要更新某个项的演示文稿缓存，请调用[COleClientItem::UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink)。  
  
 对此函数的参数包含 OLE 使用来标识目标设备的信息。 [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)结构包含 Windows 用来初始化常见打印对话框中的信息。 用户关闭对话框后，Windows 将在此结构中返回有关用户的选择信息。 `m_pd`的成员[CPrintDialog](../../mfc/reference/cprintdialog-class.md)对象是**PRINTDLG**结构。  
  
 有关详细信息，请参阅[PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namecoledocumenta--coledocumentcoledocument"></a><a name="coledocument"></a>COleDocument::COleDocument  
 构造 `COleDocument` 对象。  
  
```  
COleDocument();
```  
  
##  <a name="a-nameenablecompoundfilea--coledocumentenablecompoundfile"></a><a name="enablecompoundfile"></a>COleDocument::EnableCompoundFile  
 如果您想要使用复合文件格式将文档存储，请调用此函数。  
  
```  
void EnableCompoundFile(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是启用还是禁用复合文件的支持。  
  
### <a name="remarks"></a>备注  
 这也称为结构化的存储。 您通常从的构造函数中调用此函数在`COleDocument`的派生类。 有关复合文档的详细信息，请参阅文章[容器︰ 复合文件](../../mfc/containers-compound-files.md)...  
  
 如果未调用此成员函数，文档将存储非结构化 （"平面"） 文件格式。  
  
 复合文件的支持是启用还是禁用文档后，应不会在文档的生存期内更改设置。  
  
##  <a name="a-namegetinplaceactiveitema--coledocumentgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>COleDocument::GetInPlaceActiveItem  
 调用此函数可获取 OLE 项在框架窗口包含由该视图中就地对目前处于激活状态`pWnd`。  
  
```  
virtual COleClientItem* GetInPlaceActiveItem(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 对显示在容器文档的窗口的指针。  
  
### <a name="return-value"></a>返回值  
 一个指向单一、 就地活动 OLE 项;**NULL**有任何 OLE 项当前是否处于"处于就地活动状态"状态。  
  
##  <a name="a-namegetnextclientitema--coledocumentgetnextclientitem"></a><a name="getnextclientitem"></a>COleDocument::GetNextClientItem  
 调用此函数重复，若要访问每个文档中的客户端项目。  
  
```  
COleClientItem* GetNextClientItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**值设置到的以前调用`GetNextClientItem`; 返回的初始值`GetStartPosition`成员函数。  
  
### <a name="return-value"></a>返回值  
 在文档中下, 一步的客户端项的指针或**NULL**如果没有更多的客户端项目。  
  
### <a name="remarks"></a>备注  
 在每次调用，值`pos`为在文档中，可能会也可能不是客户端项的下一项设置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&1;](../../mfc/codesnippet/cpp/coledocument-class_1.cpp)]  
  
##  <a name="a-namegetnextitema--coledocumentgetnextitem"></a><a name="getnextitem"></a>COleDocument::GetNextItem  
 调用此函数重复，若要访问每个文档中的项。  
  
```  
virtual CDocItem* GetNextItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**值设置到的以前调用`GetNextItem`; 返回的初始值`GetStartPosition`成员函数。  
  
### <a name="return-value"></a>返回值  
 指向指定位置处的文档项的指针。  
  
### <a name="remarks"></a>备注  
 在每次调用，值`pos`设置为**位置**文档中的下一项的值。 如果检索的元素是在文档中的新值的最后一个元素`pos`是**NULL**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleContainer #&2;](../../mfc/codesnippet/cpp/coledocument-class_2.cpp)]  
  
##  <a name="a-namegetnextserveritema--coledocumentgetnextserveritem"></a><a name="getnextserveritem"></a>COleDocument::GetNextServerItem  
 调用此函数重复，若要访问每个文档中的服务器项。  
  
```  
COleServerItem* GetNextServerItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>参数  
 `pos`  
 对引用**位置**值设置到的以前调用`GetNextServerItem`; 返回的初始值`GetStartPosition`成员函数。  
  
### <a name="return-value"></a>返回值  
 在文档中下, 一步的服务器项的指针或**NULL**如果没有更多的服务器项目。  
  
### <a name="remarks"></a>备注  
 在每次调用，值`pos`为在文档中，可能会也可能不是服务器项的下一项设置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCOleServer #&2;](../../mfc/codesnippet/cpp/coledocument-class_3.cpp)]  
  
##  <a name="a-namegetprimaryselecteditema--coledocumentgetprimaryselecteditem"></a><a name="getprimaryselecteditem"></a>COleDocument::GetPrimarySelectedItem  
 由框架来检索在指定视图中当前所选的 OLE 项调用。  
  
```  
virtual COleClientItem* GetPrimarySelectedItem(CView* pView);
```  
  
### <a name="parameters"></a>参数  
 `pView`  
 显示文档的活动视图对象的指针。  
  
### <a name="return-value"></a>返回值  
 指针转换为 single，选择 OLE 项;**NULL**如果不选择任何 OLE 项目，或者如果有多个选择一个。  
  
### <a name="remarks"></a>备注  
 默认实现单个选定项的项的包含 OLE 在列表中搜索，并将指针返回到它。 如果不存在的项选择，或者如果选定的多个项，则该函数返回**NULL**。 必须重写`CView::IsSelected`为此函数可工作视图类中的成员函数。 如果您有自己的存储包含的 OLE 项的方法，重写此函数。  
  
##  <a name="a-namegetstartpositiona--coledocumentgetstartposition"></a><a name="getstartposition"></a>COleDocument::GetStartPosition  
 调用此函数可获取在文档中的第一项的位置。  
  
```  
virtual POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**位置**值，该值可用于开始遍历文档的项;**NULL**如果文档不有任何项。  
  
### <a name="remarks"></a>备注  
 将返回到的值传递`GetNextItem`， `GetNextClientItem`，或`GetNextServerItem`。  
  
##  <a name="a-namehasblankitemsa--coledocumenthasblankitems"></a><a name="hasblankitems"></a>COleDocument::HasBlankItems  
 调用此函数可确定文档是否包含任何空白项目。  
  
```  
BOOL HasBlankItems() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果文档包含任何空白项，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 空白项是其矩形为空。  
  
##  <a name="a-nameoneditchangeicona--coledocumentoneditchangeicon"></a><a name="oneditchangeicon"></a>COleDocument::OnEditChangeIcon  
 显示 OLE 更改图标对话框中，并会更改用户在对话框中选择的图标表示当前所选的 OLE 项的图标。  
  
```  
afx_msg void OnEditChangeIcon();
```  
  
### <a name="remarks"></a>备注  
 `OnEditChangeIcon`可创建并启动`COleChangeIconDialog`更改图标对话框。  
  
##  <a name="a-nameoneditconverta--coledocumentoneditconvert"></a><a name="oneditconvert"></a>COleDocument::OnEditConvert  
 显示 OLE 转换对话框中，将转换或激活对话框中的用户选择根据当前所选的 OLE 项。  
  
```  
afx_msg void OnEditConvert();
```  
  
### <a name="remarks"></a>备注  
 `OnEditConvert`可创建并启动`COleConvertDialog`Convert 对话框。  
  
 转换的示例将 Microsoft Word 文档转换到写字板文档。  
  
##  <a name="a-nameoneditlinksa--coledocumentoneditlinks"></a><a name="oneditlinks"></a>COleDocument::OnEditLinks  
 显示 OLE 编辑/链接对话框。  
  
```  
afx_msg void OnEditLinks();
```  
  
### <a name="remarks"></a>备注  
 `OnEditLinks`可创建并启动`COleLinksDialog`链接对话框中，用户可以更改所链接的对象。  
  
##  <a name="a-nameonfilesendmaila--coledocumentonfilesendmail"></a><a name="onfilesendmail"></a>COleDocument::OnFileSendMail  
 从常驻邮件主机发送的消息 （如果有） 将包含发送文档以附件形式。  
  
```  
afx_msg void OnFileSendMail();
```  
  
### <a name="remarks"></a>备注  
 `OnFileSendMail`调用`OnSaveDocument`要序列化 （保存） 到一个临时文件，然后通过电子邮件发送的未命名和修改文档。 如果文档未进行修改，则不需要的临时文件;发送原始。 `OnFileSendMail`加载 MAPI32。如果尚未加载的 DLL。  
  
 与不同的实现`OnFileSendMail`为**CDocument**，此函数可以正确处理复合文件。  
  
 有关详细信息，请参阅[MAPI 主题](../../mfc/mapi.md)和[MFC 中的 MAPI 支持](../../mfc/mapi-support-in-mfc.md)文章...  
  
##  <a name="a-nameonshowviewsa--coledocumentonshowviews"></a><a name="onshowviews"></a>COleDocument::OnShowViews  
 框架调用此函数后文档的可见性状态更改。  
  
```  
virtual void OnShowViews(BOOL bVisible);
```  
  
### <a name="parameters"></a>参数  
 `bVisible`  
 表示文档已变得可见或不可见。  
  
### <a name="remarks"></a>备注  
 此函数的默认版本没有任何影响。 如果您的应用程序必须执行任何特殊处理，文档的可见性发生更改时，请将其覆盖。  
  
##  <a name="a-nameonupdateeditchangeicona--coledocumentonupdateeditchangeicon"></a><a name="onupdateeditchangeicon"></a>COleDocument::OnUpdateEditChangeIcon  
 由框架来更新编辑菜单上的更改图标命令调用。  
  
```  
afx_msg void OnUpdateEditChangeIcon(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`来更新用户界面。  
  
### <a name="remarks"></a>备注  
 `OnUpdateEditChangeIcon`更新命令的用户界面，具体取决于是有效的图标存在于文档中。 重写此函数可更改的行为。  
  
##  <a name="a-nameonupdateeditlinksmenua--coledocumentonupdateeditlinksmenu"></a><a name="onupdateeditlinksmenu"></a>COleDocument::OnUpdateEditLinksMenu  
 由框架以便更新在编辑菜单上的链接命令调用。  
  
```  
afx_msg void OnUpdateEditLinksMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`来更新用户界面。  
  
### <a name="remarks"></a>备注  
 在文档中，第一个 OLE 项从开始`OnUpdateEditLinksMenu`访问每个项，测试该项目是否链接，以及它是一个链接，如果启用链接命令。 重写此函数可更改的行为。  
  
##  <a name="a-nameonupdateobjectverbmenua--coledocumentonupdateobjectverbmenu"></a><a name="onupdateobjectverbmenu"></a>COleDocument::OnUpdateObjectVerbMenu  
 由框架调用以更新*ObjectName*命令在编辑菜单和谓词子菜单从访问*ObjectName*命令，其中*ObjectName*在文档中嵌入的 OLE 对象的名称。  
  
```  
afx_msg void OnUpdateObjectVerbMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`来更新用户界面。  
  
### <a name="remarks"></a>备注  
 `OnUpdateObjectVerbMenu`更新*ObjectName*具体取决于是否是有效的对象存在于文档中的命令的用户界面。 如果对象存在， *ObjectName*启用编辑菜单上的命令。 当选择此菜单命令时，将显示谓词子菜单。 谓词子菜单包含可用于对象，如编辑、 属性等的所有动词命令。 重写此函数可更改的行为。  
  
##  <a name="a-nameonupdatepastelinkmenua--coledocumentonupdatepastelinkmenu"></a><a name="onupdatepastelinkmenu"></a>COleDocument::OnUpdatePasteLinkMenu  
 由框架来确定是否可以从剪贴板中粘贴链接的 OLE 项调用。  
  
```  
afx_msg void OnUpdatePasteLinkMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`来更新用户界面。  
  
### <a name="remarks"></a>备注  
 启用或禁用具体取决于是否项可将粘贴到文档或不选择性粘贴的菜单命令。  
  
##  <a name="a-nameonupdatepastemenua--coledocumentonupdatepastemenu"></a><a name="onupdatepastemenu"></a>COleDocument::OnUpdatePasteMenu  
 由框架来确定是否可以从剪贴板中粘贴嵌入的 OLE 项调用。  
  
```  
afx_msg void OnUpdatePasteMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>参数  
 `pCmdUI`  
 一个指向`CCmdUI`结构，它表示生成更新命令的菜单。 更新处理程序调用**启用**成员函数`CCmdUI`结构通过`pCmdUI`来更新用户界面。  
  
### <a name="remarks"></a>备注  
 启用或禁用具体取决于是否项可将粘贴到文档或不粘贴菜单命令和按钮。  
  
##  <a name="a-nameremoveitema--coledocumentremoveitem"></a><a name="removeitem"></a>COleDocument::RemoveItem  
 调用此函数可从文档中移除一个项。  
  
```  
virtual void RemoveItem(CDocItem* pItem);
```  
  
### <a name="parameters"></a>参数  
 `pItem`  
 要删除的文档项的指针。  
  
### <a name="remarks"></a>备注  
 通常不需要显式; 调用此函数它由的析构函数调用`COleClientItem`和`COleServerItem`。  
  
##  <a name="a-nameupdatemodifiedflaga--coledocumentupdatemodifiedflag"></a><a name="updatemodifiedflag"></a>COleDocument::UpdateModifiedFlag  
 调用此函数可将该文档标记为已修改，如果修改了任何所含的 OLE 项。  
  
```  
virtual void UpdateModifiedFlag();
```  
  
### <a name="remarks"></a>备注  
 这样，框架以提示用户将文档保存到在结束之前，即使在文档中的本机数据未修改。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例容器](../../visual-cpp-samples.md)   
 [MFC 示例 MFCBIND](../../visual-cpp-samples.md)   
 [CDocument 类](../../mfc/reference/cdocument-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




