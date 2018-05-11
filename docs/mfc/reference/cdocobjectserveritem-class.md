---
title: CDocObjectServerItem 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6f990a00fb96195a54ee7ed6906068985b052f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem 类
实现特别针对 DocObject 服务器的 OLE 服务器谓词。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocObjectServerItem : public COleServerItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|构造 `CDocObjectServerItem` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::GetDocument](#getdocument)|检索指向包含项的文档。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocObjectServerItem::OnHide](#onhide)|如果框架试图隐藏 DocObject 项，将引发异常。|  
|[CDocObjectServerItem::OnShow](#onshow)|由框架，以使 DocObject 项就地活动状态。 如果该项不是 DocObject，调用[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)。|  
  
## <a name="remarks"></a>备注  
 `CDocObjectServerItem` 定义可重写成员函数： [OnHide](#onhide)， [OnOpen](http://msdn.microsoft.com/en-us/7a9b1363-6ad8-4732-9959-4e35c07644fd)，和[OnShow](#onshow)。  
  
 若要使用`CDocObjectServerItem`，确保[OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)中重写你`COleServerDoc`-派生的类返回一个新`CDocObjectServerItem`对象。 如果你需要更改你的项目中任何功能，你可以创建你自己的新实例`CDocObjectServerItem`-派生类。  
  
 DocObjects 的进一步信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[COleCmdUI](../../mfc/reference/colecmdui-class.md)中*MFC 参考*。 另请参阅[Internet 前几个步骤： 活动文档](../../mfc/active-documents-on-the-internet.md)和[活动文档](../../mfc/active-documents-on-the-internet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleServerItem](../../mfc/reference/coleserveritem-class.md)  
  
 `CDocObjectServerItem`  
  
## <a name="requirements"></a>要求  
 **标头：** afxdocob.h  
  
##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem  
 构造 `CDocObjectServerItem` 对象。  
  
```  
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>参数  
 `pServerDoc`  
 指向将包含新的 DocObject 项的文档的指针。  
  
 `bAutoDelete`  
 指示链接到该发布时，是否可以删除对象。 将参数设置为**FALSE**如果`CDocObjectServerItem`对象是不可或缺的组成部分文档的数据。 将其设置为**TRUE**如果对象是用于标识可以由框架删除的文档的数据中的范围的辅助结构。  
  
##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument  
 检索指向包含项的文档。  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档的指针**NULL**如果该项不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 这将允许到作为参数传递的服务器文档的访问[CDocObjectServerItem](#cdocobjectserveritem)构造函数。  
  
##  <a name="onhide"></a>  CDocObjectServerItem::OnHide  
 由框架调用以隐藏项。  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>备注  
 如果该项是 DocObject，默认实现将引发异常。 不能隐藏活动 DocObject 项，因为它采用整个视图。 你必须先停用 DocObject 项以将其隐藏。 如果该项不是 DocObject，默认实现调用[COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)。  
  
##  <a name="onshow"></a>  CDocObjectServerItem::OnShow  
 由框架，以指示服务器应用程序发出 DocObject 项处于就地活动状态。  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>备注  
 如果该项不是 DocObject，默认实现调用[COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)。 如果你想要执行特殊处理打开 DocObject 项时，重写此函数。  
  
## <a name="see-also"></a>请参阅  
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDocObjectServer 类](../../mfc/reference/cdocobjectserver-class.md)   
 [COleDocObjectItem 类](../../mfc/reference/coledocobjectitem-class.md)
