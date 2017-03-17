---
title: "CMFCRibbonCustomizePropertyPage 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
dev_langs:
- C++
helpviewer_keywords:
- ~CMFCRibbonCustomizePropertyPage destructor
- CMFCRibbonCustomizePropertyPage class, destructor
- GetThisClass method
- CreateObject method
- CMFCRibbonCustomizePropertyPage class
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
caps.latest.revision: 26
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 83323142441de13140383152a32122bf1644003f
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage 类
实现的自定义页**自定义**基于功能区的应用程序中的对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|构造 `CMFCRibbonCustomizePropertyPage` 对象。|  
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|描述|  
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|添加到自定义类别**命令**组合框。|  
|`CMFCRibbonCustomizePropertyPage::CreateObject`|由框架用于创建此类类型的动态实例。|  
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|当用户单击由系统调用**确定**上**自定义**对话框。|  
  
## <a name="remarks"></a>备注  
 如果您想要添加到自定义命令**自定义**对话框中，您必须处理 AFX_WM_ON_RIBBON_CUSTOMIZE 消息。 消息处理程序，在实例化`CMFCRibbonCustomizePropertyPage`在堆栈上的对象。 创建自定义命令的列表，然后调用`AddCustomCategory`要添加到新页面**自定义**对话框。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造`CMFCRibbonCustomizePropertyPage`对象并将添加一个自定义类别。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&22;](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)  
  
 [CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribboncustomizedialog.h  
  
##  <a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory  
 添加到自定义类别**命令**组合框。  
  
```  
void AddCustomCategory(
    LPCTSTR lpszName,  
    const CList<UINT, UINT>& lstIDS);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `lpszName`|指定自定义的类别名称。|  
|[in] `lstIDS`|包含功能区命令 Id 的自定义的类别中显示。|  
  
### <a name="remarks"></a>备注  
 此方法将添加一个名为类别`lpszName`到**命令**组合框。 当用户选择该类别时，这些命令中指定`lstIDS`命令列表中显示。  
  
##  <a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage  
 构造 `CMFCRibbonCustomizePropertyPage` 对象。  
  
```  
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pRibbonBar`  
 指向要为其功能区控件的选项以自定义。  
  
##  <a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK  
 用户单击时，系统 Calleld**确定**上**自定义**对话框。  
  
```  
virtual void OnOK();
```  
  
### <a name="remarks"></a>备注  
 默认实现将应用中所选的选项**自定义**到快速访问工具栏的对话框。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

