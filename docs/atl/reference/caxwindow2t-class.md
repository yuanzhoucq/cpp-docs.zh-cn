---
title: CAxWindow2T 类
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: 14080b624132979df533135bc1eef108dc793398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318700"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 类

此类提供了用于操作承载 ActiveX 控件的窗口的方法，并且还支持托管许可的 ActiveX 控件。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>参数

*TBase*<br/>
派生的类`CAxWindowT`。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAxWindow2T：：CAxWindow2T](#caxwindow2t)|构造 `CAxWindow2T` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAxWindow2T：：创建](#create)|创建主机窗口。|
|[CAxWindow2T：：创建控制](#createcontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[CAxWindow2T：：创建控制](#createcontrollicex)|创建许可的 ActiveX 控件，初始化它，在指定的窗口中托管它，并从控件中检索接口指针（或指针）。|
|[CAxWindow2T：：获取wndClass名称](#getwndclassname)|检索窗口类名称的静态方法。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAxWindow2T：：运算符 |](#operator_eq)|将 HWND 分配给现有`CAxWindow2T`对象。|

## <a name="remarks"></a>备注

`CAxWindow2T`提供了用于操作承载 ActiveX 控件的窗口的方法。 `CAxWindow2T`还支持托管许可的 ActiveX 控件。 托管由 **"AtlAxWinLic80"** 提供，由`CAxWindow2T`包装。

类`CAxWindow2`作为`CAxWindow2T`类的专业化实现。 此专业化化声明为：

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT`成员记录在[CAxWindow](../../atl/reference/caxwindow-class.md)下。

有关使用此类成员的示例，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="inheritance-hierarchy"></a>继承层次结构

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T：：CAxWindow2T

构造 `CAxWindow2T` 对象。

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>参数

*hwnd*<br/>
现有窗口的句柄。

## <a name="caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T：：创建

创建主机窗口。

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>备注

`CAxWindow2T::Create`调用[CWindow：：](../../atl/reference/cwindow-class.md#create)使用 LPCTSTR *lpstrwndClass*参数创建到提供控件宿主 （`AtlAxWinLic80`） 的窗口类。

有关`CWindow::Create`参数和返回值的说明，请参阅。

**注意**如果 0 用作*MenuOrID*参数的值，则必须将其指定为 0U（默认值），以避免编译器错误。

### <a name="example"></a>示例

有关 使用`CAxWindow2T::Create`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T：：创建控制

创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>参数

*bstrLicKey*<br/>
控件的许可证密钥;如果创建非许可控件，则为 NULL。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[CAxWindow：CreateControl。](../../atl/reference/caxwindow-class.md#createcontrol)

### <a name="example"></a>示例

有关 使用`CAxWindow2T::CreateControlLic`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T：：创建控制

创建许可的 ActiveX 控件，初始化它，在指定的窗口中托管它，并从控件中检索接口指针（或指针）。

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>参数

*bstrLicKey*<br/>
控件的许可证密钥;如果创建非许可控件，则为 NULL。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[CAxWindow：createControlEx。](../../atl/reference/caxwindow-class.md#createcontrolex)

### <a name="example"></a>示例

有关 使用`CAxWindow2T::CreateControlLicEx`的样本，请参阅[使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)托管 ActiveX 控件。

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T：：获取wndClass名称

检索窗口类的名称。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>返回值

指向包含窗口类 （`AtlAxWinLic80`） 名称的字符串的指针，该字符串可以承载许可和非许可的 ActiveX 控件。

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T：：运算符 |

将 HWND 分配给现有`CAxWindow2T`对象。

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
现有窗口的句柄。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[控件包含常见问题](../../atl/atl-control-containment-faq.md)
