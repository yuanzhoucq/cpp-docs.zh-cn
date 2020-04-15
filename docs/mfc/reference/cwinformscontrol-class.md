---
title: CWinForms控制类
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377180"
---
# <a name="cwinformscontrol-class"></a>CWinForms控制类

提供用于承载 Windows 窗体控件的基本功能。

## <a name="syntax"></a>语法

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>参数

*T托管控制*<br/>
要在 MFC 应用程序中显示的 .NET 框架 Windows 窗体控件。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWinForms控制：CwinForms控制](#cwinformscontrol)|构造 MFC Windows 窗体控件包装对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWinForms控制：创建托管控制](#createmanagedcontrol)|在 MFC 容器中创建 Windows 窗体控件。|
|[CWinForms控制：获取控制](#getcontrol)|检索指向 Windows 窗体控件的指针。|
|[CWinForms控制：获取控制句柄](#getcontrolhandle)|检索 Windows 窗体控件的句柄。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CWinForms控制：：运算符 -&gt;](#operator_-_gt)|替换[CWinForms 控制：获取](#getcontrol)表达式中的控制。|
|[CWinForms控制：：操作员 T 托管控制*](#operator_tmanagedcontrol)|将类型转换为指向 Windows 窗体控件的指针。|

## <a name="remarks"></a>备注

该`CWinFormsControl`类提供用于托管 Windows 窗体控件的基本功能。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

MFC 代码不应缓存窗口句柄（通常存储在 中`m_hWnd`）。 某些 Windows 窗体控件属性要求使用`Window``DestroyWindow`和 销毁和重新创建基础`CreateWindow`Win32。 MFC Windows 窗体实现处理`Destroy`要`Create`更新`m_hWnd`成员的控件的 和 事件。

> [!NOTE]
> MFC Windows 窗体集成仅适用于与 MFC 动态链接的项目（其中定义了 AFXDLL）。

## <a name="requirements"></a>要求

**标题：** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinForms控制：创建托管控制

在 MFC 容器中创建 Windows 窗体控件。

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>参数

*p类型*<br/>
要创建的控件的数据类型。 必须为[类型](/dotnet/api/system.type)数据类型。

*dwStyle*<br/>
要应用于控件的窗口样式。 指定[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的组合。 目前，仅支持以下样式：WS_TABSTOP、WS_VISIBLE、WS_DISABLED和WS_GROUP。

*矩形*<br/>
定义控件左上角和右下角坐标（仅首次过载）的[RECT 结构](/windows/win32/api/windef/ns-windef-rect)。

*nPlaceHolderID*<br/>
放置在资源编辑器中的静态占位符控件的句柄。 新创建的 Windows 窗体控件将替换静态控件，假设其位置、z 顺序和样式（仅第二次重载）。

*pparentwnd*<br/>
指向父窗口的指针。

*nID*<br/>
要分配给新创建的控件的资源 ID 号。

*pControl*<br/>
要与[CWinFormsControl 控制](../../mfc/reference/cwinformscontrol-class.md)对象关联的 Windows 窗体控件的实例（仅限第四次重载）。

### <a name="return-value"></a>返回值

如果成功，则返回一个非零值。 如果不成功，则返回零。

### <a name="remarks"></a>备注

此方法实例化 MFC 容器中的 .NET 框架 Windows 窗体控件。

方法的第一个重载接受 .NET 框架数据类型*pType，* 以便 MFC 可以实例化此类型的新对象。 *pType*必须是[类型](/dotnet/api/system.type)数据类型。

方法的第二个重载基于`TManagedControl``CWinFormsControl`类的模板参数创建 Windows 窗体控件。 控件的大小和位置基于传递给方法`RECT`的结构。 只有*dwStyle*才对样式很重要。

方法的第三个重载将创建一个 Windows 窗体控件，该控件将替换静态控件，将其破坏并假定其位置、z 顺序和样式。 静态控件仅用作 Windows 窗体控件的占位符。 创建控件时，此重载将*dwStyle*中的样式与静态控件的资源样式合并。

方法的第四个重载允许您传递 MFC 将包装的已实例化 Windows 窗体控件*pControl。* 它必须与`TManagedControl``CWinFormsControl`类的模板参数类型相同。

有关使用 Windows 窗体控件的示例[，请参阅在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinForms控制：CwinForms控制

构造 MFC Windows 窗体控件包装对象。

```
CWinFormsControl();
```

### <a name="remarks"></a>备注

当您调用[CWinFormsControl：：创建托管控制](#createmanagedcontrol)时，Windows 窗体控件将实例化。

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinForms控制：获取控制

检索指向 Windows 窗体控件的指针。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>返回值

返回指向 Windows 窗体控件的指针。

### <a name="example"></a>示例

  请参阅[CWinForms 控制：创建托管控制](#createmanagedcontrol)。

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinForms控制：获取控制句柄

检索 Windows 窗体控件的句柄。

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>返回值

将句柄返回到 Windows 窗体控件。

### <a name="remarks"></a>备注

`GetControlHandle`是返回存储在 .NET Framework 控件属性中的窗口句柄的帮助器方法。 在调用[CWnd：：：附加](../../mfc/reference/cwnd-class.md#attach)期间，窗口句柄值将复制到[CWnd：：m_hWnd。](../../mfc/reference/cwnd-class.md#m_hwnd)

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinForms控制：：运算符 -&gt;

替换[CWinForms 控制：获取](#getcontrol)表达式中的控制。

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>备注

此运算符提供了一个方便的语法，`GetControl`在表达式中替换。

有关 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinForms控制：：操作员 T 托管控制*

将类型转换为指向 Windows 窗体控件的指针。

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>备注

此运算符传递给`CWinFormsControl<TManagedControl>`接受指向 Windows 窗体控件的指针的函数。

## <a name="see-also"></a>另请参阅

[CWinForms对话类](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)
