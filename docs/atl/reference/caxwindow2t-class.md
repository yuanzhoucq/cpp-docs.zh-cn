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
ms.openlocfilehash: 0d5991dcbf79d1c2415594636a09908586d1dc2f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864713"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T 类

此类提供用于操作承载 ActiveX 控件的窗口的方法，并且还支持承载许可的 ActiveX 控件。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>parameters

*TBase*<br/>
从中派生 `CAxWindowT` 的类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|构造 `CAxWindow2T` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CAxWindow2T：： Create](#create)|创建宿主窗口。|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|创建授权的 ActiveX 控件，初始化它并在指定窗口中承载它。|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|创建许可的 ActiveX 控件，对其进行初始化，在指定窗口中承载该控件，并从该控件中检索一个接口指针。|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|检索窗口类名称的静态方法。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CAxWindow2T：： operator =](#operator_eq)|为现有 `CAxWindow2T` 对象分配 HWND。|

## <a name="remarks"></a>备注

`CAxWindow2T` 提供操作承载 ActiveX 控件的窗口的方法。 `CAxWindow2T` 还支持承载许可的 ActiveX 控件。 托管由 " **AtlAxWinLic80**" 提供，由 `CAxWindow2T`包装。

类 `CAxWindow2` 是作为 `CAxWindow2T` 类的专用化实现的。 此特殊化声明为：

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> [CAxWindow](../../atl/reference/caxwindow-class.md)下记录了 `CAxWindowT` 成员。

有关使用此类的成员的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>要求

**标头：** atlwin。h

##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

构造 `CAxWindow2T` 对象。

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>parameters

*hWnd*<br/>
现有窗口的句柄。

##  <a name="create"></a>CAxWindow2T：： Create

创建宿主窗口。

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

`CAxWindow2T::Create` 调用[CWindow：： Create](../../atl/reference/cwindow-class.md#create) ，并将 LPCTSTR *lpstrWndClass*参数设置为提供控件承载的窗口类（`AtlAxWinLic80`）。

有关参数和返回值的说明，请参阅 `CWindow::Create`。

**注意**如果将0用作*MenuOrID*参数的值，则必须将其指定为0u （默认值），以避免出现编译器错误。

### <a name="example"></a>示例

有关使用 `CAxWindow2T::Create`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

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

### <a name="parameters"></a>parameters

*bstrLicKey*<br/>
控件的许可证密钥;如果创建 nonlicensed 控件，则为 NULL。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[CAxWindow：： CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) 。

### <a name="example"></a>示例

有关使用 `CAxWindow2T::CreateControlLic`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

创建许可的 ActiveX 控件，对其进行初始化，在指定窗口中承载该控件，并从该控件中检索一个接口指针。

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

### <a name="parameters"></a>parameters

*bstrLicKey*<br/>
控件的许可证密钥;如果创建 nonlicensed 控件，则为 NULL。

### <a name="remarks"></a>备注

有关剩余参数和返回值的说明，请参阅[CAxWindow：： CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) 。

### <a name="example"></a>示例

有关使用 `CAxWindow2T::CreateControlLicEx`的示例，请参阅[使用 ATL AXHost 托管 ActiveX 控件](../../atl/hosting-activex-controls-using-atl-axhost.md)。

##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

检索窗口类的名称。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>返回值

一个指向字符串的指针，该字符串包含可承载许可的 ActiveX 控件和 nonlicensed ActiveX 控件的窗口类的名称（`AtlAxWinLic80`）。

##  <a name="operator_eq"></a>CAxWindow2T：： operator =

为现有 `CAxWindow2T` 对象分配 HWND。

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>parameters

*hWnd*<br/>
现有窗口的句柄。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)<br/>
[控制包含常见问题](../../atl/atl-control-containment-faq.md)
