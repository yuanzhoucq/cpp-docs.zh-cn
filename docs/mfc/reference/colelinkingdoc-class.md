---
title: COleLinkingDoc 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
dev_langs:
- C++
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 843c79d9b3c7ffeb0ceef7338132048ac51d52ef
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039968"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc 类
支持链接到所包含的嵌入项的 OLE 容器文档的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|构造 `COleLinkingDoc` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinkingDoc::Register](#register)|使用 OLE 系统 Dll 注册文档。|  
|[COleLinkingDoc::Revoke](#revoke)|撤消文档的注册。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|查找指定的嵌入的项。|  
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|查找指定的链接的项。|  
  
## <a name="remarks"></a>备注  
 容器支持的应用程序链接到嵌入项称为"链接容器"。 [OCLIENT](../../visual-cpp-samples.md)示例应用程序链接容器的示例。  
  
 当链接的项的源是另一个文档，必须在要编辑嵌入项的顺序加载包含文档中嵌入的项。 因此，链接容器必须能够由另一个容器应用程序启动，当用户想要编辑某个链接的项的源。 你的应用程序还必须使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)类，以便它可以创建文档时以编程方式启动。  
  
 若要使容器链接容器，派生您的文档类从`COleLinkingDoc`而不是[COleDocument](../../mfc/reference/coledocument-class.md)。 与任何其他 OLE 容器，则必须设计您的类用于存储应用程序的本机数据以及嵌入项或者链接项。 此外，你必须设计用于存储你的本机数据的数据结构。 如果你定义`CDocItem`-派生类，为你的应用程序的本机数据，你可以使用由定义的接口`COleDocument`来存储你的本机数据以及 OLE 数据。  
  
 若要允许应用程序由另一个容器以编程方式启动，声明`COleTemplateServer`对象作为你的应用程序的成员`CWinApp`-派生类：  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]  
  
 在`InitInstance`成员函数你`CWinApp`-派生类，创建的文档模板并指定你`COleLinkingDoc`-派生文档类的类：  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]  
  
 连接你`COleTemplateServer`到通过调用对象的文档模板对象`ConnectTemplate`成员函数，并注册所有类都对象通过调用 OLE 系统`COleTemplateServer::RegisterAll`:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]  
  
 有关示例`CWinApp`-派生类定义和`InitInstance`函数中，请参阅 OCLIENT。H 和 OCLIENT。在 MFC 示例 CPP [OCLIENT](../../visual-cpp-samples.md)。  
  
 有关详细信息使用`COleLinkingDoc`，请参阅文章[容器： 实现容器](../../mfc/containers-implementing-a-container.md)和[容器： 高级功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc  
 构造`COleLinkingDoc`对象而不从与 OLE 系统 Dll 之间的通信。  
  
```  
COleLinkingDoc();
```  
  
### <a name="remarks"></a>备注  
 必须调用`Register`成员函数，以通知 OLE 文档处于打开状态。  
  
##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem  
 由框架调用以确定文档是否包含具有指定名称的嵌入的 OLE 项。  
  
```  
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 *lpszItemName*  
 指向嵌入 OLE 项请求的名称。  
  
### <a name="return-value"></a>返回值  
 指向指定的项;**NULL**如果未找到该项目。  
  
### <a name="remarks"></a>备注  
 默认实现将搜索具有指定名称 （名称比较不区分大小写） 的项的嵌入项的列表。 如果你有自己的存储或命名嵌入的 OLE 项的方法，重写此函数。  
  
##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem  
 由框架调用以检查文档是否包含具有指定名称的链接的服务器项。  
  
```  
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 *lpszItemName*  
 指向链接 OLE 项请求的名称。  
  
### <a name="return-value"></a>返回值  
 指向指定的项;**NULL**如果未找到该项目。  
  
### <a name="remarks"></a>备注  
 默认值`COleLinkingDoc`实现始终返回**NULL**。 此函数是在派生类中的重写`COleServerDoc`搜索具有指定名称 （名称比较不区分大小写） 链接的项的 OLE 服务器项的列表。 如果已实现您自己的存储或检索链接的服务器项的方法，重写此函数。  
  
##  <a name="register"></a>  COleLinkingDoc::Register  
 告知 OLE 系统 Dll，文档已打开。  
  
```  
BOOL Register(
    COleObjectFactory* pFactory,  
    LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 *pFactory*  
 指向 OLE 工厂对象 (可以是**NULL**)。  
  
 *lpszPathName*  
 指向容器文档的完全限定路径。  
  
### <a name="return-value"></a>返回值  
 如果成功注册文档; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数创建或打开要向 OLE 系统 Dll 注册文档的命名的文件时。 没有无需调用此函数，如果文档表示嵌入的项。  
  
 如果你使用`COleTemplateServer`中你的应用程序，`Register`为您通过调用`COleLinkingDoc`的实现`OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
##  <a name="revoke"></a>  COleLinkingDoc::Revoke  
 该文档不再是打开通知 OLE 系统 Dll。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 调用此函数可撤消向 OLE 系统 Dll 的文档的注册。  
  
 关闭的命名的文件时，应调用此函数，但通常不需要直接调用它。 `Revoke` 为您通过调用`COleLinkingDoc`的实现`OnCloseDocument`， `OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDocument 类](../../mfc/reference/coledocument-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)
