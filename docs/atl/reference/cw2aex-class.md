---
title: CW2AEX 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e10650235298e7a5b2931e59c39cb21a5374d0b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087586"
---
# <a name="cw2aex-class"></a>CW2AEX 类

字符串转换宏 CT2AEX、 CW2TEX、 CW2CTEX，和 CT2CAEX 和 typedef CW2A 使用此类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*<br/>
在转换过程中所使用的缓冲区的大小。 默认长度为 128 个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|构造函数。|
|[CW2AEX:: ~ CW2AEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CW2AEX::operator LPSTR](#operator_lpstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|将源字符串存储的数据成员。|
|[CW2AEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用于存储转换后的字符串。|

## <a name="remarks"></a>备注

除非需要额外的功能，在代码中使用 CT2AEX、 CW2TEX、 CW2CTEX、 CT2CAEX 或 CW2A。

此类包含固定大小的静态缓冲区用于存储转换的结果。 如果结果太大而无法放入静态缓冲区，类分配内存使用**malloc**，当对象超出范围时释放内存。 这样可确保与不同的文本转换宏可在以前版本的 ATL，此类可以安全地在循环中使用和堆栈不会溢出。

如果类尝试分配内存堆和失败时，它将调用`AtlThrow`用 E_OUTOFMEMORY 自变量。

默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。 如果你想要重写特定转换该行为，作为类的构造函数的第二个参数指定代码页。

下列宏基于此类：

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

以下 typedef 基于此类：

- CW2A

这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。

## <a name="requirements"></a>要求

**标头：** atlconv.h

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
用来执行转换的代码页。 请参阅 Windows SDK 函数的代码页参数讨论[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)的更多详细信息。

### <a name="remarks"></a>备注

分配在转换过程中所使用的缓冲区。

##  <a name="dtor"></a>  CW2AEX:: ~ CW2AEX

析构函数。

```
~CW2AEX() throw();
```

### <a name="remarks"></a>备注

释放分配的缓冲区。

##  <a name="m_psz"></a>  CW2AEX::m_psz

将源字符串存储的数据成员。

```
LPSTR m_psz;
```

##  <a name="m_szbuffer"></a>  CW2AEX::m_szBuffer

静态缓冲区，用于存储转换后的字符串。

```
char m_szBuffer[t_nBufferLength];
```

##  <a name="operator_lpstr"></a>  CW2AEX::operator LPSTR

转换运算符。

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>返回值

返回文本字符串，键入 LPSTR。

## <a name="see-also"></a>请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 类](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX 类](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 类](../../atl/reference/cw2wex-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
