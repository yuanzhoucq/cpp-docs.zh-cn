---
title: "CFormView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
dev_langs:
- C++
helpviewer_keywords:
- views, containing controls
- CFormView class
- form views
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
caps.latest.revision: 23
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 82b38b04aa3cf2368d41ee20847c952c3082d4e4
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cformview-class"></a>CFormView 类
用于窗体视图的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CFormView : public CScrollView  
```  
  
## <a name="members"></a>成员  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFormView::CFormView](#cformview)|构造 `CFormView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|用于在初始化期间同步。|  
  
## <a name="remarks"></a>备注  
 窗体视图是实质上是一个包含控件的视图。 这些控件基于对话框模板资源进行布局。 如果你想要你的应用程序具有窗体，请使用 `CFormView`。 这些视图支持滚动，根据需要使用[CScrollView](../../mfc/reference/cscrollview-class.md)功能。  
  
 如果要[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)，您可以基于其视图类`CFormView`，使其基于窗体的应用程序。  
  
 您还可以插入新[表单主题](../../mfc/form-views-mfc.md)到基于文档视图的应用程序。 即使你的应用程序最初不支持窗体，当你插入一个新窗体时 Visual C++ 将添加这一支持。  
  
 MFC 应用程序向导和“添加类”命令是创建基于窗体的应用程序的首选的方法。 如果您需要创建一个基于窗体应用程序而不使用这些方法，请参阅[创建基于窗体的应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 `CFormView`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="cformview"></a>CFormView::CFormView  
 构造 `CFormView` 对象。  
  
```  
CFormView(LPCTSTR lpszTemplateName);  
CFormView(UINT nIDTemplate);
```  
  
### <a name="parameters"></a>参数  
 `lpszTemplateName`  
 包含以 null 结尾的字符串是对话框模板资源的名称。  
  
 `nIDTemplate`  
 包含对话框模板资源的 ID 号。  
  
### <a name="remarks"></a>备注  
 当创建类型的对象派生自`CFormView`，调用的构造函数来创建视图对象并标识该视图所基于的对话框资源之一。 按名称 (pass 字符串作为参数的构造函数) 或由其 ID (pass 作为参数的无符号整数)，您可以标识该资源。  
  
 窗体视图窗口和子控件之前将不创建`CWnd::Create`调用。 `CWnd::Create`由框架作为文档和视图创建过程中，这由文档模板的一部分调用。  
  
> [!NOTE]
>  在派生的类*必须*提供其自己的构造函数。 在构造函数中，调用构造函数中， `CFormView::CFormView`、 具有资源名称或 ID 作为参数前面的类概述中所示。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&90;](../../mfc/codesnippet/cpp/cformview-class_1.h)]  
  
 [!code-cpp[NVC_MFCDocView #&91;](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]  
  
##  <a name="isinitdlgcompleted"></a>CFormView::IsInitDlgCompleted  
 由 MFC 用于确保初始化完成后才会执行其他操作。  
  
```  
BOOL IsInitDlgCompleted() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果已完成了此对话框的初始化函数，则为 true。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 SNAPVW](../../visual-cpp-samples.md)   
 [MFC 示例 VIEWEX](../../visual-cpp-samples.md)   
 [CScrollView 类](../../mfc/reference/cscrollview-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDialog 类](../../mfc/reference/cdialog-class.md)   
 [CScrollView 类](../../mfc/reference/cscrollview-class.md)

