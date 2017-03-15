---
title: "CWinFormsView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- CWinFormsView class
- Windows Forms [C++], MFC support
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
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
ms.sourcegitcommit: 6c49d711da747e4c6cbad0f883d93196b6a98057
ms.openlocfilehash: 7aadcc1aa887cb6be1ddbb8f3797c4a9e1af5b6a
ms.lasthandoff: 02/24/2017

---
# <a name="cwinformsview-class"></a>CWinFormsView 类
提供用于将 Windows 窗体控件作为 MFC 视图承载的一般功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CWinFormsView : public CView;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsView::CWinFormsView](#cwinformsview)|构造 `CWinFormsView` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWinFormsView::GetControl](#getcontrol)|检索指向 Windows 窗体控件的指针。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称||  
|----------|-|  
|[CWinFormsView::operator 控件 ^](#operator_control)|将一种类型强制转换为指向 Windows 窗体控件的指针。|  
  
## <a name="remarks"></a>备注  
 MFC 使用`CWinFormsView`类来承载 MFC 视图中的.NET Framework Windows 窗体控件。 控件是本机的视图的子级且占用 MFC 视图的整个工作区。 结果是类似于`CFormView`视图，使您能够充分利用 Windows 窗体设计器和运行时，以创建丰富的基于窗体的视图。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
> [!NOTE]
>  MFC Windows 窗体集成可以正常工作只能在动态与 MFC 链接的项目中 （在其中定义 AFXDLL 个项目）。  
  
> [!NOTE]
>  CWinFormsView 不支持 MFC 拆分器窗口 ( [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md))。 当前仅 Windows 窗体拆分器支持控件。  
  
## <a name="requirements"></a>要求  
 **标头︰** afxwinforms.h  
  
##  <a name="a-namecwinformsviewa--cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 构造 `CWinFormsView` 对象。  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>参数  
 `pManagedViewType`  
 指向 Windows 窗体用户控件的数据类型的指针。   
  
### <a name="example"></a>示例  
 在下面的示例中，`CUserView`类继承自`CWinFormsView`，并将传递的一种`UserControl1`到`CWinFormsView`构造函数。 `UserControl1`是 ControlLibrary1.dll 中的自定义控件。  
  
 [!code-cpp[NVC_MFC_Managed #&1;](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed #&2;](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="a-namegetcontrola--cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinFormsView::GetControl  
 检索指向 Windows 窗体控件的指针。  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`System.Windows.Forms.Control`对象。  
  
### <a name="remarks"></a>备注  
 有关如何使用 Windows 窗体的示例，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="a-nameoperatorcontrola--cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinFormsView::operator 控件 ^  
 将一种类型强制转换为指向 Windows 窗体控件的指针。  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>备注  
 此运算符可用于传递`CWinFormsView`到函数中接受指向类型<xref:System.Windows.Forms.Control>。</xref:System.Windows.Forms.Control>的 Windows 窗体控件的视图  
  
### <a name="example"></a>示例  
  请参阅[CWinFormsView::GetControl](#getcontrol)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl 类](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog 类](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)

