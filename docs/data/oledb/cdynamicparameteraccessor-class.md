---
title: CDynamicParameterAccessor 类
ms.date: 02/14/2018
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
- ATL::CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor::GetParamCount
- CDynamicParameterAccessor.GetParamCount
- GetParamCount
- ATL.CDynamicParameterAccessor.GetParamCount
- GetParamIO
- CDynamicParameterAccessor::GetParamIO
- ATL.CDynamicParameterAccessor.GetParamIO
- CDynamicParameterAccessor.GetParamIO
- ATL::CDynamicParameterAccessor::GetParamIO
- ATL::CDynamicParameterAccessor::GetParamLength
- ATL.CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor.GetParamLength
- CDynamicParameterAccessor::GetParamLength
- GetParamLength
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
- CDynamicParameterAccessor::GetParamStatus
- CDynamicParameterAccessor.GetParamStatus
- ATL.CDynamicParameterAccessor.GetParamStatus
- ATL::CDynamicParameterAccessor::GetParamStatus
- GetParamStatus
- CDynamicParameterAccessor.GetParamString
- GetParamString
- CDynamicParameterAccessor::GetParamString
- ATL.CDynamicParameterAccessor.GetParamString
- ATL::CDynamicParameterAccessor::GetParamString
- CDynamicParameterAccessor.GetParamType
- CDynamicParameterAccessor:GetParamType
- CDynamicParameterAccessor::GetParamType
- ATL.CDynamicParameterAccessor.GetParamType
- GetParamType
- ATL::CDynamicParameterAccessor::GetParamType
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParamLength
- CDynamicParameterAccessor.SetParamLength
- ATL.CDynamicParameterAccessor.SetParamLength
- CDynamicParameterAccessor::SetParamLength
- SetParamLength
- CDynamicParameterAccessor::SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamStatus
- ATL::CDynamicParameterAccessor::SetParamStatus
- CDynamicParameterAccessor.SetParamStatus
- SetParamStatus
- ATL.CDynamicParameterAccessor.SetParamString
- ATL::CDynamicParameterAccessor::SetParamString
- SetParamString
- CDynamicParameterAccessor::SetParamString
- CDynamicParameterAccessor.SetParamString
helpviewer_keywords:
- CDynamicParameterAccessor class
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
- GetParam method
- GetParamCount method
- GetParamIO method
- GetParamLength method
- GetParamName method
- GetParamStatus method
- GetParamString method
- GetParamType method
- SetParam method
- SetParamLength method
- SetParamStatus method
- SetParamString method
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
ms.openlocfilehash: b7125390013e417123f09a5cc7f58be9ea87db56
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216461"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor 类

类似于 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ，但通过调用 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) 接口获取要调用的参数信息。

## <a name="syntax"></a>语法

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>要求

