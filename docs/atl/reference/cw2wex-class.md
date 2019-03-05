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
ms.openlocfilehash: d6d68f4f5c0f3532c39fee3f513e7b3102ec075d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299473"
---
# <a name="cw2wex-class"></a>CW2WEX 类

字符串转换宏 CW2TEX 和 CT2WEX 和 typedef CW2W 使用此类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <int t_nBufferLength = 128>
class CW2WEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
在转换过程中所使用的缓冲区的大小。 默认长度为 128 个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CW2WEX::CW2WEX](#cw2wex)|构造函数。|
|[CW2WEX::~CW2WEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CW2WEX::m_psz](#m_psz)|将源字符串存储的数据成员。|
|[CW2WEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用于存储转换后的字符串。|

## <a name="remarks"></a>备注

除非需要额外的功能，在代码中使用 CW2TEX、 CT2WEX 或 CW2W。

此类包含固定大小的静态缓冲区用于存储转换的结果。 如果结果太大而无法放入静态缓冲区，类分配内存使用**malloc**，当对象超出范围时释放内存。 这样可确保与不同的文本转换宏可在以前版本的 ATL，此类可以安全地在循环中使用和堆栈不会溢出。

如果类尝试分配内存堆和失败时，它将调用`AtlThrow`用 E_OUTOFMEMORY 自变量。

默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。

下列宏基于此类：

- CW2TEX

- CT2WEX

以下 typedef 基于此类：

- CW2W

这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。

## <a name="requirements"></a>要求

**标头：** atlconv.h

##  <a name="cw2wex"></a>  CW2WEX::CW2WEX

构造函数。

```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*nCodePage*<br/>
代码页中。 不使用此类中。

### <a name="remarks"></a>备注

创建所需的翻译的缓冲区。

##  <a name="dtor"></a>  CW2WEX::~CW2WEX

析构函数...

```
~CW2WEX() throw();
```

### <a name="remarks"></a>备注

释放分配的缓冲区。

##  <a name="m_psz"></a>  CW2WEX::m_psz

将源字符串存储的数据成员。

```
LPWSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2WEX::m_szBuffer

静态缓冲区，用于存储转换后的字符串。

```
wchar_t m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpwstr"></a>  CW2WEX::operator LPWSTR

强制转换运算符。

```
operator LPWSTR() const throw();
```

### <a name="return-value"></a>返回值

返回文本字符串，键入 LPWSTR。

## <a name="see-also"></a>请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 类](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
