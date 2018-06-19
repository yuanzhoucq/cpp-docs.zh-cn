---
title: CDynamicStringAccessor 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessor class
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b8888bdac7d605ce1832ef7074955fab4893b33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097593"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 类
使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  
  
## <a name="syntax"></a>语法  
  
```cpp
      template< typename BaseType, DBTYPEENUM OleDbType >  
class CDynamicStringAccessorT : public CDynamicAccessor  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)|将指定列数据作为字符串检索。|  
|[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)|将指定列数据设置为字符串。|  
  
## <a name="remarks"></a>备注  
 虽然[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)请求中提供程序，报告的本机格式数据`CDynamicStringAccessor`请求提供程序获取访问从数据存储区作为字符串数据的所有数据。 这是对于不需要计算的数据存储，例如显示或打印数据存储区的内容中的值的简单任务特别有用。  
  
 数据存储中列数据的本机类型并不重要；只要提供程序可支持数据转换，它就将提供字符串格式的数据。 如果提供程序不支持从本机数据类型转换为字符串 （这是不常见），则请求调用将返回成功值**DB_S_ERRORSOCCURED**，并将相应的列的状态指示转换问题**DBSTATUS_E_CANTCONVERTVALUE**。  
  
 使用`CDynamicStringAccessor`方法以获取列信息。 此列信息用于在运行时动态创建取值函数。  
  
 列信息存储在缓冲区创建和管理此类。 获取数据缓冲区使用[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)，或将其存储到缓冲区使用[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)。  
  
 有关的讨论和使用动态访问器类的示例，请参阅[使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。  
  
## <a name="requirements"></a>要求  
 **标头**：atldbcli.h  
  
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