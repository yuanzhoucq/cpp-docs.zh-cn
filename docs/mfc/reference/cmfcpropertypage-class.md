---
title: "CMFCPropertyPage 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
dev_langs: C++
helpviewer_keywords: CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d11f9e4849a0c632e6a63d794dc294fa504d196a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage 类
`CMFCPropertyPage`类支持的弹出菜单显示在属性页上。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|构造 `CMFCPropertyPage` 对象。|  
|`CMFCPropertyPage::~CMFCPropertyPage`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCPropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCPropertyPage::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|`CMFCPropertyPage::OnSetActive`|由用户选择和成为活动页面页时，将由框架调用此成员函数。 (重写[cpropertypage:: Onsetactive](../../mfc/reference/cpropertypage-class.md#onsetactive)。)|  
|`CMFCPropertyPage::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 有关详细信息和方法语法，请参阅[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。 （重写 `CPropertyPage::PreTranslateMessage`。）|  
  
## <a name="remarks"></a>备注  
 `CMFCPropertyPage`类表示属性表，也称为选项卡对话框中的各个页。  
  
 使用`CMFCPropertyPage`类连同[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)类。 若要使用菜单在属性页上，将出现的所有`CPropertyPage`类，该类具有`CMFCPropertyPage`类。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxpropertypage.h  
  
##  <a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage  
 构造 `CMFCPropertyPage` 对象。  
  
```  
CMFCPropertyPage(
    UINT nIDTemplate,  
    UINT nIDCaption=0);

 
CMFCPropertyPage(
    LPCTSTR lpszTemplateName,  
    UINT nIDCaption=0);
```  
  
### <a name="parameters"></a>参数  
 `nIDTemplate`  
 此页的模板的资源 ID。  
  
 `nIDCaption`  
 资源 ID 的标签将在此页的选项卡。 如果为 0，名称来自此页对话框模板中。 默认值为 0。  
  
 `lpszTemplateName`  
 指向此页的模板名称。 不能为 `NULL`。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 有关构造函数参数的详细信息，请参阅[CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage)。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertySheet 类](../../mfc/reference/cmfcpropertysheet-class.md)
