---
title: 调试和错误报告全局函数 |Microsoft 文档
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
ms.openlocfilehash: fb3257b5205587b27a83671ed8e610aad5373eef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364877"
---
# <a name="debugging-and-error-reporting-global-functions"></a>调试和错误报告全局函数
这些函数提供有用的调试和跟踪功能。  
  
|||  
|-|-|  
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|返回`GetLastError`HRESULT 的形式的错误代码。|  
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|将 Win32 错误代码转换为 HRESULT。|  
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|将设置**IErrorInfo**若要提供给客户端的错误详细信息。|  
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|引发 `CAtlException`。|  
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|调用此函数可根据 Windows 函数 `GetLastError` 的结果发出错误。|  
  
##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError  
 以 HRESULT 的形式返回调用线程的上一个错误代码值。  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>备注  
 `AtlHresultFromLastError` 调用`GetLastError`若要获取的最后一个错误，并将其转换为 HRESULT 使用后返回错误**HRESULT_FROM_WIN32**宏。  

### <a name="requirements"></a>要求  
 **标头：** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32  
 将 Win32 错误代码转换为 HRESULT。  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>参数  
 *error*  
 要转换的错误值。  
  
### <a name="remarks"></a>备注  
 将 Win32 错误代码转换为 HRESULT，使用宏**HRESULT_FROM_WIN32**。  
  
> [!NOTE]
>  而不是使用**HRESULT_FROM_WIN32(GetLastError())**，使用函数[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)。  

### <a name="requirements"></a>要求  
 **标头：** atlcomcli.h  

##  <a name="atlreporterror"></a>  AtlReportError  
 将设置`IErrorInfo`接口向客户端的对象提供错误信息。  
  
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
 `clsid`  
 [in]报告错误的对象的 CLSID。  
  
 `lpszDesc`  
 [in]描述错误的字符串。 Unicode 版本指定`lpszDesc`属于类型**LPCOLESTR**; ANSI 版本指定一种`LPCSTR`。  
  
 `iid`  
 [in]定义错误的接口的 IID 或`GUID_NULL`如果错误由操作系统定义的。  
  
 `hRes`  
 [in]`HRESULT`要返回到调用方。  
  
 `nID`  
 [in]存储的错误描述字符串资源标识符。 此值应介于 0x0200 和 0xFFFF，之间 （含）。 在调试版本中，**断言**时将导致`nID`没有有效的字符串进行索引。 在发布版本中的错误描述字符串将设置为"未知错误。"  
  
 `dwHelpID`  
 [in]错误帮助上下文标识符。  
  
 `lpszHelpFile`  
 [in]路径和名称的描述错误的帮助文件。  
  
 `hInst`  
 [in]资源句柄。 默认情况下，此参数是 **__AtlBaseModuleModule::GetResourceInstance**，其中 **__AtlBaseModuleModule**是全局实例[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)或类派生自它。  
  
### <a name="return-value"></a>返回值  
 如果`hRes`参数为非零，则返回的值`hRes`。 如果`hRes`为零，则的前四个版本`AtlReportError`返回`DISP_E_EXCEPTION`。 最后两个版本都会返回的结果宏**MAKE_HRESULT (1，FACILITY_ITF，** `nID` **)**。  
  
### <a name="remarks"></a>备注  
 字符串*lpszDesc*用作错误的文本说明。 当客户端收到`hRes`从返回`AtlReportError`，客户端可以访问**IErrorInfo**有关错误的详细信息的结构。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  不要使用`AtlReportError`c + + 中 catch 处理程序。 这些函数中的有些重写使用 ATL 字符串转换宏在内部，这反过来使用`_alloca`内部函数。 使用`AtlReportError`c + + catch 处理程序可能会导致 c + + catch 处理程序中的异常。  

### <a name="requirements"></a>要求  
 **标头：** atlcom.h  
    
##  <a name="atlthrow"></a>  AtlThrow  
 调用此函数可根据 `HRESULT` 状态代码发出错误。  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>参数  
 `hr`  
 标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 ATL 和 MFC 代码发生的错误条件时使用此函数。 它还可以从你自己的代码调用。 此函数的默认实现依赖于符号的定义 **_ATL_NO_EXCEPTIONS**和类型的项目，MFC 或 atl。  
  
 在所有情况下，此函数跟踪到调试器的 HRESULT。  
  
 在 Visual Studio 2015 Update 3 及更高版本，则此函数是特性化 __declspec （noreturn） 以避免虚假 SAL 警告。  
  
 如果 **_ATL_NO_EXCEPTIONS**未定义此函数在 MFC 项目中，将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)基于的 HRESULT 值。  
  
 如果 **_ATL_NO_EXCEPTIONS**未定义在 ATL 项目中，则函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。  
  
 如果 **_ATL_NO_EXCEPTIONS**是定义，该函数将导致断言失败而不是引发异常。  
  
 对于 ATL 项目，则可以提供您自己的 ATL 出现故障时要使用此函数的实现。 若要执行此操作，定义自己的函数与具有相同签名`AtlThrow`和 #define`AtlThrow`为您的函数的名称。 此操作必须包括 atlexcept.h （这意味着必须在包含任何 ATL 标头，因为 atlbase.h 包括 atlexcept.h 之前完成它） 之前执行。 属性函数`__declspec(noreturn)`以避免虚假 SAL 警告。  
  
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
  
 如果 **_ATL_NO_EXCEPTIONS**未定义此函数在 MFC 项目中，将引发[CMemoryException](../../mfc/reference/cmemoryexception-class.md)或[COleException](../../mfc/reference/coleexception-class.md)基于返回的值`GetLastError`.  
  
 如果 **_ATL_NO_EXCEPTIONS**未定义在 ATL 项目中，则函数将引发[CAtlException](../../atl/reference/catlexception-class.md)。  
  
 如果 **_ATL_NO_EXCEPTIONS**是定义，该函数将导致断言失败而不是引发异常。  

## <a name="requirements"></a>要求  
 **标头：** atldef.h  
   
     
## <a name="see-also"></a>请参阅  
 [函数](../../atl/reference/atl-functions.md)   
 [调试和错误报告宏](../../atl/reference/debugging-and-error-reporting-macros.md)









