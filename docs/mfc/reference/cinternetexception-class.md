---
title: C 互联网例外类
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372408"
---
# <a name="cinternetexception-class"></a>C 互联网例外类

表示与 Internet 操作相关的异常条件。

## <a name="syntax"></a>语法

```
class CInternetException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C 互联网例外：C 互联网例外](#cinternetexception)|构造 `CInternetException` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C 互联网例外：m_dwContext](#m_dwcontext)|与导致异常的操作关联的上下文值。|
|[C 互联网例外：m_dwError](#m_dwerror)|导致异常的错误。|

## <a name="remarks"></a>备注

该`CInternetException`类包括两个公共数据成员：一个保存与异常关联的错误代码，另一个保留与错误关联的 Internet 应用程序的上下文标识符。

有关 Internet 应用程序的上下文标识符的详细信息，请参阅[使用 WinInet 进行 Internet 编程的文章](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>要求

**标题：** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>C 互联网例外：C 互联网例外

创建`CInternetException`对象时将调用此成员函数。

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>参数

*dwError*<br/>
导致异常的错误。

### <a name="remarks"></a>备注

要引发 CInternetException，请致电 MFC 全局函数[AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)。

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>C 互联网例外：m_dwContext

与相关 Internet 操作关联的上下文值。

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>备注

上下文标识符最初在[CInternetSession](../../mfc/reference/cinternetsession-class.md)中指定，并由 MFC 传递给[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- 和[CInternetFile](../../mfc/reference/cinternetfile-class.md)派生类。 您可以覆盖此默认值，并分配任何*dwContext*参数您选择的值。 *dwContext*与给定对象的任何操作相关联。 *dwContext*标识 CInternetSession 返回的操作的状态信息[：：onStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)。

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>C 互联网例外：m_dwError

导致异常的错误。

```
DWORD m_dwError;
```

### <a name="remarks"></a>备注

此错误值可能是在 WINERROR 中找到的系统错误代码。H，或 WININET 的错误值。H。

有关 Win32 错误代码的列表，请参阅[错误代码](/windows/win32/Debug/system-error-codes)。 有关特定于 Internet 的错误消息的列表，请参阅。 这两个主题都在 Windows SDK 中。

## <a name="see-also"></a>另请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)
