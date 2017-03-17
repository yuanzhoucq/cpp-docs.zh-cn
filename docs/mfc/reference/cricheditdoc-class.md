---
title: "CRichEditDoc 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
dev_langs:
- C++
helpviewer_keywords:
- document/view architecture, rich edit controls
- OLE containers, rich edit
- documents, rich edit
- rich edit controls, OLE container
- CRichEditDoc class
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c7233c27c92c6dc689853e1913bb26f0bb5941fa
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditdoc-class"></a>CRichEditDoc 类
与[CRichEditView](../../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)，提供 MFC 文档视图体系结构的上下文中 rich edit 控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CRichEditDoc : public COleServerDoc  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CRichEditDoc::CreateClientItem](#createclientitem)|调用以执行清理操作文档。|  
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|指示流输入和输出是否应包含格式设置信息。|  
|[CRichEditDoc::GetView](#getview)|检索关联[CRichEditView](../../mfc/reference/cricheditview-class.md)对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CRichEditDoc::m_bRTF](#m_brtf)|指示数据流输入/输出是否应包含格式设置。|  
  
## <a name="remarks"></a>备注  
 "格式文本编辑控件"是一个窗口，用户可以输入和编辑文本。 文本可以为分配字符和段落格式设置，并且可以包含嵌入的 OLE 对象。 Rich edit 控件提供用于设置文本格式的编程接口。 但是，应用程序必须实现使用户可进行格式设置操作所需的任何用户界面组件。  
  
 `CRichEditView` 保留文本及其格式特征。 `CRichEditDoc`保留视图中的客户端项目的列表。 `CRichEditCntrItem`提供对 OLE 客户端项的容器端访问。  
  
 此 Windows 公共控件 (并因此[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)和相关类) 是仅供程序在运行 Windows 95/98 和 Windows NT 版本 3.51 及更高版本。  
  
 在 MFC 应用程序中使用格式文本编辑文档的示例，请参阅[写字板](../../visual-cpp-samples.md)示例应用程序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrich.h  
  
##  <a name="createclientitem"></a>CRichEditDoc::CreateClientItem  
 调用此函数可创建`CRichEditCntrItem`对象，并将其添加到此文档。  
  
```  
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;  
```  
  
### <a name="parameters"></a>参数  
 *preo*  
 指向[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)结构描述一个 OLE 项。 新`CRichEditCntrItem`对象构造此 OLE 项的周围。 如果*preo*是**NULL**，新的客户端项为空。  
  
### <a name="return-value"></a>返回值  
 指向新[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)已添加到此文档的对象。  
  
### <a name="remarks"></a>备注  
 此函数不执行任何 OLE 初始化。  
  
 有关详细信息，请参阅[REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat  
 调用此函数可确定文本格式的流式处理格式文本编辑的内容。  
  
```  
int GetStreamFormat() const;  
```  
  
### <a name="return-value"></a>返回值  
 以下标记之一︰  
  
- `SF_TEXT`指示 rich edit 控件不维护的格式设置信息。  
  
- `SF_RTF`指示，rich edit 控件中保存了格式设置信息。  
  
### <a name="remarks"></a>备注  
 返回值取决于[m_bRTF](#m_brtf)数据成员。 此函数将返回`SF_RTF`如果`m_bRTF`是**TRUE**; 否则为`SF_TEXT`。  
  
##  <a name="getview"></a>CRichEditDoc::GetView  
 调用此函数可访问[CRichEditView](../../mfc/reference/cricheditview-class.md)对象与此相关`CRichEditDoc`对象。  
  
```  
virtual CRichEditView* GetView() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向`CRichEditView`与文档关联的对象。  
  
### <a name="remarks"></a>备注  
 中包含的文本和格式设置信息`CRichEditView`对象。 `CRichEditDoc`对象维护的序列化的 OLE 项。 应该只有一个`CRichEditView`为每个`CRichEditDoc`。  
  
##  <a name="m_brtf"></a>CRichEditDoc::m_bRTF  
 当**TRUE**，指示[CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin)和[CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout)应存储段落和字符格式设置特性。  
  
```  
BOOL m_bRTF;  
```  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例写字板](../../visual-cpp-samples.md)   
 [COleServerDoc 类](../../mfc/reference/coleserverdoc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CRichEditView 类](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem 类](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument 类](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl 类](../../mfc/reference/cricheditctrl-class.md)

