---
title: CW2CWEX 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee4314e4f2d31e499c01049d1fbec579f16c2849
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765355"
---
# <a name="cw2cwex-class"></a>CW2CWEX 类

字符串转换宏 CW2CTEX 和 CT2CWEX 和 typedef CW2W 使用此类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<int t_nBufferLength = 128>  
class CW2CWEX
```

#### <a name="parameters"></a>参数

*t_nBufferLength*  
在转换过程中所使用的缓冲区的大小。 默认长度为 128 个字节。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|构造函数。|
|[CW2CWEX:: ~ CW2CWEX](#dtor)|析构函数。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|转换运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|将源字符串存储的数据成员。|

## <a name="remarks"></a>备注

除非需要额外的功能，在代码中使用 CW2CTEX、 CT2CWEX 或 CW2W。

此类安全地在循环中使用，不会造成堆栈溢出。 默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。

下列宏基于此类：

- CW2CTEX

- CT2CWEX

以下 typedef 基于此类：

- CW2W

这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。

## <a name="example"></a>示例

请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。

## <a name="requirements"></a>要求

**标头：** atlconv.h

##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX

构造函数。

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>参数

*psz*  
要转换的文本字符串。

*nCodePage*  
代码页中。 不使用此类中。

### <a name="remarks"></a>备注

分配在转换过程中所使用的缓冲区。

##  <a name="dtor"></a>  CW2CWEX:: ~ CW2CWEX

析构函数。

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>备注

释放分配的缓冲区。

##  <a name="m_psz"></a>  CW2CWEX::m_psz

将源字符串存储的数据成员。

```
LPCWSTR m_psz;
```

##  <a name="operator_lpcwstr"></a>  CW2CWEX::operator LPCWSTR

转换运算符。

```  
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>返回值

返回文本字符串，键入 LPCWSTR。

## <a name="see-also"></a>请参阅

[CA2AEX 类](../../atl/reference/ca2aex-class.md)   
[CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
[CA2WEX 类](../../atl/reference/ca2wex-class.md)   
[CW2AEX 类](../../atl/reference/cw2aex-class.md)   
[CW2WEX 类](../../atl/reference/cw2wex-class.md)   
[类概述](../../atl/atl-class-overview.md)
