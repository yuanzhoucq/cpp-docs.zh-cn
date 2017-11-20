---
title: "CWinFormsView 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs: C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d3551252d04dc97f6e2b4dd13df61edda576744
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
|[CWinFormsView::operator 控件 ^](#operator_control)|将类型强制转换为指向 Windows 窗体控件。|  
  
## <a name="remarks"></a>备注  
 MFC 使用`CWinFormsView`类来承载 MFC 视图中的.NET Framework Windows 窗体控件。 该控件是本机的视图的子级，并占用 MFC 视图的整个工作区。 结果是类似于`CFormView`视图，使您可以利用 Windows 窗体设计器和运行时，以创建丰富的基于窗体的视图。  
  
 有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
> [!NOTE]
>  MFC Windows 窗体集成仅在与 MFC 动态链接的项目中可以正常工作 （在其中定义 AFXDLL 项目）。  
  
> [!NOTE]
>  CWinFormsView 不支持 MFC 拆分器窗口 ( [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md))。 当前仅 Windows 窗体拆分器支持控制。  
  
## <a name="requirements"></a>要求  
 **标头：** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 构造 `CWinFormsView` 对象。  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>参数  
 `pManagedViewType`  
 指向 Windows 窗体用户控件的数据类型的指针。   
  
### <a name="example"></a>示例  
 在下面的示例中，`CUserView`类继承自`CWinFormsView`传递的类型和`UserControl1`到`CWinFormsView`构造函数。 `UserControl1`是 ControlLibrary1.dll 中的自定义控件。  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>CWinFormsView::GetControl  
 检索指向 Windows 窗体控件的指针。  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`System.Windows.Forms.Control`对象。  
  
### <a name="remarks"></a>备注  
 有关如何使用 Windows 窗体的示例，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_control"></a>CWinFormsView::operator 控件 ^  
 将类型强制转换为指向 Windows 窗体控件。  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>备注  
 此运算符，你可以传递`CWinFormsView`接受到 Windows 窗体控件的类型的指针的函数的视图<xref:System.Windows.Forms.Control>。  
  
### <a name="example"></a>示例  
  请参阅[CWinFormsView::GetControl](#getcontrol)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl 类](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog 类](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView 类](../../mfc/reference/cformview-class.md)
