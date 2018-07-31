---
title: CDynamicStringAccessor 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d74138247bdfd427dd26d1a3d98b9a82dae39e60
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337682"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 类
使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  
  
## <a name="syntax"></a>语法  
  
```cpp
template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  

## <a name="requirements"></a>要求  
 **标头**：atldbcli.h 

## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetString](#getstring)|将指定列数据作为字符串检索。|  
|[SetString](#setstring)|将指定列数据设置为字符串。|  
  
## <a name="remarks"></a>备注  
 虽然[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)请求数据以本机格式提供程序，报告`CDynamicStringAccessor`请求提供程序提取从字符串数据作为数据存储区访问的所有数据。 这是对于不需要计算的数据存储，如在显示或输出数据存储区的内容中的值的简单任务特别有用。  
  
 数据存储中列数据的本机类型并不重要；只要提供程序可支持数据转换，它就将提供字符串格式的数据。 如果提供程序不支持从本机数据类型转换为字符串 （这是不常见），请求的调用将返回成功值 DB_S_ERRORSOCCURED，并为相应的列的状态将指示转换问题DBSTATUS_E_CANTCONVERTVALUE。  
  
 使用`CDynamicStringAccessor`方法可获取列信息。 此列信息用于在运行时动态创建取值函数。  
  
 创建和管理此类缓冲区中存储的列信息。 从缓冲区使用获取数据[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)，或将其存储到缓冲区使用[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)。  
  
 有关的讨论和使用动态访问器类的示例，请参阅[使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。  

## <a name="getstring"></a> Cdynamicstringaccessor:: Getstring
将指定列数据作为字符串检索。  
  
### <a name="syntax"></a>语法  
  
```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();  

BaseType* GetString(const CHAR* pColumnName) const throw();  

BaseType* GetString(const WCHAR* pColumnName) const throw();  
```  
  
#### <a name="parameters"></a>参数  
 *nColumn*  
 [in] 列号。 列号从 1 开始。 值为 0 指书签列，如果有的话。  
  
 *pColumnName*  
 [in]指向包含的列名称的字符串的指针。  
  
### <a name="return-value"></a>返回值  
 从指定的列检索到的字符串值的指针。 值为类型`BaseType`，这将是**CHAR**或**WCHAR**具体取决于是否或未定义 _UNICODE。 如果找不到指定的列，返回 NULL。  
  
### <a name="remarks"></a>备注  
 第二个重写窗体所需列的名称为 ANSI 字符串。 第三个重写窗体所需列的名称为 Unicode 字符串。  
 
## <a name="setstring"></a> Cdynamicstringaccessor:: Setstring
将指定列数据设置为字符串。  
  
### <a name="syntax"></a>语法  
  
```cpp
HRESULT SetString(DBORDINAL nColumn,  
   BaseType* data) throw();  

HRESULT SetString(const CHAR* pColumnName,  
   BaseType* data) throw();  

HRESULT SetString(const WCHAR* pColumnName,  
   BaseType* data) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *nColumn*  
 [in] 列号。 列号从 1 开始。 特殊值 0 指书签列，如果有的话。  
  
 *pColumnName*  
 [in]指向包含的列名称的字符串的指针。  
  
 *data*  
 [in]指向要写入到指定的列的字符串数据的指针。  
  
### <a name="return-value"></a>返回值  
 指向要设置指定的列的字符串值的指针。 值为类型`BaseType`，这将是**CHAR**或**WCHAR**具体取决于是否或未定义 _UNICODE。  
  
### <a name="remarks"></a>备注  
 第二个重写窗体将作为 ANSI 字符串的列名称和第三个重写窗体将作为 Unicode 字符串的列名称。  
  
 如果 _SECURE_ATL 定义为具有非零值，如果将生成运行时断言失败输入*数据*字符串的长度超过引用的数据列的最大长度。 否则，如果超过最大允许长度，则将截断输入的字符串。  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessorA 类](../../data/oledb/cdynamicstringaccessora-class.md)   
 [CDynamicStringAccessorW 类](../../data/oledb/cdynamicstringaccessorw-class.md)   
 [CXMLAccessor 类](../../data/oledb/cxmlaccessor-class.md)