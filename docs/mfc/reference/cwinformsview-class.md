---
title: CWinFormsView 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4d90f2a7f964d264966d5254d051ebddaf2baa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448137"
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
|[CWinFormsView::GetControl](#getcontrol)|检索指向在 Windows 窗体控件。|

### <a name="public-operators"></a>公共运算符

|name||
|----------|-|
|[CWinFormsView::operator 控件 ^](#operator_control)|将一种类型强制转换为指向的 Windows 窗体控件的指针。|

## <a name="remarks"></a>备注

MFC 使用`CWinFormsView`类以承载 MFC 视图中的.NET Framework Windows 窗体控件。 该控件是本机的视图的子级，并占据整个工作区的 MFC 视图。 结果是类似于`CFormView`视图，从而可以充分利用 Windows 窗体设计器和运行时创建丰富的基于窗体的视图。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

> [!NOTE]
>  MFC Windows 窗体集成适用于仅在动态链接 mfc 的项目中 （在其中定义 AFXDLL 项目）。

> [!NOTE]
>  CWinFormsView 不支持 MFC 拆分器窗口 ( [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md))。 当前仅 Windows 窗体拆分器支持控件。

## <a name="requirements"></a>要求

**标头：** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

构造 `CWinFormsView` 对象。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>参数

*pManagedViewType*<br/>
指向 Windows 窗体用户控件的数据类型的指针。

### <a name="example"></a>示例

在以下示例中，`CUserView`类继承自`CWinFormsView`，并将传递的类型`UserControl1`到`CWinFormsView`构造函数。 `UserControl1` 是 ControlLibrary1.dll 中的自定义构建控件。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  CWinFormsView::GetControl

检索指向在 Windows 窗体控件。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>返回值

一个指向`System.Windows.Forms.Control`对象。

### <a name="remarks"></a>备注

有关如何使用 Windows 窗体的示例，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="operator_control"></a>  CWinFormsView::operator 控件 ^

将一种类型强制转换为指向的 Windows 窗体控件的指针。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>备注

此运算符可用于传递`CWinFormsView`函数接受一个指向类型的 Windows 窗体控件的视图<xref:System.Windows.Forms.Control>。

### <a name="example"></a>示例

  请参阅[CWinFormsView::GetControl](#getcontrol)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl 类](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog 类](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
