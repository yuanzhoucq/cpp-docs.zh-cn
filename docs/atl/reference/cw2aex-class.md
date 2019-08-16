---
title: CW2AEX 类
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 4dda1cb9e54c44f7940475660bc629192b9ead61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496267"
---
# <a name="cw2aex-class"></a>CW2AEX 类

此类由字符串转换宏 CT2AEX、CW2TEX、CW2CTEX、CT2CAEX 和 typedef CW2A 使用。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
在转换过程中使用的缓冲区大小。 默认长度为128个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|构造函数。|
|[CW2AEX::~CW2AEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CW2AEX:: operator LPSTR](#operator_lpstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|存储源字符串的数据成员。|
|[CW2AEX::m_szBuffer](#m_szbuffer)|用于存储转换后的字符串的静态缓冲区。|

## <a name="remarks"></a>备注

除非需要额外的功能, 否则请在代码中使用 CT2AEX、CW2TEX、CW2CTEX、CT2CAEX 或 CW2A。

此类包含固定大小的静态缓冲区, 该缓冲区用于存储转换的结果。 如果结果太大而无法放入静态缓冲区中, 则类将使用**malloc**分配内存, 当对象超出范围时释放内存。 这可以确保不同于早期版本的 ATL 中提供的文本转换宏, 此类可安全地在循环中使用, 并且不会溢出堆栈。

如果类尝试在堆上分配内存并失败, 则它将调用`AtlThrow` E_OUTOFMEMORY 的参数。

默认情况下, ATL 转换类和宏将当前线程的 ANSI 代码页用于转换。 如果要重写特定转换的行为, 请将代码页指定为该类的构造函数的第二个参数。

以下宏基于此类:

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

以下 typedef 基于此类:

- CW2A

有关这些文本转换宏的讨论, 请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

有关使用这些字符串转换宏的示例, 请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="requirements"></a>要求

**标头:** atlconv。h

##  <a name="cw2aex"></a>  CW2AEX::CW2AEX

构造函数。

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*<br/>
要转换的文本字符串。

*nCodePage*<br/>
用于执行转换的代码页。 有关更多详细信息, 请参阅 Windows SDK 函数的代码页参数讨论[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) 。

### <a name="remarks"></a>备注

分配在转换过程中使用的缓冲区。

##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX

析构函数。

```
~CW2AEX() throw();
```

### <a name="remarks"></a>备注

释放已分配的缓冲区。

##  <a name="m_psz"></a>  CW2AEX::m_psz

存储源字符串的数据成员。

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

用于存储转换后的字符串的静态缓冲区。

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>CW2AEX:: operator LPSTR

转换运算符。

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>返回值

以 LPSTR 类型返回文本字符串。

## <a name="see-also"></a>请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 类](../../atl/reference/cw2wex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
