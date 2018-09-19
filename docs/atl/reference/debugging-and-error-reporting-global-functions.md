---
title: 调试和错误报告全局函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs:
- C++
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3bef300671894e054ddf9b1ca0ab9dcf3b135370
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019404"
---
# <a name="debugging-and-error-reporting-global-functions"></a>调试和错误报告全局函数

这些函数提供有用的调试和跟踪工具。

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|返回`GetLastError`HRESULT 的形式中的错误代码。|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|将 Win32 错误代码转换为 HRESULT。|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|设置了`IErrorInfo`向客户端提供错误详细信息。|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|引发 `CAtlException`。|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。|

##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError

以 HRESULT 的形式返回调用线程的上一个错误代码值。

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>备注

`AtlHresultFromLastError` 调用`GetLastError`若要获取的最后一个错误，并将其转换为 HRESULT 使用返回 HRESULT_FROM_WIN32 宏后返回错误。  

### <a name="requirements"></a>要求

**标头：** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32

将 Win32 错误代码转换为 HRESULT。

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>参数

*error*<br/>
要转换的错误值。

### <a name="remarks"></a>备注

将使用宏返回 HRESULT_FROM_WIN32 HRESULT 转换为 Win32 错误代码。

> [!NOTE]
>  而不是使用`HRESULT_FROM_WIN32(GetLastError())`，使用函数[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。  

### <a name="requirements"></a>要求

**标头：** atlcomcli.h  

##  <a name="atlreporterror"></a>  AtlReportError

设置了`IErrorInfo`接口向对象的客户端提供错误信息。

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

*clsid*<br/>
[in]报告错误的对象的 CLSID。

*lpszDesc*<br/>
[in]描述错误的字符串。 Unicode 版本指定*lpszDesc*属于类型 LPCOLESTR; ANSI 版本指定 LPCSTR 的类型。

*iid*<br/>
[in]如果错误由操作系统定义的错误或 GUID_NULL 的接口的 IID。

*hRes*<br/>
[in]所需的 HRESULT 返回到调用方。

*nID*<br/>
[in]资源标识符的错误描述字符串的存储位置。 此值应介于 0x0200 和 0xffff 内，之间 （含）。 在调试版本中， **ASSERT**如果会导致*nID*没有有效的字符串进行索引。 在发布版本中的错误描述字符串将设置为"未知错误。"

*dwHelpID*<br/>
[in]错误的帮助上下文标识符。

*lpszHelpFile*<br/>
[in]路径和描述错误的帮助文件的名称。

*hInst*<br/>
[in]资源的句柄。 默认情况下，此参数是`__AtlBaseModuleModule::GetResourceInstance`，其中`__AtlBaseModuleModule`是全局实例[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)或从其派生的类。

### <a name="return-value"></a>返回值

如果*hRes*参数为非零值，则返回的值*hRes*。 如果*hRes*为零，则前四个版本的`AtlReportError`返回 DISP_E_EXCEPTION。 最后两个版本都会返回结果的宏**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。

### <a name="remarks"></a>备注

将字符串*lpszDesc*用作该错误的文本说明。 当客户端收到*hRes*返回从`AtlReportError`，客户端可以访问`IErrorInfo`有关错误的详细信息的结构。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  不要使用`AtlReportError`中 c + + catch 处理程序。 这些函数的有些重写使用 ATL 字符串转换宏在内部，这反过来使用`_alloca`内部函数。 使用`AtlReportError`在 c + + catch 处理程序可能会导致 c + + catch 处理程序中的异常。  

### <a name="requirements"></a>要求

**标头：** atlcom.h

##  <a name="atlthrow"></a>  AtlThrow

调用此函数可根据 HRESULT 状态代码发出错误信号。

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>参数

*hr*<br/>
标准的 HRESULT 值。

### <a name="remarks"></a>备注

ATL 和 MFC 代码出现错误条件时使用此函数。 它还可以从你自己的代码调用。 此函数的默认实现取决于符号 _ATL_NO_EXCEPTIONS 的定义和类型的项目，MFC 或 atl。

在所有情况下，此函数跟踪到调试器的 HRESULT。

在 Visual Studio 2015 Update 3 及更高版本，此函数是特性化 __declspec （noreturn） 以避免出现虚假的 SAL 警告。

如果 _ATL_NO_EXCEPTIONS 未定义 MFC 项目中，此函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)基于的 HRESULT 值。

如果在 ATL 项目中未定义 _ATL_NO_EXCEPTIONS，该函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。

如果定义 _ATL_NO_EXCEPTIONS，则该函数将导致断言失败而不是引发异常。

对于 ATL 项目，则可以提供由 ATL 发生故障时要使用此函数的实现。 若要执行此操作，定义自己的函数与具有相同签名`AtlThrow`和 #define`AtlThrow`为你的函数的名称。 这必须包括 atlexcept.h （这意味着它必须在包含任何 ATL 标头，因为 atlbase.h 包括 atlexcept.h 之前完成） 之前完成。 属性函数`__declspec(noreturn)`以避免出现虚假的 SAL 警告。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>要求

**标头：** atldef.h  

##  <a name="atlthrowlastwin32"></a>  AtlThrowLastWin32

调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>备注

此函数跟踪的结果`GetLastError`到调试器。

如果 _ATL_NO_EXCEPTIONS 未定义 MFC 项目中，此函数将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)上返回的值基于`GetLastError`。

如果在 ATL 项目中未定义 _ATL_NO_EXCEPTIONS，该函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。

如果定义 _ATL_NO_EXCEPTIONS，则该函数将导致断言失败而不是引发异常。  

## <a name="requirements"></a>要求

**标头：** atldef.h

## <a name="see-also"></a>请参阅

[函数](../../atl/reference/atl-functions.md)<br/>
[调试和错误报告宏](../../atl/reference/debugging-and-error-reporting-macros.md)

