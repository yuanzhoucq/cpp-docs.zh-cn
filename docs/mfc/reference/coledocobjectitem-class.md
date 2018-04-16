---
title: "COleDocObjectItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 246c645dad5ed11fb5428e2f90ed9b9574696417
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem 类
实现活动文档包容。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|构造`COleDocObject`项。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|使用默认打印机设置的容器应用程序的文档进行打印。|  
|[COleDocObjectItem::ExecCommand](#execcommand)|执行由用户指定的命令。|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|检索文档的活动视图。|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|检索容器应用程序的文档中的页面数。|  
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|准备容器应用程序的文档进行打印。|  
|[COleDocObjectItem::OnPrint](#onprint)|容器应用程序的文档进行打印。|  
|[COleDocObjectItem::QueryCommand](#querycommand)|查询由用户界面事件生成的一个或多个命令的状态。|  
|[COleDocObjectItem::Release](#release)|释放的 OLE 项链接到的连接，并将其关闭，如果它处于打开状态。 不会销毁客户端项。|  
  
## <a name="remarks"></a>备注  
 在 MFC 中，活动文档被处理方法类似于常规、 就地编辑嵌入，具有以下差异：  
  
-   `COleDocument`-派生的类仍保留当前嵌入项的列表; 但是，这些项可能`COleDocObjectItem`-派生的项。  
  
-   活动文档处于活动状态，它会占用整个工作区的视图，处于就地活动状态时。  
  
-   活动文档容器具有完全控制**帮助**菜单。  
  
-   **帮助**菜单包含活动文档容器和服务器的菜单项。  
  
 由于活动文档容器拥有**帮助**菜单中，容器负责转发服务器**帮助**菜单消息到服务器。 此集成由`COleDocObjectItem`。  
  
 有关菜单合并功能和活动文档激活的详细信息，请参阅概述[活动文档包容](../../mfc/active-document-containment.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxole.h  
  
##  <a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem  
 调用此成员函数可初始化`COleDocObjectItem`对象。  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pContainerDoc`  
 指向的指针`COleDocument`充当活动文档容器的对象。 此参数必须是**NULL**启用**IMPLEMENT_SERIALIZE**。 通常将 OLE 项构造与非**NULL**文档指针。  
  
##  <a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting  
 由使用默认设置的文档框架调用。  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>参数  
 `pCaller`  
 指向的指针[CView](../../mfc/reference/cview-class.md)发送打印命令的对象。  
  
 `pInfo`  
 指向的指针[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象，描述要打印的作业。  
  
##  <a name="execcommand"></a>COleDocObjectItem::ExecCommand  
 调用此成员函数以执行用户指定的命令。  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nCmdID`  
 要执行的命令标识符。 必须在由标识的组`pguidCmdGroup`。  
  
 `nCmdExecOpt`  
 指定命令执行选项。 默认情况下，设置以执行该命令而不提示用户。 请参阅[OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930)有关值的列表。  
  
 `pguidCmdGroup`  
 命令组的唯一标识符。 默认情况下， **NULL**，它指定标准的组。 该命令传递中`nCmdID`必须属于的组。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`如果成功; 否则，返回以下错误代码之一。  
  
|“值”|描述|  
|-----------|-----------------|  
|**E_UNEXPECTED**|出现意外的错误。|  
|**E_FAIL**|出现错误。|  
|**E_NOTIMPL**|指示 MFC 本身应尝试转换并将其分派命令。|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`为非**NULL** ，但未指定识别的命令组。|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`无法识别为有效命令组 pGroup 中。|  
|**OLECMDERR_DISABLED**|由该命令`nCmdID`处于禁用状态，并且无法执行。|  
|**OLECMDERR_NOHELP**|调用方标识的命令上要求帮助`nCmdID`但没有帮助可用。|  
|**OLECMDERR_CANCELLED**|用户已取消执行。|  
  
### <a name="remarks"></a>备注  
 `pguidCmdGroup`和`nCmdID`参数一起唯一标识要调用的命令。 `nCmdExecOpt`参数指定要执行的准确操作。  
  
##  <a name="getactiveview"></a>COleDocObjectItem::GetActiveView  
 调用此成员函数以获取指向`IOleDocumentView`接口的当前处于活动状态的视图。  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[IOleDocumentView](http://msdn.microsoft.com/library/windows/desktop/ms678455)接口的当前处于活动状态的视图。 如果没有当前视图，它返回**NULL**。  
  
### <a name="remarks"></a>备注  
 对返回的引用计数`IOleDocumentView`此函数返回之前，不会增加指针。  
  
##  <a name="getpagecount"></a>COleDocObjectItem::GetPageCount  
 调用此成员函数可检索文档中的页面数。  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>参数  
 *pnFirstPage*  
 指向文档的第一页的数的指针。 可以是**NULL**，指示调用方不需要此数字。  
  
 *pcPages*  
 指向文档中的页面的总数的指针。 可以是**NULL**，指示调用方不需要此数字。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting  
 由框架用于打印准备文档调用此成员函数。  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pCaller`  
 指向的指针[CView](../../mfc/reference/cview-class.md)发送打印命令的对象。  
  
 `pInfo`  
 指向的指针[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象，描述要打印的作业。  
  
 `bPrintAll`  
 指定是否要打印整个文档。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="onprint"></a>COleDocObjectItem::OnPrint  
 此成员函数调用由框架打印文档。  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pCaller`  
 指向正在发送打印命令 CView 对象的指针。  
  
 `pInfo`  
 指向的指针[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)对象，描述要打印的作业。  
  
 `bPrintAll`  
 指定是否要打印整个文档。  
  
##  <a name="querycommand"></a>COleDocObjectItem::QueryCommand  
 查询由用户界面事件生成的一个或多个命令的状态。  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>参数  
 `nCmdID`  
 要查询的命令标识符。  
  
 `pdwStatus`  
 指向作为查询的结果而返回的标志的指针。 有关可能的值的列表，请参阅[OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237)。  
  
 `pCmdText`  
 指向[OLECMDTEXT](http://msdn.microsoft.com/library/windows/desktop/ms693314)中要返回其为单个命令的名称和状态信息的结构。 可以是**NULL**以指示调用方不需要此信息。  
  
 `pguidCmdGroup`  
 命令组中; 的唯一标识符可以是**NULL**指定标准的组。  
  
### <a name="return-value"></a>返回值  
 返回值的完整列表，请参阅[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) Windows SDK 中。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491)方法，如 Windows SDK 中所述。  
  
##  <a name="release"></a>COleDocObjectItem::Release  
 释放的 OLE 项链接到的连接，并将其关闭，如果它处于打开状态。 不会销毁客户端项。  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>参数  
 `dwCloseOption`  
 指定在什么情况下，当它返回时向加载状态已保存该 OLE 项的标志。 有关可能的值的列表，请参阅[COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close)。  
  
### <a name="remarks"></a>备注  
 不会销毁客户端项。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MFCBIND](../../visual-cpp-samples.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem 类](../../mfc/reference/cdocobjectserveritem-class.md)
