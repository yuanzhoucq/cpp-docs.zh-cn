---
title: CWinFormsControl 类
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
ms.openlocfilehash: 91691203f88f07f597aaad6a5db32b03e7ad11c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323291"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl 类

提供用于承载 Windows 窗体控件的基本功能。

## <a name="syntax"></a>语法

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>参数

*TManagedControl*<br/>
要在 MFC 应用程序中显示.NET Framework Windows 窗体控件。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|构造一个 MFC Windows 窗体控件包装器对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|在 MFC 容器中创建的 Windows 窗体控件。|
|[CWinFormsControl::GetControl](#getcontrol)|检索指向在 Windows 窗体控件。|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|检索 Windows 窗体控件的句柄。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|将替换[CWinFormsControl::GetControl](#getcontrol)在表达式中。|
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|将一种类型强制转换为指向的 Windows 窗体控件的指针。|

## <a name="remarks"></a>备注

`CWinFormsControl`类提供了用于承载 Windows 窗体控件的基本功能。

有关使用 Windows 窗体的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

MFC 代码不应缓存窗口句柄 (通常存储在`m_hWnd`)。 某些 Windows 窗体控件属性需要基础 Win32`Window`销毁并重新创建使用`DestroyWindow`和`CreateWindow`。 MFC Windows 窗体实现句柄`Destroy`并`Create`要更新的控件的事件`m_hWnd`成员。

> [!NOTE]
>  MFC Windows 窗体集成仅在使用 MFC （在其中定义了 AFXDLL） 动态链接的项目中可以正常工作。

## <a name="requirements"></a>要求

**标头：** afxwinforms.h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl

在 MFC 容器中创建的 Windows 窗体控件。

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

*pType*<br/>
要创建的控件的数据类型。 必须是[类型](https://msdn.microsoft.com/library/system.type)数据类型。

*dwStyle*<br/>
要应用于控件的窗口样式。 指定的组合[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 目前，支持仅以下样式：WS_TABSTOP、 WS_VISIBLE、 WS_DISABLED 和 WS_GROUP。

*rect*<br/>
一个[RECT 结构](/windows/desktop/api/windef/ns-windef-tagrect)，它定义控件的左上角和右下角的坐标 （仅第一个重载）。

*nPlaceHolderID*<br/>
静态位置持有者控件的句柄放在资源编辑器中。 在新创建的 Windows 窗体控件取代了静态控件，假定其位置、 z 顺序和样式 （仅第二个重载）。

*pParentWnd*<br/>
指向父窗口的指针。

*nID*<br/>
要分配给新创建的控件的资源 ID 号。

*pControl*<br/>
若要与之关联的 Windows 窗体控件的实例[CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)对象 （仅第四个重载）。

### <a name="return-value"></a>返回值

如果成功，返回非零值。 如果不成功，将返回零。

### <a name="remarks"></a>备注

此方法实例化 MFC 容器中的.NET Framework Windows 窗体控件。

该方法的第一个重载接受.NET Framework 数据类型*pType*以便 MFC 可以实例化此类型的新对象。 *pType*必须是[类型](https://msdn.microsoft.com/library/system.type)数据类型。

该方法的第二个重载创建基于的 Windows 窗体控件`TManagedControl`的模板参数`CWinFormsControl`类。 大小和位置的控件基于`RECT`结构传递给该方法。 仅*dwStyle*样式非常重要。

该方法的第三个重载创建替换静态控件，将其销毁，并假设其位置、 z 顺序和样式的 Windows 窗体控件。 静态控件只能用作在 Windows 窗体控件的占位符。 在创建控件时，此重载将合并来自样式*dwStyle*使用静态控件的资源样式。

该方法的第四个重载允许您将在已经实例化 Windows 窗体控件中传递*pControl* ，MFC 将自动换行。 它必须与相同类型的`TManagedControl`的模板参数`CWinFormsControl`类。

请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)了解有关使用 Windows 窗体控件。

##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl

构造一个 MFC Windows 窗体控件包装器对象。

```
CWinFormsControl();
```

### <a name="remarks"></a>备注

在调用时，实例化 Windows 窗体控件[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。

##  <a name="getcontrol"></a>  CWinFormsControl::GetControl

检索指向在 Windows 窗体控件。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>返回值

返回一个指向在 Windows 窗体控件。

### <a name="example"></a>示例

  请参阅[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。

##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle

检索 Windows 窗体控件的句柄。

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>返回值

返回的句柄在 Windows 窗体控件。

### <a name="remarks"></a>备注

`GetControlHandle` 是返回存储在.NET Framework 控件属性中的窗口句柄的帮助器方法。 窗口句柄值复制到[CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd)在调用[CWnd::Attach](../../mfc/reference/cwnd-class.md#attach)。

##  <a name="operator_-_gt"></a>  CWinFormsControl::operator -&gt;

将替换[CWinFormsControl::GetControl](#getcontrol)在表达式中。

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>备注

此运算符提供了方便的语法，用于替换`GetControl`在表达式中。

在 Windows 窗体上的详细信息，请参阅[在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl^

将一种类型强制转换为指向的 Windows 窗体控件的指针。

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>备注

此运算符将传递`CWinFormsControl<TManagedControl>`接受指向的 Windows 窗体控件的指针的函数。

## <a name="see-also"></a>请参阅

[CWinFormsDialog 类](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView 类](../../mfc/reference/cwinformsview-class.md)
