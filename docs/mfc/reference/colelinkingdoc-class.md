---
title: "COleLinkingDoc 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- OLE containers, client items
- COleLinkingDoc class
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
caps.latest.revision: 24
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
ms.openlocfilehash: acdfde1413d5ff93efc63dbbf211881f71cf624e
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc 类
支持链接到所包含的嵌入项的 OLE 容器文档的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleLinkingDoc : public COleDocument  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|构造 `COleLinkingDoc` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleLinkingDoc::Register](#register)|使用 OLE 系统 Dll 注册文档。|  
|[COleLinkingDoc::Revoke](#revoke)|撤消文档的注册。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|查找指定的嵌入的项。|  
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|查找指定的链接的项。|  
  
## <a name="remarks"></a>备注  
 容器支持的应用程序将链接到嵌入项称为"链接容器"。 [OCLIENT](../../visual-cpp-samples.md)示例应用程序是链接容器的示例。  
  
 链接的项的源时另一个文档，必须在要编辑嵌入项的顺序加载包含文档中嵌入的项。 出于此原因，链接容器必须能够在用户想要编辑链接的项的源时由另一个容器应用程序启动。 您的应用程序还必须使用[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)类，以便它可以创建文档时以编程方式启动。  
  
 若要使您的容器链接容器，派生文档类从`COleLinkingDoc`而不是[COleDocument](../../mfc/reference/coledocument-class.md)。 与任何其他 OLE 容器，必须设计您的类用于存储应用程序的本机数据以及嵌入或链接的项。 此外，您必须设计用于存储您的本机数据的数据结构。 如果您定义`CDocItem`的派生类，您的应用程序的本机数据，您可以使用所定义接口`COleDocument`来存储您的本机数据以及 OLE 数据。  
  
 若要允许应用程序以编程方式启动的另一个容器，声明`COleTemplateServer`对象作为应用程序的成员`CWinApp`的派生类︰  
  
 [!code-cpp[NVC_MFCOleContainer 第&23;](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]  
  
 在`InitInstance`成员函数的您`CWinApp`-派生类中，创建文档模板，并指定您`COleLinkingDoc`-派生文档类的类︰  
  
 [!code-cpp[NVC_MFCOleContainer #&24;](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]  
  
 连接您`COleTemplateServer`到通过调用对象的文档模板对象`ConnectTemplate`成员函数，并注册所有类都对象向 OLE 系统通过调用**coletemplateserver:: Registerall**:  
  
 [!code-cpp[NVC_MFCOleContainer #&25;](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]  
  
 有关示例`CWinApp`的派生类定义和`InitInstance`函数中，请参阅 OCLIENT。H 和 OCLIENT。在 MFC 示例 CPP [OCLIENT](../../visual-cpp-samples.md)。  
  
 有关详细信息使用`COleLinkingDoc`，请参阅文章[容器︰ 实现容器](../../mfc/containers-implementing-a-container.md)和[容器︰ 高级功能](../../mfc/containers-advanced-features.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="colelinkingdoc"></a>COleLinkingDoc::COleLinkingDoc  
 构造`COleLinkingDoc`对象而无需开始与 OLE 系统 Dll 之间的通信。  
  
```  
COleLinkingDoc();
```  
  
### <a name="remarks"></a>备注  
 必须调用`Register`成员函数，以通知 OLE 文档处于打开状态。  
  
##  <a name="onfindembeddeditem"></a>COleLinkingDoc::OnFindEmbeddedItem  
 由框架来确定文档是否包含具有指定名称嵌入的 OLE 项调用。  
  
```  
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 `lpszItemName`  
 为嵌入的 OLE 项请求的名称的指针。  
  
### <a name="return-value"></a>返回值  
 一个指向指定的项;**NULL**如果找不到该项目。  
  
### <a name="remarks"></a>备注  
 默认实现将搜索具有指定名称 （名称比较不区分大小写） 的项的嵌入项的列表。 如果您有自己的存储或命名嵌入的 OLE 项的方法，重写此函数。  
  
##  <a name="ongetlinkeditem"></a>COleLinkingDoc::OnGetLinkedItem  
 由框架来检查文档是否包含具有指定名称的链接的服务器项调用。  
  
```  
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>参数  
 `lpszItemName`  
 链接 OLE 项请求的名称的指针。  
  
### <a name="return-value"></a>返回值  
 一个指向指定的项;**NULL**如果找不到该项目。  
  
### <a name="remarks"></a>备注  
 默认值`COleLinkingDoc`实现始终返回**NULL**。 此函数是在派生类中的重写`COleServerDoc`搜索具有指定名称 （名称比较不区分大小写） 链接的项的 OLE 服务器项的列表。 如果你已实现了自己的存储或检索链接的服务器项的方法，重写此函数。  
  
##  <a name="register"></a>COleLinkingDoc::Register  
 告知 OLE 系统 Dll 此文档已打开。  
  
```  
BOOL Register(
    COleObjectFactory* pFactory,  
    LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>参数  
 *pFactory*  
 对 OLE 工厂对象的指针 (可以是**NULL**)。  
  
 `lpszPathName`  
 指针，指向容器文档的完全限定路径。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功注册文档;否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数时创建或打开一个命名的文件，以向 OLE 系统 Dll 注册文档。 没有无需调用此函数，如果文档表示嵌入的项。  
  
 如果您使用`COleTemplateServer`应用程序中`Register`为您通过调用`COleLinkingDoc`的实现`OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
##  <a name="revoke"></a>COleLinkingDoc::Revoke  
 告知 OLE 系统 Dll 文档不再处于打开状态。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 调用此函数可撤消文档的注册向 OLE 系统 Dll。  
  
 关闭的命名的文件时，应调用此函数，但通常不需要直接调用。 `Revoke`为您通过调用`COleLinkingDoc`的实现`OnCloseDocument`， `OnNewDocument`， `OnOpenDocument`，和`OnSaveDocument`。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [COleDocument 类](../../mfc/reference/coledocument-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocTemplate 类](../../mfc/reference/cdoctemplate-class.md)

