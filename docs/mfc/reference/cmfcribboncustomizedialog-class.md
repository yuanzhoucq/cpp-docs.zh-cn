---
title: "CMFCRibbonCustomizeDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonCustomizeDialog class
- CMFCRibbonCustomizeDialog class, destructor
- ~CMFCRibbonCustomizeDialog destructor
- GetThisClass method
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d27247f89901adad1778313cdde6fe206a569f0d
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog 类
显示功能区**自定义**页。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|构造 `CMFCRibbonCustomizeDialog` 对象。|  
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|`CMFCRibbonCustomizeDialog::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
  
## <a name="remarks"></a>备注  
 如果不处理 AFX_WM_ON_RIBBON_CUSTOMIZE 消息，或者如果您从消息处理程序返回 0，MFC 自动实例化此类。  
  
 如果想要使用此类应用程序中显示功能区**自定义**对话框框中，只是其实例化并调用`DoModal`方法。  
  
 由于此类派生自[CMFCPropertySheet 类](../../mfc/reference/cmfcpropertysheet-class.md)，您可以通过添加自定义页`CMFCPropertySheet`API。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)  
  
 [CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribboncustomizedialog.h  
  
##  <a name="cmfcribboncustomizedialog"></a>CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog  
 构造 `CMFCRibbonCustomizeDialog` 对象。  
  
```  
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,  
    CMFCRibbonBar* pRibbon);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndParent`  
 指向父窗口 （通常主框架） 的指针。  
  
 [in] `pRibbon`  
 一个指向`CMFCRibbonBar`那就是进行自定义。  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCRibbonCustomizeDialog`对象。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&18;](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]  
  
### <a name="remarks"></a>备注  
 构造函数实例化[CMFCRibbonCustomizePropertyPage 类](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)对象，并将其添加到属性页的集合。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

