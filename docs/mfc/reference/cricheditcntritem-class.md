---
title: "CRichEditCntrItem 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCntrItem class
- OLE items, in rich edit views
- rich edit controls, using
- rich edit controls, OLE items
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
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
ms.openlocfilehash: b29c7c3b80d24ef9ddb94e09c6b5c7bf2444bb4f
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem 类
与[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)，提供 MFC 文档视图体系结构的上下文中 rich edit 控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CRichEditCntrItem : public COleClientItem  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|构造 `CRichEditCntrItem` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|将项激活为另一种类型。|  
  
## <a name="remarks"></a>备注  
 "格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本可以为分配字符和段落格式设置，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。  
  
 `CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`保留视图中的 OLE 客户端项目的列表。 `CRichEditCntrItem` 提供对 OLE 客户端项的容器端访问。  
  
 此 Windows 公共控件 (并因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 是仅供程序在运行 Windows 95/98 和 Windows NT 版本 3.51 及更高版本。  
  
 在 MFC 应用程序中使用格式文本编辑容器项的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `CRichEditCntrItem`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrich.h  
  
##  <a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem  
 调用此函数可创建`CRichEditCntrItem`对象，并将其添加到容器文档。  
  
```  
CRichEditCntrItem(
    REOBJECT* preo = NULL,  
    CRichEditDoc* pContainer = NULL);
```  
  
### <a name="parameters"></a>参数  
 *preo*  
 指向[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)结构描述一个 OLE 项。 新`CRichEditCntrItem`对象构造此 OLE 项的周围。 如果*preo*是**NULL**，客户端项为空。  
  
 `pContainer`  
 指向将包含此项的容器文档的指针。 如果`pContainer`是**NULL**，必须显式调用[COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem)若要将此客户端项目添加到文档。  
  
### <a name="remarks"></a>备注  
 此函数不执行任何 OLE 初始化。  
  
 有关详细信息，请参阅[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject  
 调用此函数可同步设备方面， [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)，此**CRichEditCntrltem**到指定的*reo*。  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>参数  
 *reo*  
 引用[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)结构描述一个 OLE 项。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例写字板](../../visual-cpp-samples.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc 类](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView 类](../../mfc/reference/cricheditview-class.md)

