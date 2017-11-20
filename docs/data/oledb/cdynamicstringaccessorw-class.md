---
title: "CDynamicStringAccessorW 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDynamicStringAccessorW
dev_langs: C++
helpviewer_keywords: CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 531aa1fa88e4d8b0ad7bd6bd61a3479a2fd7d0af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW 类
可以在不知道数据库架构 （基础结构） 时访问数据源。  
  
## <a name="syntax"></a>语法  
  
```  
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## <a name="remarks"></a>备注  
 它们都请求提供程序获取访问从数据存储区作为字符串数据的所有数据，但`CDynamicStringAccessor`请求 Unicode 字符串数据。  
  
 `CDynamicStringAccessorW`继承**GetString**和`SetString`从`CDynamicStringAccessor`。 当你使用这些方法中的`CDynamicStringAccessorW`对象， ***BaseType***是**WCHAR**。  
  
## <a name="requirements"></a>要求  
 **标头**：atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)