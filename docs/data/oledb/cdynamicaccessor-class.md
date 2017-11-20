---
title: "CDynamicAccessor 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
dev_langs: C++
helpviewer_keywords: CDynamicAccessor class
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b36276a1a4ae64bee40a41cd844b1ad0d38c911a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 类
使您可以在不知道数据库架构（数据库的基础结构）的情况下访问数据源。  
  
## <a name="syntax"></a>语法  
  
```  
class CDynamicAccessor : public CAccessorBase  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cdynamicaccessor-addbindentry.md)|重写默认访问器时，请将绑定条目添加到输出列。|  
|[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)|实例化和初始化`CDynamicAccessor`对象。|  
|[关闭](../../data/oledb/cdynamicaccessor-close.md)|取消绑定所有列，释放分配的内存，并释放[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)类中的接口指针。|  
|[GetBookmark](../../data/oledb/cdynamicaccessor-getbookmark.md)|检索当前行的书签。|  
|[GetBlobHandling](../../data/oledb/cdynamicaccessor-getblobhandling.md)|检索 BLOB 处理的当前行值。|  
|[GetBlobSizeLimit](../../data/oledb/cdynamicaccessor-getblobsizelimit.md)|检索以字节为单位的最大 BLOB 大小。|  
|[GetColumnCount](../../data/oledb/cdynamicaccessor-getcolumncount.md)|检索行集中的列的数。|  
|[GetColumnFlags](../../data/oledb/cdynamicaccessor-getcolumnflags.md)|检索列特征。|  
|[GetColumnInfo](../../data/oledb/cdynamicaccessor-getcolumninfo.md)|检索列元数据。|  
|[GetColumnName](../../data/oledb/cdynamicaccessor-getcolumnname.md)|检索指定列的名称。|  
|[GetColumnType](../../data/oledb/cdynamicaccessor-getcolumntype.md)|检索指定列的数据类型。|  
|[GetLength](../../data/oledb/cdynamicaccessor-getlength.md)|检索以字节为单位的列的最大可取长度。|  
|[GetOrdinal](../../data/oledb/cdynamicaccessor-getordinal.md)|检索给定的一个列名称的列索引。|  
|[GetStatus](../../data/oledb/cdynamicaccessor-getstatus.md)|检索指定列的状态。|  
|[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)|从缓冲区中检索数据。|  
|[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)|设置处理的当前行值的 BLOB。|  
|[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)|以字节为单位设置的最大 BLOB 大小。|  
|[SetLength](../../data/oledb/cdynamicaccessor-setlength.md)|以字节为单位设置列的长度。|  
|[SetStatus](../../data/oledb/cdynamicaccessor-setstatus.md)|设置指定列的状态。|  
|[SetValue](../../data/oledb/cdynamicaccessor-setvalue.md)|将数据存储到缓冲区。|  
  
## <a name="remarks"></a>备注  
 使用`CDynamicAccessor`方法以获取列信息，如列名称、 列数、 数据类型和等等。 然后可以使用此列信息以在运行时动态创建取值函数。  
  
 列信息存储在缓冲区是创建和管理此类。 获取数据缓冲区使用[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)。  
  
 有关的讨论和使用动态访问器类的示例，请参阅[使用动态访问器](../../data/oledb/using-dynamic-accessors.md)。  
  
## <a name="requirements"></a>要求  
 **标头**：atldbcli.h  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 类](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)