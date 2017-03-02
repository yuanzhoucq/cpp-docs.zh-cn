---
title: "CDocObjectServerItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
dev_langs:
- C++
helpviewer_keywords:
- document object server
- CDocObjectServerItem class
- servers [C++], ActiveX documents
- docobject server
- servers [C++], doc objects
- ActiveX documents [C++], document server
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
caps.latest.revision: 22
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
ms.openlocfilehash: 06cf873512fbf43b729d9a70f185582a4e48cafc
ms.lasthandoff: 02/24/2017

---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 类
实现特别针对 DocObject 服务器的 OLE 服务器谓词。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|构造 `CDocObjectServerItem` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|检索指向包含该项目的文档。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|如果框架试图隐藏 DocObject 项，将引发异常。|  
|[CDocObjectServerItem::OnShow](#onshow)|由框架调用以使 DocObject 项处于就地活动状态。 如果此项不是 DocObject，调用[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|  
  
## <a name="remarks"></a>备注  
 `CDocObjectServerItem`定义可重写成员函数︰ [į](#onhide)， [OnOpen](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd)，和[OnShow](#onshow)。  
  
 若要使用`CDocObjectServerItem`，确保[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)中重写您`COleServerDoc`的派生的类返回一个新`CDocObjectServerItem`对象。 如果需要更改您的项目中的任何功能，您可以创建您自己的新实例`CDocObjectServerItem`的派生类。  
  
 DocObjects 的进一步信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 参考*。 另请参阅[Internet 前几个步骤︰ 活动文档](../../mfc/active-documents-on-the-internet.md)和[活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxdocob.h  
  
##  <a name="a-namecdocobjectserveritema--cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem  
 构造 `CDocObjectServerItem` 对象。  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 `pServerDoc`  
 指向将包含新的 DocObject 项目的文档的指针。  
  
 `bAutoDelete`  
 指示链接到该发布时是否可以删除该对象。 将参数设置为**FALSE**如果`CDocObjectServerItem`对象是文档的数据的组成部分。 将其设置为**TRUE**如果对象是用来标识在可以删除由框架的文档的数据中的范围的辅助结构。  
  
##  <a name="a-namegetdocumenta--cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument  
 检索指向包含该项目的文档。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档的指针**NULL**如果该项不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 这将允许访问服务器文档作为参数传递到[CDocObjectServerItem](#cdocobjectserveritem)构造函数。  
  
##  <a name="a-nameonhidea--cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide  
 由框架表示隐藏该项调用。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>备注  
 如果该项是 DocObject，默认实现将引发异常。 不能隐藏活动 DocObject 项，因为它采用整个视图。 您必须先停用 DocObject 项以使其消失。 如果此项不是 DocObject，默认实现调用[COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。  
  
##  <a name="a-nameonshowa--cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow  
 由框架调用以指示服务器应用程序，以便 DocObject 项处于就地活动状态。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>备注  
 如果此项不是 DocObject，默认实现调用[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果您想要执行特殊处理打开 DocObject 项时，重写此函数。  
  
## <a name="see-also"></a>另请参阅  
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer 类](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem 类](../../mfc/reference/coledocobjectitem-class.md)

