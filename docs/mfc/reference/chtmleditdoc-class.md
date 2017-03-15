---
title: "CHtmlEditDoc 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditDoc
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditDoc class
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
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
ms.openlocfilehash: 1d9651c5009fd8f4c742c6b9bf08e32bd67c7d30
ms.lasthandoff: 02/24/2017

---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc 类
与[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)，提供了 MFC 文档视图体系结构的上下文中的 web 浏览器编辑平台功能。  
  
## <a name="syntax"></a>语法  
  
```  
class AFX_NOVTABLE CHtmlEditDoc : public CDocument  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|构造 `CHtmlEditDoc` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CHtmlEditDoc::GetView](#getview)|检索`CHtmlEditView`对象附加到此文档。|  
|[CHtmlEditDoc::IsModified](#ismodified)|返回关联的视图 WebBrowser 控件是否包含已由用户修改的文档。|  
|[CHtmlEditDoc::OpenURL](#openurl)|打开一个 URL。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 `CHtmlEditDoc`  
  
## <a name="requirements"></a>要求  
 **标头：** afxhtml.h  
  
##  <a name="a-namechtmleditdoca--chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc  
 构造**CHtmlEditDoc**对象。  
  
```  
CHtmlEditDoc();
```  
  
##  <a name="a-namegetviewa--chtmleditdocgetview"></a><a name="getview"></a>CHtmlEditDoc::GetView  
 检索[CHtmlEditView](../../mfc/reference/chtmleditview-class.md)对象附加到此文档。  
  
```  
virtual CHtmlEditView* GetView() const;  
```  
  
### <a name="return-value"></a>返回值  
 将指针返回到文档的**CHtmlEditView**对象。  
  
##  <a name="a-nameismodifieda--chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc::IsModified  
 返回关联的视图 WebBrowser 控件是否包含已由用户修改的文档。  
  
```  
virtual BOOL IsModified();
```  
  
##  <a name="a-nameopenurla--chtmleditdocopenurl"></a><a name="openurl"></a>CHtmlEditDoc::OpenURL  
 打开一个 URL。  
  
```  
virtual BOOL OpenURL(LPCTSTR lpszURL);
```  
  
### <a name="parameters"></a>参数  
 `lpszURL`  
 要打开的 URL。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
## <a name="see-also"></a>另请参阅  
 [HTMLEdit 示例](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


