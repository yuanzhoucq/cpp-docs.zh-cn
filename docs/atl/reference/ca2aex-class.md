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
ms.openlocfilehash: 712e663ab58e2c9de4e2f25090b84b35d0bced71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247633"
---
# <a name="ca2aex-class"></a>CA2AEX 类

字符串转换宏 CA2TEX 和 CT2AEX 和 typedef CA2A 使用此类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template <int t_nBufferLength = 128>
class CA2AEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
在转换过程中所使用的缓冲区的大小。 默认长度为 128 个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|构造函数。|
|[CA2AEX::~CA2AEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CA2AEX::operator LPSTR](#operator_lpstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CA2AEX::m_psz](#m_psz)|将源字符串存储的数据成员。|
|[CA2AEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用于存储转换后的字符串。|

## <a name="remarks"></a>备注

除非需要额外的功能，则使用 CA2TEX、 CT2AEX 或 CA2A 中你自己的代码。

此类包含固定大小的静态缓冲区用于存储转换的结果。 如果结果太大而无法放入静态缓冲区，类分配内存使用**malloc**，当对象超出范围时释放内存。 这样可确保与不同的文本转换宏可在以前版本的 ATL，此类可以安全地在循环中使用和堆栈不会溢出。

如果类尝试分配内存堆和失败时，它将调用`AtlThrow`用 E_OUTOFMEMORY 自变量。

默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。

下列宏基于此类：

- CA2TEX

- CT2AEX

以下 typedef 基于此类：

- CA2A

这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。

## <a name="requirements"></a>要求

**标头：** atlconv.h

##  <a name="ca2aex"></a>  CA2AEX::CA2AEX

构造函数。

```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*nCodePage*<br/>
未使用此类。

### <a name="remarks"></a>备注

创建所需的翻译的缓冲区。

##  <a name="dtor"></a>  CA2AEX::~CA2AEX

析构函数。

```
~CA2AEX() throw();
```

### <a name="remarks"></a>备注

释放分配的缓冲区。

##  <a name="m_psz"></a>  CA2AEX::m_psz

将源字符串存储的数据成员。

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CA2AEX::m_szBuffer

静态缓冲区，用于存储转换后的字符串。

```
char m_szBuffer[ t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CA2AEX::operator LPSTR

转换运算符。

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>返回值

返回文本字符串，键入 LPSTR。

## <a name="see-also"></a>请参阅

[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 类](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 类](../../atl/reference/cw2wex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
