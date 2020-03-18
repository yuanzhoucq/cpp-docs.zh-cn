---
title: 调试和错误报告全局函数
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7483b7473383958089b0c88d0b3c2645ddc2a4f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423134"
---
# <a name="debugging-and-error-reporting-global-functions"></a>调试和错误报告全局函数

这些函数提供有用的调试和跟踪功能。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|以 HRESULT 形式返回 `GetLastError` 错误代码。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|将 Win32 错误代码转换为 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|设置 `IErrorInfo` 以向客户端提供错误详细信息。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|引发 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。|

##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

以 HRESULT 的形式返回调用线程的上一个错误代码值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>备注

`AtlHresultFromLastError` 调用 `GetLastError` 获取最后一个错误，并使用 HRESULT_FROM_WIN32 宏将错误转换为 HRESULT 后返回该错误。

### <a name="requirements"></a>要求

**标头：** atlcomcli。h

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32

将 Win32 错误代码转换为 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>parameters

*error*<br/>
要转换的错误值。

### <a name="remarks"></a>备注

使用宏 HRESULT_FROM_WIN32 将 Win32 错误代码转换为 HRESULT。

> [!NOTE]
>  使用[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)函数，而不是使用 `HRESULT_FROM_WIN32(GetLastError())`。

### <a name="requirements"></a>要求

**标头：** atlcomcli。h

##  <a name="atlreporterror"></a>AtlReportError

设置 `IErrorInfo` 接口，为对象的客户端提供错误信息。

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>parameters

*clsid*<br/>
中报告错误的对象的 CLSID。

*lpszDesc*<br/>
中描述错误的字符串。 Unicode 版本指定*lpszDesc*的类型为 LPCOLESTR;ANSI 版本指定 LPCSTR 的类型。

*iid*<br/>
中定义错误的接口的 IID，如果错误是由操作系统定义的，则为 GUID_NULL。

*hRes*<br/>
中要返回给调用方的 HRESULT。

*nID*<br/>
中存储错误说明字符串的资源标识符。 此值应介于0x0200 和0xFFFF 之间，包括在内。 在调试版本中，如果*nID*未为有效字符串编制索引，则会产生**断言**。 在发布版本中，错误描述字符串将设置为 "未知错误"。

*dwHelpID*<br/>
中错误的帮助上下文标识符。

*lpszHelpFile*<br/>
中描述错误的帮助文件的路径和名称。

*hInst*<br/>
中资源的句柄。 默认情况下，此参数为 `__AtlBaseModuleModule::GetResourceInstance`，其中 `__AtlBaseModuleModule` 是[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)的全局实例或从其派生的类。

### <a name="return-value"></a>返回值

如果*hRes*参数为非零，则返回*hRes*的值。 如果*hRes*为零，则 `AtlReportError` 的前四个版本返回 DISP_E_EXCEPTION。 最后两个版本返回宏的结果**MAKE_HRESULT （1、FACILITY_ITF** `nID` **）** 。

### <a name="remarks"></a>备注

字符串*lpszDesc*用作错误的文本说明。 当客户端收到 `AtlReportError`返回的*hRes*时，客户端可以访问 `IErrorInfo` 结构以获取有关错误的详细信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  请勿在 catch 处理程序C++中使用 `AtlReportError`。 这些函数的一些替代在内部使用 ATL 字符串转换宏，这反过来又在内部使用 `_alloca` 函数。 在C++ catch 处理程序中使用 `AtlReportError` 会导致 catch C++处理程序中出现异常。

### <a name="requirements"></a>要求

**标头：** atlcom。h

##  <a name="atlthrow"></a>AtlThrow

调用此函数可根据 HRESULT 状态代码指示错误。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>parameters

*人事*<br/>
标准 HRESULT 值。

### <a name="remarks"></a>备注

此函数由 ATL 和 MFC 代码在出现错误情况时使用。 还可以从自己的代码中调用它。 此函数的默认实现取决于符号 _ATL_NO_EXCEPTIONS 和项目类型（MFC 或 ATL）的定义。

在所有情况下，此函数都将 HRESULT 跟踪到调试器。

在 Visual Studio 2015 Update 3 和更高版本中，此函数的属性 __declspec （noreturn），以避免出现虚假的 SAL 警告。

如果 MFC 项目中未定义 _ATL_NO_EXCEPTIONS，则此函数将根据 HRESULT 的值引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md) 。

如果在 ATL 项目中未定义 _ATL_NO_EXCEPTIONS，该函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。

如果定义 _ATL_NO_EXCEPTIONS，该函数将导致断言失败，而不引发异常。

对于 ATL 项目，可以提供此函数的实现，以便在发生故障时 ATL 使用该函数。 为此，请用与 `AtlThrow` 相同的签名定义自己的函数，并 #define `AtlThrow` 作为函数的名称。 必须在包含 atlexcept 之前完成此操作（这意味着必须在包含任何 ATL 标头之前完成此操作），因为 atlbase.h 包含 atlexcept。 将函数 `__declspec(noreturn)` 特性，以避免出现虚假的 SAL 警告。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>要求

**标头：** atldef

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32

调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>备注

此函数跟踪 `GetLastError` 到调试器的结果。

如果 MFC 项目中未定义 _ATL_NO_EXCEPTIONS，则此函数将基于 `GetLastError`返回的值引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md) 。

如果在 ATL 项目中未定义 _ATL_NO_EXCEPTIONS，该函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。

如果定义 _ATL_NO_EXCEPTIONS，该函数将导致断言失败，而不引发异常。

## <a name="requirements"></a>要求

**标头：** atldef

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[调试和错误报告宏](../../atl/reference/debugging-and-error-reporting-macros.md)
