---
title: CDataSource 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7835cd7401c13ab167a9236db4f7e2fc98f3e175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasource-class"></a>CDataSource 类
对应于一个 OLE DB 数据源对象，该对象表示通过提供程序建立的与数据源的连接。  
  
## <a name="syntax"></a>语法

```cpp
class CDataSource  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[关闭](../../data/oledb/cdatasource-close.md)|关闭连接。|  
|[GetInitializationString](../../data/oledb/cdatasource-getinitializationstring.md)|检索当前打开的数据源的初始化字符串。|  
|[GetProperties](../../data/oledb/cdatasource-getproperties.md)|获取当前为连接的数据源设置的属性的值。|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|获取当前为连接的数据源设置的单个属性的值。|  
|[打开](../../data/oledb/cdatasource-open.md)|创建一个与提供程序 （数据源） 的连接，使用**CLSID**， **ProgID**，或`CEnumerator`由调用方提供的名字对象。|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|从由用户提供的文件名指定的文件打开数据源。|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|打开由初始化字符串指定的数据源。|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|允许用户选择之前创建的数据链接文件来打开对应的数据源。|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|使用“数据链接”对话框打开数据源对象。|  
  
## <a name="remarks"></a>备注  
 可以为单个连接创建一个或多个数据库会话。 这些会话由 `CSession` 表示。 必须调用[cdatasource:: Open](../../data/oledb/cdatasource-open.md)打开之前创建的会话连接`CSession::Open`。  
  
 有关如何使用的示例`CDataSource`，请参阅[CatDB](../../visual-cpp-samples.md)示例。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)