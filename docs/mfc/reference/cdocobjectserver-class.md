---
title: CDocObjectServer 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f89812fbc0e1b6a3df80cd7c99879d8d630179de
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956451"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer 类
实现将常规 `COleDocument` 服务器接入完整 DocObject 服务器所需的其他 OLE 接口： `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`和 `IPrint`。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocObjectServer : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|构造 `CDocObjectServer` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|激活的文档对象服务器，但不显示它。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|显示 DocObject 视图。|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|还原 DocObject 视图的状态。|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|保存 DocObject 视图状态。|  
  
## <a name="remarks"></a>备注  
 `CDocObjectServer` 派生自`CCmdTarget`和与紧密合作`COleServerDoc`要公开的接口。  
  
 DocObject 服务器文档可以包含[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) DocObject 项表示的服务器接口的对象。  
  
 若要自定义 DocObject 服务器，请派生您自己的类从`CDocObjectServer`并重写其视图安装程序函数， [OnActivateView](#onactivateview)， [OnApplyViewState](#onapplyviewstate)，和[OnSaveViewState](#onsaveviewstate). 你将需要提供响应框架调用类的新实例。  
  
 DocObjects 的进一步信息，请参阅[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 参考*。 另请参阅[Internet 前几个步骤： 活动文档](../../mfc/active-documents-on-the-internet.md)和[活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
 另请参阅以下知识库文章：  
  
-   Q247382: PRB: ActiveX 文档 Server 中的控件的工具提示隐藏的 ActiveX 文档容器  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdocob.h  
  
##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject  
 调用此函数可激活 （但不是显示） 文档对象服务器。  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>备注  
 `ActivateDocObject` 调用`IOleDocumentSite`的`ActivateMe`方法，但不显示视图，因为它在等待有关如何设置并显示的视图，给定的调用中的特定说明[CDocObjectServer::OnActivateView](#onactivateview)。  
  
 在一起，`ActivateDocObject`和`OnActivateView`激活并显示 DocObject 视图。 DocObject 激活不同于其他类型的 OLE 就地激活。 DocObject 激活绕过显示就地阴影边框和 （如大小调整控点） 的对象修饰、 忽略对象扩展盘区功能，和绘制而不是外部 （如下所示正常该矩形中绘制这些视图矩形中的滚动条就地激活）。  
  
##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer  
 构造并初始化一个 `CDocObjectServer` 对象。  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pOwner*  
 指向 DocObject 服务器的客户端的客户端站点文档的指针。  
  
 *pDocSite*  
 指向的指针`IOleDocumentSite`由容器实现的接口。  
  
### <a name="remarks"></a>备注  
 当 DocObject 处于活动状态时，客户端站点 OLE 接口 ( `IOleDocumentSite`) 是什么使 DocObject 服务器与其客户端 （容器） 进行通信。 当激活 DocObject 服务器时，它首先检查容器实现`IOleDocumentSite`接口。 如果是这样， [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)称为容器是否支持 DocObjects。 默认情况下，`GetDocObjectServer`返回**NULL**。 必须重写`COleServerDoc::GetDocObjectServer`构造新`CDocObjectServer`对象或你自己，与指向派生的对象`COleServerDoc`容器并将其`IOleDocumentSite`作为构造函数的参数的接口。  
  
##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView  
 调用此函数可显示 DocObject 视图。  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>返回值  
 返回错误或警告值。 默认情况下，将返回**NOERROR**成功; 否则为如果**E_FAIL**。  
  
### <a name="remarks"></a>备注  
 此函数创建的就地框架窗口、 绘制视图中的滚动条、 设置的菜单的服务器使用其容器共享、 添加帧控件、 设置活动的对象，则最后显示的就地框架窗口和将焦点设置。  
  
##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState  
 重写此函数可还原的 DocObject 视图状态。  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 *ar*  
 A`CArchive`从中序列化的视图状态的对象。  
  
### <a name="remarks"></a>备注  
 正在为其实例化后首次显示视图时，调用此函数。 `OnApplyViewState` 指示要重新初始化自身根据中的数据的视图`CArchive`以前保存的对象[OnSaveViewState](#onsaveviewstate)。 视图必须验证中的数据`CArchive`对象，因为容器不会尝试解释以任何方式的视图状态数据。  
  
 你可以使用`OnSaveViewState`来存储持久性信息特定于你的视图状态。 如果你重写`OnSaveViewState`存储信息，你将想要重写`OnApplyViewState`读取该信息并将其应用于您的视图中，新激活时。  
  
##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState  
 重写此函数可保存 DocObject 视图有关的额外状态信息。  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 *ar*  
 A`CArchive`对象的视图状态序列化。  
  
### <a name="remarks"></a>备注  
 你的状态可能包含属性，例如视图类型、 缩放系数、 插入和选择点和等等。 容器通常在停用视图之前调用此函数。 更高版本可以通过还原的已保存的状态[OnApplyViewState](#onapplyviewstate)。  
  
 你可以使用`OnSaveViewState`来存储持久性信息特定于你的视图状态。 如果你重写`OnSaveViewState`存储信息，你将想要重写`OnApplyViewState`读取该信息并将其应用于您的视图中，新激活时。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocObjectServerItem 类](../../mfc/reference/cdocobjectserveritem-class.md)
