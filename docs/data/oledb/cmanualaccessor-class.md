---
title: CManualAccessor 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f94e1100398b3f338fdc34839aee9a1e8f67871c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338371"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor 类
表示用于高级用途而设计的访问器类型。  
  
## <a name="syntax"></a>语法

```cpp
class CManualAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](#addbindentry)|将绑定条目添加到输出列。|  
|[AddParameterEntry](#addparameterentry)|将参数项添加到参数访问器。|  
|[CreateAccessor](#createaccessor)|列绑定结构分配内存并初始化列数据成员。|  
|[CreateParameterAccessor](#createparameteraccessor)|参数绑定结构分配内存并初始化参数数据成员。|  
  
## <a name="remarks"></a>备注  
 使用`CManualAccessor`，可以指定参数和运行时函数调用的输出列绑定。  

## <a name="addbindentry"></a> Cmanualaccessor:: Addbindentry
将绑定条目添加到输出列。  
  
### <a name="syntax"></a>语法  
  
```cpp
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx)中*OLE DB 程序员参考*。  
  
 *nOrdinal*  
 [in]列号。  
  
 *wType*  
 [in]数据类型。  
  
 *nColumnSize*  
 [in]列大小 （字节）。  
  
 *pData*  
 [in]指向存储在缓冲区中的列数据的指针。  
  
 *pLength*  
 [in]指向字段长度，如果所需的指针。  
  
 *pStatus*  
 [in]指向要绑定到的列状态，如果所需的变量的指针。  
  
### <a name="remarks"></a>备注  
 若要使用此函数，必须首先调用[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)。 无法添加更多的项中指定的列数比`CreateAccessor`。 
  
## <a name="addparameterentry"></a> Cmanualaccessor:: Addparameterentry
将参数项添加到参数项结构。  
  
### <a name="syntax"></a>语法  
  
```cpp
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx)中*OLE DB 程序员参考*。  
  
 *nOrdinal*  
 [in]参数数目。  
  
 *wType*  
 [in]数据类型。  
  
 *nColumnSize*  
 [in]列大小 （字节）。  
  
 *pData*  
 [in]指向存储在缓冲区中的列数据的指针。  
  
 *pLength*  
 [in]指向字段长度，如果所需的指针。  
  
 *pStatus*  
 [in]指向要绑定到的列状态，如果所需的变量的指针。  
  
 *eParamIO*  
 [in]指定绑定与之关联的参数是否为输入、 输入/输出或输出参数。  
  
### <a name="remarks"></a>备注  
 若要使用此函数，必须首先调用[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)。 

## <a name="createaccessor"></a> Cmanualaccessor:: Createaccessor
列绑定结构分配内存并初始化列数据成员。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *nBindEntries*  
 [in]列数。 该数目应与匹配对的调用次数[cmanualaccessor:: Addbindentry](../../data/oledb/cmanualaccessor-addbindentry.md)函数。  
  
 *pBuffer*  
 [in]指向缓冲区的输出列的存储位置的指针。  
  
 *nBufferSize*  
 [in]以字节为单位的缓冲区的大小。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 在调用之前调用此函数`CManualAccessor::AddBindEntry`函数。  

## <a name="createparameteraccessor"></a> Cmanualaccessor:: Createparameteraccessor
参数绑定结构分配内存并初始化参数数据成员。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT CreateParameterAccessor(int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *nBindEntries*  
 [in]列数。  
  
 *pBuffer*  
 [in]指向缓冲区的输入的列的存储位置的指针。  
  
 *nBufferSize*  
 [in]以字节为单位的缓冲区的大小。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 您必须调用此函数之前调用[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)。

## <a name="see-also"></a>请参阅  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)