---
title: "CDocObjectServer 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
dev_langs:
- C++
helpviewer_keywords:
- document object server
- CDocObjectServer class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 75fb0ba49d105a673e862ed3044e85ac9e990e9c
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 类
实现将常规 `COleDocument` 服务器接入完整 DocObject 服务器所需的其他 OLE 接口： `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|构造 `CDocObjectServer` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|激活的文档对象服务器，但不是显示它。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|显示 DocObject 视图。|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|还原 DocObject 视图的状态。|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|保存 DocObject 视图状态。|  
  
## <a name="remarks"></a>备注  
 `CDocObjectServer`派生自`CCmdTarget`和与紧密合作`COleServerDoc`要公开的接口。  
  
 DocObject 服务器文档可以包含[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) DocObject 项代表服务器接口的对象。  
  
 若要自定义 DocObject 服务器，请派生您自己的类从`CDocObjectServer`并重写其视图设置功能， [OnActivateView](#onactivateview)， [OnApplyViewState](#onapplyviewstate)，和[OnSaveViewState](#onsaveviewstate)。 您将需要提供您在框架将调用响应中的类的新实例。  
  
 DocObjects 的进一步信息，请参阅[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 参考*。 另请参阅[Internet 前几个步骤︰ 活动文档](../../mfc/active-documents-on-the-internet.md)和[活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
 另请参阅以下知识库文章︰  
  
-   Q247382: PRB: ActiveX 文档服务器中的控件的工具提示隐藏的 ActiveX 文档容器  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdocob.h  
  
##  <a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject  
 调用此函数可将文档对象服务器激活 （但不是显示）。  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>备注  
 `ActivateDocObject`调用`IOleDocumentSite`的**ActivateMe**方法，但不显示视图，因为它在等待如何设置和显示视图中，对的调用中提供的具体说明[CDocObjectServer::OnActivateView](#onactivateview)。  
  
 在一起，`ActivateDocObject`和`OnActivateView`激活并显示 DocObject 视图。 DocObject 激活不同于其他类型的 OLE 就地激活。 DocObject 激活将绕过显示就地阴影边框和对象 （如大小调整控点） 的修饰，将忽略对象扩展盘区功能，并绘制而不是在该矩形 （如在正常的就地激活） 的外部绘制它们的视图矩形中的滚动条。  
  
##  <a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer  
 构造并初始化一个 `CDocObjectServer` 对象。  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pOwner*  
 指向 DocObject 服务器的客户端的客户端站点文档的指针。  
  
 `pDocSite`  
 一个指向`IOleDocumentSite`由容器实现的接口。  
  
### <a name="remarks"></a>备注  
 当 DocObject 处于活动状态时，客户端站点 OLE 接口 ( `IOleDocumentSite`) 是什么使 DocObject 服务器与它的客户端 （容器） 进行通信。 当激活 DocObject 服务器时，它首先检查该容器实现`IOleDocumentSite`接口。 如果是这样， [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)调用以查看该容器是否支持 DocObjects。 默认情况下，`GetDocObjectServer`返回**NULL**。 必须重写`COleServerDoc::GetDocObjectServer`用于构造新`CDocObjectServer`对象或派生您自己的情况下，使用指向指针的对象`COleServerDoc`容器并将其`IOleDocumentSite`接口作为构造函数的参数。  
  
##  <a name="onactivateview"></a>CDocObjectServer::OnActivateView  
 调用此函数可显示 DocObject 视图。  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>返回值  
 返回错误或警告值。 默认情况下，返回**NOERROR**如果成功，否则为**E_FAIL**。  
  
### <a name="remarks"></a>备注  
 此函数创建的就地框架窗口、 绘制在视图中的滚动条、 设置服务器与其容器与共享、 添加框架控件、 设置活动的对象，则最后显示的就地框架窗口和将焦点设置的菜单。  
  
##  <a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState  
 重写此函数以还原 DocObject 视图的状态。  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 一个`CArchive`从中序列化的视图状态对象。  
  
### <a name="remarks"></a>备注  
 在完成其实例化后第一次显示视图时，调用此函数。 `OnApplyViewState`指示视图以重新初始化自身中的数据根据`CArchive`以前保存的与对象[OnSaveViewState](#onsaveviewstate)。 视图必须验证中的数据`CArchive`对象，因为该容器不会尝试解释以任何方式的视图状态数据。  
  
 您可以使用`OnSaveViewState`来存储持久性信息特定于您的视图状态。 如果重写`OnSaveViewState`来存储信息，您需要重写`OnApplyViewState`读取该信息并将其应用于您的视图中，新激活时。  
  
##  <a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState  
 重写此函数可保存 DocObject 视图有关的额外状态信息。  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 `ar`  
 一个`CArchive`视图状态序列化到对象。  
  
### <a name="remarks"></a>备注  
 您的状态可能包括属性，如视图类型、 缩放系数、 插入和选择点等。 容器通常在停用视图之前调用此函数。 稍后可以将已保存的状态还原通过[OnApplyViewState](#onapplyviewstate)。  
  
 您可以使用`OnSaveViewState`来存储持久性信息特定于您的视图状态。 如果重写`OnSaveViewState`来存储信息，您需要重写`OnApplyViewState`读取该信息并将其应用于您的视图中，新激活时。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem 类](../../mfc/reference/cdocobjectserveritem-class.md)

