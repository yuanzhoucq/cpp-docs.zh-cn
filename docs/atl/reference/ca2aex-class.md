---
title: CA2AEX 类
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168522"
---
# <a name="ca2aex-class"></a>CA2AEX 类

此类由字符串转换宏 CA2TEX 和 CT2AEX 以及 typedef CA2A 使用。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
在转换过程中使用的缓冲区大小。 默认长度为128个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|构造函数。|
|[CA2AEX：： ~ CA2AEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CA2AEX：： operator LPSTR](#operator_lpstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CA2AEX：： m_psz](#m_psz)|存储源字符串的数据成员。|
|[CA2AEX：： m_szBuffer](#m_szbuffer)|用于存储转换后的字符串的静态缓冲区。|

## <a name="remarks"></a>备注

除非需要额外的功能，否则请在自己的代码中使用 CA2TEX、CT2AEX 或 CA2A。

此类包含固定大小的静态缓冲区，该缓冲区用于存储转换的结果。 如果结果太大而无法放入静态缓冲区中，则类将使用**malloc**分配内存，当对象超出范围时释放内存。 这可以确保不同于早期版本的 ATL 中提供的文本转换宏，此类可安全地在循环中使用，并且不会溢出堆栈。

如果类尝试在堆上分配内存并失败，则它将使用 E_OUTOFMEMORY `AtlThrow`的参数调用。

默认情况下，ATL 转换类和宏将当前线程的 ANSI 代码页用于转换。

以下宏基于此类：

- CA2TEX

- CT2AEX

以下 typedef 基于此类：

- CA2A

有关这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

有关使用这些字符串转换宏的示例，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="requirements"></a>要求

**标头：** atlconv。h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

构造函数。

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*nCodePage*<br/>
此类中未使用。

### <a name="remarks"></a>备注

创建转换所需的缓冲区。

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX：： ~ CA2AEX

析构函数。

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>备注

释放已分配的缓冲区。

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX：： m_psz

存储源字符串的数据成员。

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX：： m_szBuffer

用于存储转换后的字符串的静态缓冲区。

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX：： operator LPSTR

转换运算符。

```cpp
operator LPSTR() const throw();
```

### <a name="return-value"></a>返回值

以 LPSTR 类型返回文本字符串。

## <a name="see-also"></a>另请参阅

[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 类](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 类](../../atl/reference/cw2wex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
