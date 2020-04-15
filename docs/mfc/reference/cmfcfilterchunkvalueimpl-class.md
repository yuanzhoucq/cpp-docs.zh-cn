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
ms.openlocfilehash: 2c90a873033516710077d31c8bb8af5fb5172ca6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367507"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 类

这是一个简化块和属性值对逻辑的类。

## <a name="syntax"></a>语法

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 过滤器块值 impl：_CMFC 过滤器块值 impl](#_dtorcmfcfilterchunkvalueimpl)|析构对象。|
|[CMFC 过滤器块值 impl：：CMFC 过滤器块值](#cmfcfilterchunkvalueimpl)|构造对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC过滤器Chunkvalueimpl：：清除](#clear)|清除块值。|
|[CMFC 过滤器块值 impl：：复制块](#copychunk)|将此块复制到描述块特征的结构。|
|[CMFC过滤器chunk值：：从复制](#copyfrom)|从其他值初始化此块值。|
|[CMFC过滤器块值：：获取块状](#getchunkguid)|检索块 GUID。|
|[CMFC过滤器块值：：获取块状PID](#getchunkpid)|检索块 PID（属性 ID）。|
|[CMFC 过滤器块值：：获取块类型](#getchunktype)|获取块类型。|
|[CMFC过滤器块值：：获取字符串](#getstring)|检索字符串值。|
|[CMFC过滤器Chunkvalueimpl：获取价值](#getvalue)|检索该值作为分配的道具变量。|
|[CMFC过滤器Chunkvalueimpl：：获取ValueNoalloc](#getvaluenoalloc)|返回未分配（内部值）值。|
|[CMFC过滤器chunk值：：有效](#isvalid)|检查此属性值是否有效。|
|[CMFC过滤器块值：：SetBoolValue](#setboolvalue)|已重载。 按键将属性设置到布尔。|
|[CMFC过滤器块值：：设置Word值](#setdwordvalue)|按键将属性设置到 DWORD。|
|[CMFC过滤器块值：：设置文件时间值](#setfiletimevalue)|按键将属性设置到文件时间。|
|[CMFC过滤器块值：setint64值](#setint64value)|按键将属性设置到 int64。|
|[CMFC 过滤器块值：：setintValue](#setintvalue)|按键将属性设置到 int。|
|[CMFC 过滤器块值：：设置长值](#setlongvalue)|按键将属性设置为 LONG。|
|[CMFC 过滤器块值：：设置系统时间值](#setsystemtimevalue)|按键将属性设置到系统时间。|
|[CMFC 过滤器块值：：设置文本值](#settextvalue)|按键将属性设置到 Unicode 字符串。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMFC 过滤器块值 impl：：设置块](#setchunk)|设置块公共属性的帮助器函数。|

## <a name="remarks"></a>备注

使用时，只需创建一个 CMFCFilterChunkValueImpl 类，即可获得正确的类型

示例：

CMFC过滤器块值块;

hr = 块。SetBoolValue（PKEY_IsAttachment，真实）;

or

hr = 块。设置文件时间值（PKEY_ItemDate，英尺已修改）;

## <a name="inheritance-hierarchy"></a>继承层次结构

`ATL::IFilterChunkValue`

[CMFC过滤器块值](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFC过滤器Chunkvalueimpl：：清除

清除块值。

```
void Clear();
```

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFC 过滤器块值 impl：：CMFC 过滤器块值

构造对象。

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFC 过滤器块值 impl：_CMFC 过滤器块值 impl

析构对象。

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFC 过滤器块值 impl：：复制块

将此块复制到描述块特征的结构。

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>参数

*pStatChunk*<br/>
指向描述块特征的目标值的指针。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFC过滤器chunk值：：从复制

从其他值初始化此块值。

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>参数

*pValue*<br/>
指定要从中复制的源值。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFC过滤器块值：：获取块状

检索块 GUID。

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>返回值

对标识块的 GUID 的引用。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFC过滤器块值：：获取块状PID

检索块 PID（属性 ID）。

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>返回值

包含属性 ID 的 DWORD 值。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFC 过滤器块值：：获取块类型

检索块类型。

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>返回值

一个 CHUNKSTATE 枚举值，它指定当前块是文本类型属性还是值类型属性。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFC过滤器块值：：获取字符串

检索字符串值。

```
CString &GetString();
```

### <a name="return-value"></a>返回值

包含块值的字符串。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFC过滤器Chunkvalueimpl：获取价值

检索该值作为分配的道具变量。

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>参数

*ppPropVariant*<br/>
当函数返回时，此参数包含块值。

### <a name="return-value"></a>返回值

S_OK如果 PROPVARIANT 已成功分配，并且块值已成功复制到*ppPropvariant;* 否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFC过滤器Chunkvalueimpl：：获取ValueNoalloc

返回未分配（内部值）值。

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>返回值

返回当前块值。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFC过滤器chunk值：：有效

检查此属性值是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果当前块值有效，则为 TRUE;如果当前块值有效，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFC过滤器块值：：SetBoolValue

已重载。 按键将属性设置到布尔。

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

*皮基*<br/>
指定属性键。

*bVal*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFC 过滤器块值 impl：：设置块

设置块公共属性的帮助器函数。

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

*皮基*<br/>
指定属性键。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFC过滤器块值：：设置Word值

按键将属性设置为 DWORD。

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

*皮基*<br/>
指定属性键。

*德瓦尔*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFC过滤器块值：：设置文件时间值

按键将属性设置为文件时间。

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

*皮基*<br/>
指定属性键。

*德瓦尔*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFC过滤器块值：setint64值

按键将属性设置为 int64。

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

*皮基*<br/>
指定属性键。

*恩瓦尔*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFC 过滤器块值：：setintValue

按键将属性设置为 int。

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

*皮基*<br/>
指定属性键。

*恩瓦尔*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFC 过滤器块值：：设置长值

按键将属性设置为 LONG。

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

*皮基*<br/>
指定属性键。

*lVal*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFC 过滤器块值：：设置系统时间值

按键将属性设置到系统时间。

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

*皮基*<br/>
指定属性键。

*系统时间*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFC 过滤器块值：：设置文本值

按键将属性设置到 Unicode 字符串。

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

*皮基*<br/>
指定属性键。

*pszValue*<br/>
指定要设置的块值。

*块类型*<br/>
标志指示此块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。

*现场*<br/>
与文本块关联的语言和子语言。 块区域设置由文档索引器用于执行正确的文本断字。 如果块既不是文本类型，也不是数据类型为VT_LPWSTR、VT_LPSTR 或VT_BSTR的值类型，则此字段将被忽略。

*cwcLen来源*<br/>
派生当前块的源文本的长度（ 零值表示源文本和派生文本之间的字符对应。 非零值表示不存在此类直接对应关系。

*cwcStart来源*<br/>
派生块的源文本从其开始的偏移量。

*块中断类型*<br/>
将前一个块与当前块分隔的中断类型。 值来自CHUNK_BREAKTYPE枚举。

### <a name="return-value"></a>返回值

S_OK如果成功;否则是错误代码。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
