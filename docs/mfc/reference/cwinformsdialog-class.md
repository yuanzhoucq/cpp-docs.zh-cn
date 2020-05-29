---
title: CWinForms对话类
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367429"
---
# <a name="cwinformsdialog-class"></a>CWinForms对话类

承载 Windows 窗体用户控件的 MFC 对话框类的包装器。

## <a name="syntax"></a>语法

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>参数

*T托管控制*<br/>
要在 MFC 应用程序中显示的 .NET 框架用户控件。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWinForms对话：：CwinForms对话](#cwinformsdialog)|构造 `CWinFormsDialog` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinForms对话：获取控制](#getcontrol)|检索对 Windows 窗体用户控件的引用。|
|[CWinForms对话：：获取控制句柄](#getcontrolhandle)|检索 Windows 窗体用户控件的窗口句柄。|
|[CwinForms对话：：OnInitDialog](#oninitdialog)|通过在 MFC 对话框上创建和托管 Windows 窗体用户控件来初始化 MFC 对话框。|

### <a name="public-operators"></a>公共运算符

|名称||
|----------|-|
|[CWinForms对话：：运算符 -&gt;](#operator_-_gt)|替换[CWinFormsDialog：：获取](#getcontrol)表达式中的控制。|
|[CWinForms对话：：操作员 T 托管控制*](#operator-tmanagedcontrol-hat)|将类型强制转换为对 Windows 窗体用户控件的引用。|

## <a name="remarks"></a>备注

`CWinFormsDialog`是承载 Windows 窗体用户控件的 MFC 对话框类[（ CDialog](../../mfc/reference/cdialog-class.md)） 的包装器。 这允许在模态或无模式 MFC 对话框上显示 .NET 框架控件。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)，并将[Windows 窗体用户控件托管为 MFC 对话框](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。

## <a name="requirements"></a>要求

**标题：** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinForms对话：：CwinForms对话

构造 `CWinFormsDialog` 对象。

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>参数

*nIDTemplate*<br/>
包含对话框模板资源的 ID。 使用对话框编辑器创建对话框模板并将其存储在应用程序的资源脚本文件中。 有关对话框模板的详细信息，请参阅[CDialog 类](../../mfc/reference/cdialog-class.md)。

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinForms对话：获取控制

检索对 Windows 窗体用户控件的引用。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>返回值

在 MFC 对话框中返回对 Windows 窗体控件的引用。

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinForms对话：：获取控制句柄

检索 Windows 窗体用户控件的窗口句柄。

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>返回值

将窗口句柄返回到 Windows 窗体用户控件。

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CwinForms对话：：OnInitDialog

通过在 MFC 对话框上创建和托管 Windows 窗体用户控件来初始化 MFC 对话框。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>返回值

Boolean 值，用于指定应用程序是否已将输入焦点设置为对话框中的一个控件。 如果`OnInitDialog`返回非零，Windows 会将输入焦点设置到对话框中的第一个控件。 仅当应用程序已显式将输入焦点设置为对话框中的一个控件时，此方法才能返回 0。

### <a name="remarks"></a>备注

创建 MFC 对话框（使用从[CDialog](../../mfc/reference/cdialog-class.md)继承的[创建](../../mfc/reference/cdialog-class.md#create)、[创建间接](../../mfc/reference/cdialog-class.md#createindirect)或[DoModal](../../mfc/reference/cdialog-class.md#domodal)方法）时，将发送WM_INITDIALOG消息并调用此方法。 它在对话框上创建 Windows 窗体控件的实例，并调整对话框的大小以适应用户控件的大小。 然后，它将在 MFC 对话框中承载新控件。

如果在初始化对话框时需要执行特殊处理，则重写此成员函数。 有关使用此方法的详细信息，请参阅[CDialog：onInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)。

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinForms对话：：运算符 -&gt;

替换[CWinFormsDialog：：获取](#getcontrol)表达式中的控制。

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>备注

此运算符提供了一个方便的语法，`GetControl`在表达式中替换。

有关使用 Windows 窗体的信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinForms对话：：操作员 T 托管控制*

将类型强制转换为对 Windows 窗体用户控件的引用。

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>备注

此运算符强制转换类型作为对 Windows 窗体控件的引用。 它用于将`CWinFormsDialog<TManagedControl>`对话框传递给接受指向 Windows 窗体用户控件对象的指针的函数。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog 类](../../mfc/reference/cdialog-class.md)
