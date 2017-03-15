---
title: "CDocItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocItem
dev_langs:
- C++
helpviewer_keywords:
- items, document
- document items
- server documents, document items
- CDocItem class
- container document items
- client document items
- OLE documents, items
- server documents
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
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
ms.openlocfilehash: 1ade88aa562180d5c3a6a7afe3fe26943a5d811d
ms.lasthandoff: 02/24/2017

---
# <a name="cdocitem-class"></a>CDocItem 类
属于文档数据一部分的文档项的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDocItem::GetDocument](#getdocument)|返回包含项的文档。|  
|[CDocItem::IsBlank](#isblank)|确定项是否包含任何信息。|  
  
## <a name="remarks"></a>备注  
 `CDocItem`对象用于表示在客户端和服务器文档中的 OLE 项。  
  
 有关详细信息，请参阅文章[容器︰ 实现容器](../../mfc/containers-implementing-a-container.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="a-namegetdocumenta--cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem::GetDocument  
 调用此函数可获取包含项的文档。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档的指针**NULL**，如果该项目不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 在派生类中重写此函数[COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)，返回一个指向任何一个[COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)对象。  
  
##  <a name="a-nameisblanka--cdocitemisblank"></a><a name="isblank"></a>CDocItem::IsBlank  
 默认序列化时由框架调用。  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果该项目不包含任何信息;否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CDocItem`对象是否不为空。 [COleClientItem](../../mfc/reference/coleclientitem-class.md)对象是有时空白因为直接从它们派生`CDocItem`。 但是， [COleServerItem](../../mfc/reference/coleserveritem-class.md)对象始终为空白。 默认情况下，OLE 应用程序包含`COleClientItem`没有 x 或 y 的对象进行序列化扩展盘区。 这通过返回**TRUE**的重写`IsBlank`该项时没有任何 x 或 y 扩展盘区。  
  
 如果您想要在序列化过程中执行其他操作，重写此函数。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDocument 类](../../mfc/reference/coledocument-class.md)   
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)

