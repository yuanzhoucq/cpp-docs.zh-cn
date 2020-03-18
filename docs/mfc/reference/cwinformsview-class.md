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
ms.openlocfilehash: f4a5e6b88527dad8606092ccebd4899bba5181f6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426287"
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
|[CWinFormsView：： CWinFormsView](#cwinformsview)|构造 `CWinFormsView` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinFormsView：： GetControl](#getcontrol)|检索指向 Windows 窗体控件的指针。|

### <a name="public-operators"></a>公用運算子

|名称||
|----------|-|
|[CWinFormsView：： operator 控件 ^](#operator_control)|将类型强制转换为指向 Windows 窗体控件的指针。|

## <a name="remarks"></a>备注

MFC 使用 `CWinFormsView` 类在 MFC 视图中承载 .NET Framework Windows 窗体控件。 控件是本机视图的子级，它占据 MFC 视图的整个工作区。 结果类似于 `CFormView` 视图，使您可以利用 Windows 窗体设计器和运行时来创建基于窗体的丰富视图。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

> [!NOTE]
>  MFC Windows 窗体集成仅适用于使用 MFC 动态链接的项目（定义了 AFXDLL 的项目）。

> [!NOTE]
>  CWinFormsView 不支持 MFC 拆分窗口（ [CSplitterWnd 类](../../mfc/reference/csplitterwnd-class.md)）。 目前仅支持 Windows 窗体拆分器控件。

## <a name="requirements"></a>要求

**标头：** afxwinforms

##  <a name="cwinformsview"></a>CWinFormsView：： CWinFormsView

构造 `CWinFormsView` 对象。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>parameters

*pManagedViewType*<br/>
指向 Windows 窗体用户控件的数据类型的指针。

### <a name="example"></a>示例

在下面的示例中，`CUserView` 类继承自 `CWinFormsView` 并将 `UserControl1` 类型传递到 `CWinFormsView` 构造函数。 `UserControl1` 是 ControlLibrary1 中的自定义生成的控件。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>CWinFormsView：： GetControl

检索指向 Windows 窗体控件的指针。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>返回值

一个指向 `System.Windows.Forms.Control` 对象的指针。

### <a name="remarks"></a>备注

有关如何使用 Windows 窗体的示例，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="operator_control"></a>CWinFormsView：： operator 控件 ^

将类型强制转换为指向 Windows 窗体控件的指针。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>备注

此运算符允许您将 `CWinFormsView` 视图传递到接受指向类型 <xref:System.Windows.Forms.Control>的 Windows 窗体控件的指针的函数。

### <a name="example"></a>示例

  请参阅[CWinFormsView：： GetControl](#getcontrol)。

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl 类](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog 类](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 类](../../mfc/reference/cformview-class.md)
