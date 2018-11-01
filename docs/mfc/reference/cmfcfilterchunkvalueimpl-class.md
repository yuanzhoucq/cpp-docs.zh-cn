---
title: CMFCFilterChunkValueImpl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: a59cf087a52bd7b6a2eaa00d3091047e93e14d4d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666838"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 类

这是一个类，这样可以简化区块和属性值对逻辑。

## <a name="syntax"></a>语法

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destructs 对象。|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|构造对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|清除 ChunkValue。|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|将此文本块复制到块区的特征描述的结构。|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|初始化此区块的值从另一个值。|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|检索块区的 GUID。|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|检索块区 PID (属性 ID)。|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|获取消息的分块类型。|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|检索字符串值。|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|为已分配 propvariant 检索的值。|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|返回一个非分配 （内部值） 值。|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|检查此属性的值是否有效。|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|已重载。 将属性设置为布尔值的密钥。|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|通过指向 DWORD 键设置的属性。|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|将属性设置为 filetime 的密钥。|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|通过为 int64 键设置的属性。|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|将属性设置为 int。 按键|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|将属性设置为长整型的密钥。|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|将属性设置成 SystemTime 按键。|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|将属性设置为 Unicode 字符串的密钥。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|一个设置分块的通用属性的帮助器函数。|

## <a name="remarks"></a>备注

若要使用，您只需创建正确类型的 CMFCFilterChunkValueImpl 类

示例:

CMFCFilterChunkValueImpl 区块;

hr = 区块。SetBoolValue(PKEY_IsAttachment, true);

或

hr = 区块。SetFileTimeValue (PKEY_ItemDate，ftLastModified);

## <a name="inheritance-hierarchy"></a>继承层次结构

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear

清除 ChunkValue。

```
void Clear();
```

### <a name="remarks"></a>备注

##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

构造对象。

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>备注

##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl

Destructs 对象。

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>备注

##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk

将此文本块复制到块区的特征描述的结构。

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>参数

*pStatChunk*<br/>
一个指向目标值，描述在块区的特征。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom

初始化此区块的值从另一个值。

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>参数

*pValue*<br/>
指定要从复制的源值。

### <a name="remarks"></a>备注

##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID

检索块区的 GUID。

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>返回值

对标识块的 GUID 的引用。

### <a name="remarks"></a>备注

##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID

检索块区 PID (属性 ID)。

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>返回值

DWORD 值，该值包含属性 id。

### <a name="remarks"></a>备注

##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType

检索块区类型。

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>返回值

CHUNKSTATE 枚举值，指定当前区块是文本类型的属性或值类型属性。

### <a name="remarks"></a>备注

##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString

检索字符串值。

```
CString &GetString();
```

### <a name="return-value"></a>返回值

包含块区值的字符串。

### <a name="remarks"></a>备注

##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue

为已分配 propvariant 检索的值。

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>参数

*ppPropVariant*<br/>
当函数返回时，此参数包含块区值。

### <a name="return-value"></a>返回值

如果已成功分配 PROPVARIANT 和区块值已成功复制到，则为 S_OK *ppPropVariant*; 否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc

返回非分配 （内部值） 值。

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>返回值

返回当前的块区值。

### <a name="remarks"></a>备注

##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid

检查此属性的值是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果当前的块区值有效，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue

已重载。 将属性设置为布尔值的密钥。

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*bVal*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk

一个设置分块的通用属性的帮助器函数。

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue

将属性设置为 DWORD 按键。

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*dwVal*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue

将属性设置为 filetime 的密钥。

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*dtVal*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value

通过为 int64 键设置的属性。

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*nVal*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue

将属性设置为 int。 按键

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*nVal*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue

将属性设置为长整型的密钥。

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*lVal*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue

将属性设置成 SystemTime 按键。

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*systemTime*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue

将属性设置为 Unicode 字符串的密钥。

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>参数

*主键*<br/>
指定一个属性键。

*pszValue*<br/>
指定要设置的块区值。

*chunkType*<br/>
标志指示此块包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*locale*<br/>
语言和子语言的文本块与相关联。 文档索引器使用区块区域设置执行正确的断字的文本。 如果区块是文本类型既不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。

*cwcLenSource*<br/>
中从其派生当前文本块的源文本的字符长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系存在。

*cwcStartSource*<br/>
从中派生区块的源文本开始的源区块中偏移量。

*chunkBreakType*<br/>
分页符将与当前的块区分开的上一个块区的类型。 从 CHUNK_BREAKTYPE 枚举的有效值。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为错误代码。

### <a name="remarks"></a>备注

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
