---
title: CDynamicParameterAccessor 类 |Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0db07c8419db53d30612e6edbbe134634e37a74
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083939"
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor 类

类似于 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) ，但通过调用 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) 接口获取要调用的参数信息。

## <a name="syntax"></a>语法

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="requirements"></a>要求

**标头**：atldbcli.h

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

有关演示如何使用此类以执行 SQL Server 存储过程并获取输出参数值的示例，请参阅[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)示例中的代码[Microsoft VCSamples](https://github.com/Microsoft/VCSamples)GitHub 上的存储库。

## <a name="cdynamicparameteraccessor"></a> Cdynamicparameteraccessor:: Cdynamicparameteraccessor

构造函数。  
  
### <a name="syntax"></a>语法  
  
```cpp
typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor(eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>参数  

*eBlobHandling*<br/>
指定处理 BLOB 数据的方式。 默认值为 DBBLOBHANDLING_DEFAULT。 请参阅[cdynamicaccessor:: Setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) DBBLOBHANDLINGENUM 值的说明。  
  
*nBlobSize*<br/>
最大 BLOB 大小（以字节为单位）；该值之上的列数据被视为 BLOB。 默认值为 8000。 请参阅[cdynamicaccessor:: Setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)有关详细信息。  
  
### <a name="remarks"></a>备注  

请参阅[cdynamicaccessor:: Cdynamicaccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) BLOB 处理的详细信息的构造函数。 

## <a name="getparam"></a> Cdynamicparameteraccessor:: Getparam

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
模板化参数，其数据类型。  
  
*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*pParamName*<br/>
[in]参数名称。  
  
*pData*<br/>
[out]指向包含从缓冲区检索到的数据的内存的指针。  
  
### <a name="return-value"></a>返回值  

对于非模板化的版本中，指向包含数据的内存缓冲区中检索。 对于模板化版本，则返回 **，则返回 true**成功后或**false**失败。  
  
使用`GetParam`从缓冲区检索非字符串参数数据。 使用[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)从缓冲区检索字符串参数数据。  

## <a name="getparamcount"></a> Cdynamicparameteraccessor:: Getparamcount

检索存储在缓冲区中的参数数目。  
  
### <a name="syntax"></a>语法  
  
```cpp
DB_UPARAMS GetParamCount() const throw();  
```  
  
### <a name="return-value"></a>返回值  

参数的数量。  

## <a name="getparamio"></a> Cdynamicparameteraccessor:: Getparamio

确定指定参数是输入参数还是输出参数。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetParamIO(DBORDINAL nParam,   
   DBPARAMIO* pParamIO) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*pParamIO*<br/>
一个指向的变量包含`DBPARAMIO`指定参数的类型 （输入或输出）。 它定义，如下所示：  
  
```cpp  
typedef DWORD DBPARAMIO;  
  
enum DBPARAMIOENUM {  
    DBPARAMIO_NOTPARAM   = 0,  
    DBPARAMIO_INPUT      = 0x1,  
    DBPARAMIO_OUTPUT     = 0x2  
};  
```  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**成功后或**false**失败。  

## <a name="getparamlength"></a> Cdynamicparameteraccessor:: Getparamlength

检索存储在缓冲区中的指定参数的长度。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetParamLength(DBORDINAL nParam,  
   DBLENGTH* pLength);  

DBLENGTH* GetParamLength(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*pLength*<br/>
[out] 指向包含指定参数的长度（以字节为单位）的变量的指针。  
  
### <a name="remarks"></a>备注  

第一个重写返回 **，则返回 true**成功后或**false**失败。 第二个重写指向包含参数的长度的内存。 

## <a name="getparamname"></a> Cdynamicparameteraccessor:: Getparamname

检索指定参数的名称。  
  
### <a name="syntax"></a>语法  
  
```cpp
LPOLESTR GetParamName(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
### <a name="return-value"></a>返回值  

指定参数的名称。  

## <a name="getparamstatus"></a> Cdynamicparameteraccessor:: Getparamstatus

检索存储在缓冲区中的指定参数的状态。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetParamStatus(DBORDINAL nParam,  
   DBSTATUS* pStatus);  

DBSTATUS* GetParamStatus(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*pStatus*<br/>
[out]指向包含指定的参数的 DBSTATUS 状态的变量的指针。 DBSTATUS 值的信息，请参阅[状态](/previous-versions/windows/desktop/ms722617)中*OLE DB 程序员参考*，或在 oledb.h DBSTATUS 搜索。  
  
### <a name="remarks"></a>备注  

第一个重写返回 **，则返回 true**成功后或**false**失败。 第二个重写指向包含指定的参数的状态的内存。

## <a name="getparamstring"></a> Cdynamicparameteraccessor:: Getparamstring

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
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*strOutput*<br/>
[out]ANSI (`CSimpleStringA`) 或 Unicode (`CSimpleStringW`) 的字符串的指定参数的数据。 应传递的类型参数`CString`，例如：  
  
[!code-cpp[NVC_OLEDB_Consumer#9](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-getparamstring_1.cpp)]  
  
*pBuffer*<br/>
[out]一个指向 ANSI (**CHAR**) 或 Unicode (**WCHAR**) 的字符串的指定参数的数据。  
  
*pMaxLen*<br/>
[out]指向缓冲区的大小的指针指向的*pBuffer* （以字符为单位，包括终止 NULL）。  
  
### <a name="remarks"></a>备注  

返回 **，则返回 true**成功后或**false**失败。  
  
如果*pBuffer*为 NULL，此方法将设置指向的内存中的所需的缓冲区大小*pMaxLen*并返回**true**而无需将数据复制。  
  
此方法将失败，如果缓冲区*pBuffer*不够大，以包含整个字符串。  
  
使用`GetParamString`从缓冲区检索字符串参数数据。 使用[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)从缓冲区检索非字符串参数数据。  

## <a name="getparamtype"></a> Cdynamicparameteraccessor:: Getparamtype

检索指定参数的数据类型。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool GetParamType(DBORDINAL nParam,  
   DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*pType*<br/>
[out]指向包含指定的参数的数据类型的变量的指针。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**成功后或**false**失败。  

## <a name="setparam"></a> Cdynamicparameteraccessor:: Setparam

设置使用指定的 （非字符串） 数据的参数缓冲区。  
  
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
模板化参数，其数据类型。  
  
*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 例如：  
  
[!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
*pParamName*<br/>
[in]参数名称。  
  
*pData*<br/>
[in]指向包含要写入缓冲区的数据的内存的指针。  
  
*status*<br/>
[in]DBSTATUS 列状态。 DBSTATUS 值的信息，请参阅[状态](/previous-versions/windows/desktop/ms722617)中*OLE DB 程序员参考*，或在 oledb.h DBSTATUS 搜索。  
  
### <a name="return-value"></a>返回值  

返回 **，则返回 true**成功后或**false**失败。  
  
使用`SetParam`用于将非字符串参数数据设置缓冲区中。 使用[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)用于将字符串参数数据设置缓冲区中。  

## <a name="setparamlength"></a> Cdynamicparameteraccessor:: Setparamlength

设置存储在缓冲区中的指定参数的长度。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool SetParamLength(DBORDINAL nParam,  
   DBLENGTH length);  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*length*<br/>
[in]指定参数的长度以字节为单位。  
  
### <a name="remarks"></a>备注  

返回 **，则返回 true**成功后或**false**失败。 

## <a name="setparamstatus"></a> Cdynamicparameteraccessor:: Setparamstatus

设置存储在缓冲区中的指定参数的状态。  
  
### <a name="syntax"></a>语法  
  
```cpp
bool SetParamStatus(DBORDINAL nParam,  
   DBSTATUS status);  
```  
  
#### <a name="parameters"></a>参数  

*nParam*<br/>
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*status*<br/>
[in]指定参数的 DBSTATUS 状态。 DBSTATUS 值的信息，请参阅[状态](/previous-versions/windows/desktop/ms722617)中*OLE DB 程序员参考*，或在 oledb.h DBSTATUS 搜索。  
  
### <a name="remarks"></a>备注  

返回 **，则返回 true**成功后或**false**失败。 

## <a name="setparamstring"></a> Cdynamicparameteraccessor:: Setparamstring

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
[in] 参数号（相对于 1 的偏移量）。 将为返回值保留参数 0。 参数号是基于参数在 SQL 或存储的过程调用中的顺序的参数索引。 请参阅[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)有关的示例。  
  
*pString*<br/>
[in]一个指向 ANSI (**CHAR**) 或 Unicode (**WCHAR**) 的字符串的指定参数的数据。 请参阅 oledb.h DBSTATUS。  
  
*status*<br/>
[in]指定参数的 DBSTATUS 状态。 DBSTATUS 值的信息，请参阅[状态](/previous-versions/windows/desktop/ms722617)中*OLE DB 程序员参考*，或在 oledb.h DBSTATUS 搜索。  
  
### <a name="remarks"></a>备注  

返回 **，则返回 true**成功后或**false**失败。  
  
`SetParamString` 如果您尝试设置为大于最大大小为指定的字符串将失败*pString*。  
  
使用`SetParamString`用于将字符串参数数据设置缓冲区中。 使用[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)用于将非字符串参数数据设置缓冲区中。 

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)  