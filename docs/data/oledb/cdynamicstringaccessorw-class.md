---
title: CDynamicStringAccessorW 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorW
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 767add2be1f9f5266a6a66ce4455dec172f63e45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095737"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW 类
可以在不知道数据库架构 （基础结构） 时访问数据源。  
  
## <a name="syntax"></a>语法

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## <a name="remarks"></a>备注  
 它们都请求提供程序获取访问从数据存储区作为字符串数据的所有数据，但`CDynamicStringAccessor`请求 Unicode 字符串数据。  
  
 `CDynamicStringAccessorW` 继承**GetString**和`SetString`从`CDynamicStringAccessor`。 当你使用这些方法中的`CDynamicStringAccessorW`对象， ***BaseType***是**WCHAR**。  
  
## <a name="requirements"></a>要求  
 **标头**：atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)