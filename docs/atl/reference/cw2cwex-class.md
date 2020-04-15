---
title: CW2CWEX 类
ms.date: 11/04/2016
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
ms.openlocfilehash: 07dd0319586054403d8ed0c8efc813b4061e355a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330435"
---
# <a name="cw2cwex-class"></a>CW2CWEX 类

此类由字符串转换宏 CW2CTEX 和 CT2CWEX 以及类型 def CW2W 使用。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template<int t_nBufferLength = 128>
class CW2CWEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
翻译过程中使用的缓冲区的大小。 默认长度为 128 字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CW2CWEX：CW2CWEX](#cw2cwex)|构造函数。|
|[CW2CWEX：*CW2CWEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CW2CWEX：：运营商LPCWSTR](#operator_lpcwstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CW2CWEX：：m_psz](#m_psz)|存储源字符串的数据成员。|

## <a name="remarks"></a>备注

除非需要额外的功能，否则请使用代码中的 CW2CTEX、CT2CWEX 或 CW2W。

此类在循环中使用是安全的，并且不会溢出堆栈。 默认情况下，ATL 转换类和宏使用当前线程的 ANSI 代码页进行转换。

以下宏基于此类：

- CW2CTEX

- CT2CWEX

以下类型def基于此类：

- CW2W

有关这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

有关使用这些字符串转换宏的示例，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="requirements"></a>要求

**标题：** atlconv.h

## <a name="cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX：CW2CWEX

构造函数。

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*n代码页*<br/>
代码页。 此类中未使用。

### <a name="remarks"></a>备注

分配翻译过程中使用的缓冲区。

## <a name="cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX：*CW2CWEX

析构函数。

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>备注

释放分配的缓冲区。

## <a name="cw2cwexm_psz"></a><a name="m_psz"></a>CW2CWEX：：m_psz

存储源字符串的数据成员。

```
LPCWSTR m_psz;
```

## <a name="cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX：：运营商LPCWSTR

转换运算符。

```
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>返回值

将文本字符串返回为 LPCWSTR 类型。

## <a name="see-also"></a>另请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 类](../../atl/reference/cw2aex-class.md)<br/>
[CW2WEX 类](../../atl/reference/cw2wex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
