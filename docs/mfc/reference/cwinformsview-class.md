---
title: CWinFormsView 类
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369596"
---
# <a name="cwinformsview-class"></a>CWinFormsView 类

提供用于将 Windows 窗体控件作为 MFC 视图承载的一般功能。

## <a name="syntax"></a>语法

```
class CWinFormsView : public CView;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWinForms查看：CwinForms查看](#cwinformsview)|构造 `CWinFormsView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinForms查看：获取控制](#getcontrol)|检索指向 Windows 窗体控件的指针。|

### <a name="public-operators"></a>公共运算符

|名称||
|----------|-|
|[CWinForms查看：：操作员控制*](#operator_control)|将类型转换为指向 Windows 窗体控件的指针。|

## <a name="remarks"></a>备注

MFC 使用`CWinFormsView`类在 MFC 视图中托管 .NET 框架 Windows 窗体控件。 控件是本机视图的子级，并占据 MFC 视图的整个工作区。 结果类似于`CFormView`视图，允许您利用 Windows 窗体设计器和运行时创建丰富的基于窗体的视图。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

> [!NOTE]
> MFC Windows 窗体集成仅适用于与 MFC 动态链接的项目（其中定义了 AFXDLL 的项目）。

> [!NOTE]
> CWinFormsView 不支持 MFC 拆分器窗口[（CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)）。 目前仅支持 Windows 窗体拆分器控件。

## <a name="requirements"></a>要求

**标题：** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinForms查看：CwinForms查看

构造 `CWinFormsView` 对象。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>参数

*p托管视图类型*<br/>
指向 Windows 窗体用户控件的数据类型的指针。

### <a name="example"></a>示例

在下面的`CUserView`示例中，类继承`CWinFormsView`并将 的类型`UserControl1`传递给`CWinFormsView`构造函数。 `UserControl1`是 ControlLibrary1.dll 中的自定义控件。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinForms查看：获取控制

检索指向 Windows 窗体控件的指针。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>返回值

一个指向 `System.Windows.Forms.Control` 对象的指针。

### <a name="remarks"></a>备注

有关如何使用 Windows 窗体的示例，请参阅在[MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinForms查看：：操作员控制*

将类型转换为指向 Windows 窗体控件的指针。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>备注

此运算符允许您将`CWinFormsView`视图传递给接受指向类型<xref:System.Windows.Forms.Control>Windows 窗体控件的指针的函数。

### <a name="example"></a>示例

  请参阅[CWinFormsView：获取控制](#getcontrol)。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CWinForms控制类](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinForms对话类](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
