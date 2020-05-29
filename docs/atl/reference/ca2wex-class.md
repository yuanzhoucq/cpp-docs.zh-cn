---
title: CA2WEX 类
ms.date: 11/04/2016
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
ms.openlocfilehash: a710034c5d94a8fb093a2b6a2a52373e2bab2d6d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168496"
---
# <a name="ca2wex-class"></a>CA2WEX 类

此类由字符串转换宏 CA2TEX、CA2CTEX、CT2WEX、CT2CWEX 和 typedef CA2W 使用。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
template <int t_nBufferLength = 128>
class CA2WEX
```

### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
在转换过程中使用的缓冲区大小。 默认长度为128个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CA2WEX::CA2WEX](#ca2wex)|构造函数。|
|[CA2WEX：： ~ CA2WEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CA2WEX：： operator LPWSTR](#operator_lpwstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CA2WEX：： m_psz](#m_psz)|存储源字符串的数据成员。|
|[CA2WEX：： m_szBuffer](#m_szbuffer)|用于存储转换后的字符串的静态缓冲区。|

## <a name="remarks"></a>备注

除非需要额外的功能，否则请在代码中使用 CA2TEX、CA2CTEX、CT2WEX、CT2CWEX 或 CA2W。

此类包含固定大小的静态缓冲区，该缓冲区用于存储转换的结果。 如果结果太大而无法放入静态缓冲区中，则类将使用**malloc**分配内存，当对象超出范围时释放内存。 这可以确保不同于早期版本的 ATL 中提供的文本转换宏，此类可安全地在循环中使用，并且不会溢出堆栈。

如果类尝试在堆上分配内存并失败，则它将使用 E_OUTOFMEMORY `AtlThrow`的参数调用。

默认情况下，ATL 转换类和宏将当前线程的 ANSI 代码页用于转换。 如果要重写特定转换的行为，请将代码页指定为该类的构造函数的第二个参数。

以下宏基于此类：

- CA2TEX

- CA2CTEX

- CT2WEX

- CT2CWEX

以下 typedef 基于此类：

- CA2W

有关这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

有关使用这些字符串转换宏的示例，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="requirements"></a>要求

**标头：** atlconv。h

## <a name="ca2wexca2wex"></a><a name="ca2wex"></a>CA2WEX::CA2WEX

构造函数。

```cpp
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*nCodePage*<br/>
用于执行转换的代码页。 有关更多详细信息，请参阅 Windows SDK 函数的代码页参数讨论[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) 。

### <a name="remarks"></a>备注

分配在转换过程中使用的缓冲区。

## <a name="ca2wexca2wex"></a><a name="dtor"></a>CA2WEX：： ~ CA2WEX

析构函数。

```cpp
~CA2WEX() throw();
```

### <a name="remarks"></a>备注

释放已分配的缓冲区。

## <a name="ca2wexm_psz"></a><a name="m_psz"></a>CA2WEX：： m_psz

存储源字符串的数据成员。

```cpp
LPWSTR m_psz;
```

## <a name="ca2wexm_szbuffer"></a><a name="m_szbuffer"></a>CA2WEX：： m_szBuffer

用于存储转换后的字符串的静态缓冲区。

```cpp
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="ca2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CA2WEX：： operator LPWSTR

转换运算符。

```cpp
operator LPWSTR() const throw();
```

### <a name="return-value"></a>返回值

以 LPWSTR 类型返回文本字符串。

## <a name="see-also"></a>另请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CW2AEX 类](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 类](../../atl/reference/cw2wex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