**标头**： atldbcli。h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[CDynamicParameterAccessor](#cdynamicparameteraccessor)|构造函数。|
|[GetParam](#getparam)|从缓冲区中检索参数数据。|
|[GetParamCount](#getparamcount)|检索访问器中的参数数目。|
|[GetParamIO](#getparamio)|确定指定参数是输入参数还是输出参数。|
|[GetParamLength](#getparamlength)|检索存储在缓冲区中的指定参数的长度。|
|[GetParamName](#getparamname)|检索指定参数的名称。|
|[GetParamStatus](#getparamstatus)|检索存储在缓冲区中的指定参数的状态。|
|[GetParamString](#getparamstring)|检索存储在缓冲区中的指定参数的字符串数据。|
|[GetParamType](#getparamtype)|检索指定参数的数据类型。|
|[SetParam](#setparam)|使用参数数据设置缓冲区。|
|[SetParamLength](#setparamlength)|设置存储在缓冲区中的指定参数的长度。|
|[SetParamStatus](#setparamstatus)|设置存储在缓冲区中的指定参数的状态。|
|[SetParamString](#setparamstring)|设置存储在缓冲区中的指定参数的字符串数据。|

## <a name="remarks"></a>备注

访问接口必须支持 `ICommandWithParameters` 以便使用者使用此类。

参数信息存储在由此类创建和管理的缓冲区中。 通过使用 [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 和 [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)从缓冲区中获取参数数据。

有关演示如何使用此类执行 SQL Server 存储过程并获取输出参数值的示例，请参阅 GitHub 上的[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)存储库中的[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例代码。

## <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a><a name="cdynamicparameteraccessor"></a>CDynamicParameterAccessor：： CDynamicParameterAccessor

构造函数。

### <a name="syntax"></a>语法

```cpp
typedef CDynamicParameterAccessor _ParamClass;
CDynamicParameterAccessor(
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000 )
   : CDynamicAccessor(eBlobHandling, nBlobSize )
```

#### <a name="parameters"></a>参数

*eBlobHandling*<br/>
指定处理 BLOB 数据的方式。 默认值为 DBBLOBHANDLING_DEFAULT。 有关 DBBLOBHANDLINGENUM 值的说明，请参阅[CDynamicAccessor：： SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) 。

*nBlobSize*<br/>
最大 BLOB 大小（以字节为单位）；该值之上的列数据被视为 BLOB。 默认值为8000。 有关详细信息，请参阅[CDynamicAccessor：： SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) 。

### <a name="remarks"></a>备注

有关 BLOB 处理的详细信息，请参阅[CDynamicAccessor：： CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md)构造函数。

## <a name="cdynamicparameteraccessorgetparam"></a><a name="getparam"></a>CDynamicParameterAccessor：： GetParam

从参数缓冲区中检索指定参数的非字符串数据。

### <a name="syntax"></a>语法

```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,
   ctype* pData) const throw();

template <class ctype> bool GetParam(TCHAR* pParamName,
   ctype* pData) const throw();

void* GetParam(DBORDINAL nParam) const throw();

void* GetParam(TCHAR* pParamName) const throw();
```

#### <a name="parameters"></a>参数

*ctype*<br/>
作为数据类型的模板化参数。

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pParamName*<br/>
中参数名称。

*pData*<br/>
弄指向包含从缓冲区中检索到的数据的内存的指针。

### <a name="return-value"></a>返回值

对于非模板化版本，指向包含从缓冲区中检索到的数据的内存。 对于模板化版本， **`true`** 在成功或 **`false`** 失败时返回。

用于 `GetParam` 从缓冲区中检索非字符串参数数据。 使用[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)从缓冲区中检索字符串参数数据。

## <a name="cdynamicparameteraccessorgetparamcount"></a><a name="getparamcount"></a>CDynamicParameterAccessor：： GetParamCount

检索存储在缓冲区中的参数数目。

### <a name="syntax"></a>语法

```cpp
DB_UPARAMS GetParamCount() const throw();
```

### <a name="return-value"></a>返回值

参数的数量。

## <a name="cdynamicparameteraccessorgetparamio"></a><a name="getparamio"></a>CDynamicParameterAccessor：： GetParamIO

确定指定参数是输入参数还是输出参数。

### <a name="syntax"></a>语法

```cpp
bool GetParamIO(DBORDINAL nParam,
   DBPARAMIO* pParamIO) const throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pParamIO*<br/>
指向变量的指针，该变量包含 `DBPARAMIO` 指定参数的类型（输入或输出）。 它的定义如下：

```cpp
typedef DWORD DBPARAMIO;

enum DBPARAMIOENUM {
    DBPARAMIO_NOTPARAM   = 0,
    DBPARAMIO_INPUT      = 0x1,
    DBPARAMIO_OUTPUT     = 0x2
};
```

### <a name="return-value"></a>返回值

**`true`** 成功或失败时返回 **`false`** 。

## <a name="cdynamicparameteraccessorgetparamlength"></a><a name="getparamlength"></a>CDynamicParameterAccessor：： GetParamLength

检索存储在缓冲区中的指定参数的长度。

### <a name="syntax"></a>语法

```cpp
bool GetParamLength(DBORDINAL nParam,
   DBLENGTH* pLength);

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pLength*<br/>
[out] 指向包含指定参数的长度（以字节为单位）的变量的指针。

### <a name="remarks"></a>备注

第一次重写会 **`true`** 在成功或 **`false`** 失败时返回。 第二个重写指向包含参数的长度的内存。

## <a name="cdynamicparameteraccessorgetparamname"></a><a name="getparamname"></a>CDynamicParameterAccessor：： GetParamName

检索指定参数的名称。

### <a name="syntax"></a>语法

```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

### <a name="return-value"></a>返回值

指定参数的名称。

## <a name="cdynamicparameteraccessorgetparamstatus"></a><a name="getparamstatus"></a>CDynamicParameterAccessor：： GetParamStatus

检索存储在缓冲区中的指定参数的状态。

### <a name="syntax"></a>语法

```cpp
bool GetParamStatus(DBORDINAL nParam,
   DBSTATUS* pStatus);

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pStatus*<br/>
弄指向包含指定参数的 DBSTATUS 状态的变量的指针。 有关 DBSTATUS 值的信息，请参阅*OLE DB 程序员参考*中的[状态](/previous-versions/windows/desktop/ms722617(v=vs.85))或在 DBSTATUS 中搜索。

### <a name="remarks"></a>备注

第一次重写会 **`true`** 在成功或 **`false`** 失败时返回。 第二次重写指向包含指定参数状态的内存。

## <a name="cdynamicparameteraccessorgetparamstring"></a><a name="getparamstring"></a>CDynamicParameterAccessor：： GetParamString

检索存储在缓冲区中的指定参数的字符串数据。

### <a name="syntax"></a>语法

```cpp
bool GetParamString(DBORDINAL nParam,
   CSimpleStringA& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CSimpleStringW& strOutput) throw();

bool GetParamString(DBORDINAL nParam,
   CHAR* pBuffer,
   size_t* pMaxLen) throw();

bool GetParamString(DBORDINAL nParam,
   WCHAR* pBuffer,
   size_t* pMaxLen) throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*strOutput*<br/>
弄指定参数的 ANSI （ `CSimpleStringA` ）或 Unicode （ `CSimpleStringW` ）字符串数据。 应传递类型为的参数 `CString` ，例如：

[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]

*pBuffer*<br/>
弄指向指定参数的 ANSI （**CHAR**）或 Unicode （**WCHAR**）字符串数据的指针。

*pMaxLen*<br/>
弄一个指针，指向由*pBuffer*指向的缓冲区的大小（包括终止 NULL）。

### <a name="remarks"></a>备注

**`true`** 成功或失败时返回 **`false`** 。

如果*pBuffer*为 NULL，则此方法将在*pMaxLen*指向的内存中设置所需的缓冲区大小，并返回 **`true`** 而不复制数据。

如果缓冲区*pBuffer*不够大，无法包含整个字符串，则此方法将失败。

用于 `GetParamString` 从缓冲区中检索字符串参数数据。 使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)从缓冲区中检索非字符串参数数据。

## <a name="cdynamicparameteraccessorgetparamtype"></a><a name="getparamtype"></a>CDynamicParameterAccessor：： GetParamType

检索指定参数的数据类型。

### <a name="syntax"></a>语法

```cpp
bool GetParamType(DBORDINAL nParam,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pType*<br/>
弄指向包含指定参数的数据类型的变量的指针。

### <a name="return-value"></a>返回值

**`true`** 成功或失败时返回 **`false`** 。

## <a name="cdynamicparameteraccessorsetparam"></a><a name="setparam"></a>CDynamicParameterAccessor：： SetParam

使用指定的（非字符串）数据设置参数缓冲区。

### <a name="syntax"></a>语法

```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,
   constctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();

template <class ctype>
bool SetParam(TCHAR* pParamName,
   const ctype* pData,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>参数

*ctype*<br/>
作为数据类型的模板化参数。

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 例如：

[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]

*pParamName*<br/>
中参数名称。

*pData*<br/>
中指向内存的指针，该内存包含要写入到缓冲区的数据。

*status*<br/>
中DBSTATUS 列状态。 有关 DBSTATUS 值的信息，请参阅*OLE DB 程序员参考*中的[状态](/previous-versions/windows/desktop/ms722617(v=vs.85))或在 DBSTATUS 中搜索。

### <a name="return-value"></a>返回值

**`true`** 成功或失败时返回 **`false`** 。

用于 `SetParam` 设置缓冲区中的非字符串参数数据。 使用[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)设置缓冲区中的字符串参数数据。

## <a name="cdynamicparameteraccessorsetparamlength"></a><a name="setparamlength"></a>CDynamicParameterAccessor：： SetParamLength

设置存储在缓冲区中的指定参数的长度。

### <a name="syntax"></a>语法

```cpp
bool SetParamLength(DBORDINAL nParam,
   DBLENGTH length);
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*length*<br/>
中指定参数的长度（以字节为单位）。

### <a name="remarks"></a>备注

**`true`** 成功或失败时返回 **`false`** 。

## <a name="cdynamicparameteraccessorsetparamstatus"></a><a name="setparamstatus"></a>CDynamicParameterAccessor：： SetParamStatus

设置存储在缓冲区中的指定参数的状态。

### <a name="syntax"></a>语法

```cpp
bool SetParamStatus(DBORDINAL nParam,
   DBSTATUS status);
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*status*<br/>
中指定参数的 DBSTATUS 状态。 有关 DBSTATUS 值的信息，请参阅*OLE DB 程序员参考*中的[状态](/previous-versions/windows/desktop/ms722617(v=vs.85))或在 DBSTATUS 中搜索。

### <a name="remarks"></a>备注

**`true`** 成功或失败时返回 **`false`** 。

## <a name="cdynamicparameteraccessorsetparamstring"></a><a name="setparamstring"></a>CDynamicParameterAccessor：： SetParamString

设置存储在缓冲区中的指定参数的字符串数据。

### <a name="syntax"></a>语法

```cpp
bool SetParamString(DBORDINAL nParam,
   constCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();bool SetParamString(DBORDINAL nParam,
   constWCHAR* pString,
   DBSTATUS status = DBSTATUS_S_OK) throw();
```

#### <a name="parameters"></a>参数

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 有关示例，请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) 。

*pString*<br/>
中指向指定参数的 ANSI （**CHAR**）或 Unicode （**WCHAR**）字符串数据的指针。 请参阅 oledb 中的 DBSTATUS。

*status*<br/>
中指定参数的 DBSTATUS 状态。 有关 DBSTATUS 值的信息，请参阅*OLE DB 程序员参考*中的[状态](/previous-versions/windows/desktop/ms722617(v=vs.85))或在 DBSTATUS 中搜索。

### <a name="remarks"></a>备注

**`true`** 成功或失败时返回 **`false`** 。

`SetParamString`如果尝试设置的字符串大于为*pString*指定的最大大小，则将失败。

用于 `SetParamString` 设置缓冲区中的字符串参数数据。 使用[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)设置缓冲区中的非字符串参数数据。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)
