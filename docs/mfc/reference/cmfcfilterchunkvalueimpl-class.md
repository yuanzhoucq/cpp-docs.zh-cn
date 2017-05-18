---
title: "CMFCFilterChunkValueImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCFilterChunkValueImpl class
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8de3cba19a60b8022df96a9edafd13677fa3fecb
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfilterchunkvalueimpl-class"></a>CMFCFilterChunkValueImpl 类
这是一个类，这样可以简化区块和属性值对逻辑。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destructs 对象。|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|构造对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](#clear)|清除 ChunkValue。|  
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|将此文本块复制到一种结构描述的特征的块。|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|初始化此块值从另一个的值。|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|检索块区 GUID。|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|检索块区 PID (属性 ID)。|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|获取消息类型的分块。|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|检索字符串值。|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|为已分配 propvariant 检索的值。|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|返回一个未分配的非 （内部值） 的值。|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|检查此属性的值是否为有效。|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|已重载。 将属性设置为布尔值的密钥。|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|通过指向 DWORD 键设置的属性。|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|由一个 filetime 的关键设置的属性。|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|通过为 int64 键设置的属性。|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|通过键给整型变量设置的属性|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|通过为长整型键设置的属性。|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|将属性设置成 SystemTime 的密钥。|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|通过为 Unicode 字符串的键设置的属性。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|一个设置分块的通用属性的帮助器函数。|  
  
## <a name="remarks"></a>备注  
 若要使用，您只需创建正确类型的 CMFCFilterChunkValueImpl 类  
  
 示例:  
  
 CMFCFilterChunkValueImpl 块;  
  
 hr = 块区。SetBoolValue(PKEY_IsAttachment, true);  
  
 或  
  
 hr = 块区。SetFileTimeValue (PKEY_ItemDate，ftLastModified);  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="clear"></a>CMFCFilterChunkValueImpl::Clear  
 清除 ChunkValue。  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl  
 构造对象。  
  
```  
CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl  
 Destructs 对象。  
  
```  
virtual ~CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk  
 将此文本块复制到一种结构描述的特征的块。  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>参数  
 `pStatChunk`  
 指向目标值，描述在块区的特征的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyFrom  
 初始化此块值从另一个的值。  
  
```  
void CopyFrom (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>参数  
 `pValue`  
 指定要从复制的源值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID  
 检索块区 GUID。  
  
```  
REFGUID GetChunkGUID() const;  
```  
  
### <a name="return-value"></a>返回值  
 对标识区块的 GUID 的引用。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID  
 检索块区 PID (属性 ID)。  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>返回值  
 DWORD 值，该值包含属性 id。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType  
 检索的消息块类型。  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>返回值  
 CHUNKSTATE 枚举值，指定当前块是文本类型属性或值类型属性。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getstring"></a>CMFCFilterChunkValueImpl::GetString  
 检索字符串值。  
  
```  
CString &GetString();
```  
  
### <a name="return-value"></a>返回值  
 包含文本块值的字符串。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue  
 为已分配 propvariant 检索的值。  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>参数  
 `ppPropVariant`  
 当函数返回时，此参数将包含文本块值。  
  
### <a name="return-value"></a>返回值  
 如果已成功分配 PROPVARIANT 并已成功将区块值复制到，则为 S_OK `ppPropVariant`; 否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc  
 返回未分配的非 （内部值） 值。  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>返回值  
 返回当前块值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid  
 检查此属性的值是否为有效。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果当前的区块值有效，则为否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue  
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
 `pkey`  
 指定一个属性键。  
  
 `bVal`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk  
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
 `pkey`  
 指定一个属性键。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue  
 通过指向 DWORD 键设置的属性。  
  
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
 `pkey`  
 指定一个属性键。  
  
 `dwVal`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue  
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
 `pkey`  
 指定一个属性键。  
  
 `dtVal`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value  
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
 `pkey`  
 指定一个属性键。  
  
 `nVal`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue  
 将属性设置为 int。 密钥  
  
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
 `pkey`  
 指定一个属性键。  
  
 `nVal`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue  
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
 `pkey`  
 指定一个属性键。  
  
 `lVal`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue  
 将属性设置成 SystemTime 的密钥。  
  
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
 `pkey`  
 指定一个属性键。  
  
 `systemTime`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
##  <a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue  
 通过为 Unicode 字符串的键设置的属性。  
  
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
 `pkey`  
 指定一个属性键。  
  
 `pszValue`  
 指定要设置的块区值。  
  
 `chunkType`  
 标志指示此消息块是否包含文本类型或值类型属性。 标志值取自 CHUNKSTATE 枚举。  
  
 `locale`  
 与的文本块相关联的子语言和语言。 区块的区域设置是文档的索引器用于执行正确的断字的文本。 如果分块是既不文本类型，也不具有数据类型为 VT_LPWSTR、 VT_LPSTR 或 VT_BSTR 的值类型，则忽略此字段。  
  
 `cwcLenSource`  
 以字符为单位从中派生当前文本块的源文本的长度。 零值表示字符的字符的源文本和派生的文本之间的对应关系。 一个非零值表示没有这种直接的对应关系，存在。  
  
 `cwcStartSource`  
 从中派生的文本块的源文本开始在源块区中的偏移量。  
  
 `chunkBreakType`  
 将与当前块区分开的上一个块区的分页符的类型。 值为从 CHUNK_BREAKTYPE 枚举。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误代码。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

