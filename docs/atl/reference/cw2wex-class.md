---
title: CW2WEX 类
ms.date: 11/04/2016
f1_keywords:
- CW2WEX
- ATLCONV/ATL::CW2WEX
- ATLCONV/ATL::CW2WEX::CW2WEX
- ATLCONV/ATL::CW2WEX::m_psz
- ATLCONV/ATL::CW2WEX::m_szBuffer
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
ms.openlocfilehash: b116775a595f9fb3612d46e19526cf1396f85002
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330352"
---
# <a name="cw2wex-class"></a>CW2WEX 类

此类由字符串转换宏 CW2TEX 和 CT2WEX 以及类型 def CW2W 使用。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
翻译过程中使用的缓冲区的大小。 默认长度为 128 字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CW2WEX：CW2WEX](#cw2wex)|构造函数。|
|[CW2WEX：*CW2WEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CW2WEX：：操作员LPWSTR](#operator_lpwstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CW2WEX：m_psz](#m_psz)|存储源字符串的数据成员。|
|[CW2WEX：m_szBuffer](#m_szbuffer)|用于存储转换后的字符串的静态缓冲区。|

## <a name="remarks"></a>备注

除非需要额外的功能，否则请使用代码中的 CW2TEX、CT2WEX 或 CW2W。

此类包含一个固定大小的静态缓冲区，用于存储转换的结果。 如果结果太大而无法放入静态缓冲区中，则类将使用**malloc**分配内存，当对象超出范围时释放内存。 这可确保与早期版本的 ATL 中提供的文本转换宏不同，此类在循环中使用是安全的，并且不会溢出堆栈。

如果类尝试在堆上分配内存而失败，它将调用`AtlThrow`E_OUTOFMEMORY参数。

默认情况下，ATL 转换类和宏使用当前线程的 ANSI 代码页进行转换。

以下宏基于此类：

- CW2TEX

- CT2WEX

以下类型def基于此类：

- CW2W

有关这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

有关使用这些字符串转换宏的示例，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="requirements"></a>要求

**标题：** atlconv.h

## <a name="cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX：CW2WEX

构造函数。

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*n代码页*<br/>
代码页。 此类中未使用。

### <a name="remarks"></a>备注

创建转换所需的缓冲区。

## <a name="cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX：*CW2WEX

析构函数。

```
~CW2WEX() throw();
```

### <a name="remarks"></a>备注

释放分配的缓冲区。

## <a name="cw2wexm_psz"></a><a name="m_psz"></a>CW2WEX：m_psz

存储源字符串的数据成员。

```
LPWSTR m_psz;
```

## <a name="cw2wexm_szbuffer"></a><a name="m_szbuffer"></a>CW2WEX：m_szBuffer

用于存储转换后的字符串的静态缓冲区。

```
wchar_t m_szBuffer[t_nBufferLength];
```

## <a name="cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX：：操作员LPWSTR

强制操作运算符。

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>返回值

将文本字符串返回为 LPWSTR 类型。

## <a name="see-also"></a>另请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 类](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
