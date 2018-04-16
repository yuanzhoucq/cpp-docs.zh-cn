---
title: "CDocItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs:
- C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8a4987554965674612eaf8d9aa78c659f7f28b75
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdocitem-class"></a>CDocItem 类
属于文档数据一部分的文档项的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CDocItem : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDocItem::GetDocument](#getdocument)|返回包含项的文档。|  
|[CDocItem::IsBlank](#isblank)|确定项目是否包含任何信息。|  
  
## <a name="remarks"></a>备注  
 `CDocItem`对象用于表示在客户端和服务器文档中的 OLE 项。  
  
 有关详细信息，请参阅文章[容器： 实现容器](../../mfc/containers-implementing-a-container.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxole.h  
  
##  <a name="getdocument"></a>CDocItem::GetDocument  
 调用此函数可获取包含项的文档。  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向包含的项; 文档的指针**NULL**，如果项不是文档的一部分。  
  
### <a name="remarks"></a>备注  
 此函数在派生类中重写[COleClientItem](../../mfc/reference/coleclientitem-class.md)和[COleServerItem](../../mfc/reference/coleserveritem-class.md)，返回一个指向为[COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)，或[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)对象。  
  
##  <a name="isblank"></a>CDocItem::IsBlank  
 默认序列化时，由框架调用。  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果项不包含任何信息; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，`CDocItem`对象不为空。 [COleClientItem](../../mfc/reference/coleclientitem-class.md)对象有时是空白因为它们直接从派生`CDocItem`。 但是， [COleServerItem](../../mfc/reference/coleserveritem-class.md)对象始终为空白。 默认情况下，OLE 应用程序包含`COleClientItem`没有 x 或 y 的对象序列化扩展盘区。 这通过返回**TRUE**的重写`IsBlank`项时出现任何 x 或 y 扩展盘区。  
  
 如果你想要在序列化过程中执行其他操作，重写此函数。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDocument 类](../../mfc/reference/coledocument-class.md)   
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)
