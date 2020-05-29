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
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330207"
---
# <a name="debugging-and-error-reporting-global-functions"></a>调试和错误报告全局函数

这些功能提供有用的调试和跟踪功能。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|返回`GetLastError`HRESULT 形式的错误代码。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|将 Win32 错误代码转换为 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|设置`IErrorInfo`以向客户端提供错误详细信息。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|引发 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>从上次错误中得出

以 HRESULT 的形式返回调用线程的上一个错误代码值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>备注

`AtlHresultFromLastError`调用`GetLastError`以获取最后一个错误，并在使用HRESULT_FROM_WIN32宏将其转换为 HRESULT 后返回该错误。

### <a name="requirements"></a>要求

**标题：** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresult从Win32

将 Win32 错误代码转换为 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>参数

*错误*<br/>
要转换的错误值。

### <a name="remarks"></a>备注

使用宏HRESULT_FROM_WIN32将 Win32 错误代码转换为 HRESULT。

> [!NOTE]
> 而不是使用`HRESULT_FROM_WIN32(GetLastError())`， 使用 函数[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。

### <a name="requirements"></a>要求

**标题：** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>AtlReport错误

设置`IErrorInfo`接口以向对象的客户端提供错误信息。

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

### <a name="parameters"></a>参数

*Clsid*<br/>
[在]报告错误的对象的 CLSID。

*lpszDesc*<br/>
[在]描述错误的字符串。 Unicode 版本指定*lpszDesc*的类型为 LPCOLESTR;ANSI 版本指定 LPCSTR 的类型。

*Iid*<br/>
[在]定义错误的接口的 IID，或者如果错误是由操作系统定义的，则GUID_NULL。

*hRes*<br/>
[在]要返回给调用方的 HRESULT。

*nID*<br/>
[在]存储错误描述字符串的资源标识符。 此值应介于 0x0200 和 0xFF 之间（包括）。 在调试生成中，如果*nID*不索引有效字符串，则会产生**ASSERT。** 在发布版本中，错误描述字符串将设置为"未知错误"。

*dwHelpID*<br/>
[在]错误的帮助上下文标识符。

*lpszHelp文件*<br/>
[在]描述错误的帮助文件的路径和名称。

*hInst*<br/>
[在]资源的句柄。 默认情况下，此参数是`__AtlBaseModuleModule::GetResourceInstance` `__AtlBaseModuleModule` [，CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)的全局实例或派生自它的类位于此地。

### <a name="return-value"></a>返回值

如果*hRes*参数是非零，则返回*hRes*的值。 如果*hRes*为零，则`AtlReportError`返回的前四个版本DISP_E_EXCEPTION。 最后两个版本返回宏**MAKE_HRESULT的结果（1，FACILITY_ITF。** `nID` **)**

### <a name="remarks"></a>备注

字符串*lpszDesc*用作错误的文本说明。 当客户端收到您从`AtlReportError`返回*的 hRe 时*，客户端可以访问结构以`IErrorInfo`了解有关错误的详细信息。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> 请勿在`AtlReportError`C++捕获处理程序中使用。 这些函数的某些重写在内部使用 ATL 字符串转换宏，而后者又在内部使用`_alloca`该函数。 `AtlReportError`在C++捕获处理程序中使用可能会导致C++捕获处理程序中的异常。

### <a name="requirements"></a>要求

**标题：** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow

调用此函数以根据 HRESULT 状态代码发出错误信号。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>参数

*人力资源*<br/>
标准 HRESULT 值。

### <a name="remarks"></a>备注

在出现错误情况时，ATL 和 MFC 代码会使用此功能。 也可以从您自己的代码调用它。 此函数的默认实现取决于符号_ATL_NO_EXCEPTIONS的定义以及项目类型 MFC 或 ATL。

在所有情况下，此函数将 HRESULT 跟踪到调试器。

在 Visual Studio 2015 更新 3 及更高版本中，此功能被归因于__declspec（不返回），以避免虚假的 SAL 警告。

如果未在 MFC 项目中定义_ATL_NO_EXCEPTIONS，则此函数将基于 HRESULT 的值引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException。](../../mfc/reference/coleexception-class.md)

如果在 ATL 项目中未定义_ATL_NO_EXCEPTIONS，则函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。

如果定义了_ATL_NO_EXCEPTIONS，则函数会导致断言失败，而不是引发异常。

对于 ATL 项目，可以提供您自己的实现，以便 ATL 在发生故障时使用此功能。 为此，使用与`AtlThrow`函数的名称相同的签名和#define`AtlThrow`定义您自己的函数。 这必须在包括 atlexcept.h 之前完成（这意味着在包括任何 ATL 标头之前必须完成，因为 atlbase.h 包含 atlexcept.h）。 属性函数`__declspec(noreturn)`以避免虚假的 SAL 警告。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>要求

**标题：** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32

调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>备注

此函数跟踪调试器的结果`GetLastError`。

如果未在 MFC 项目中定义_ATL_NO_EXCEPTIONS，则此函数将基于 返回`GetLastError`的值引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException。](../../mfc/reference/coleexception-class.md)

如果在 ATL 项目中未定义_ATL_NO_EXCEPTIONS，则函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。

如果定义了_ATL_NO_EXCEPTIONS，则函数会导致断言失败，而不是引发异常。

## <a name="requirements"></a>要求

**标题：** atldef.h

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[调试和错误报告宏](../../atl/reference/debugging-and-error-reporting-macros.md)
