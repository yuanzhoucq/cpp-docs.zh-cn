---
title: "CDataConnection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c8e405b95543d170a4e94e39626e9b9793791c7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnection-class"></a>CDataConnection 类
管理与数据源的连接。  
  
## <a name="syntax"></a>语法

```cpp
class CDataConnection  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|构造函数。 实例化和初始化`CDataConnection`对象。|  
|[复制](../../data/oledb/cdataconnection-copy.md)|创建现有的数据连接的副本。|  
|[打开](../../data/oledb/cdataconnection-open.md)|打开使用初始化字符串的数据源的连接。|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|打开当前连接上的新会话。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[BOOL 运算符](../../data/oledb/cdataconnection-operator-bool.md)|确定当前会话是否为打开。|  
|[operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|确定当前会话是否为打开。|  
|[operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|返回所包含的引用`CDataSource`对象。|  
|[operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|返回指向包含的 `CDataSource` 对象的指针。|  
|[operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)|返回所包含的引用`CSession`对象。|  
|[operator CSession*](../../data/oledb/cdataconnection-operator-csession-star.md)|返回指向包含的 `CSession` 对象的指针。|  
  
## <a name="remarks"></a>备注  
 `CDataConnection` 是用于创建客户端，因为它封装必要的对象 （数据源和会话） 和一些操作，你需要连接到数据源时执行操作的有用类  
  
 而无需`CDataConnection`，你必须创建`CDataSource`对象，请调用其[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)方法，然后创建的一个实例[CSession](../../data/oledb/csession-class.md)对象，请调用其[打开](../../data/oledb/csession-open.md)方法，然后创建[CCommand](../../data/oledb/ccommand-class.md)对象并调用其**打开*** 方法。  
  
 与`CDataConnection`，只需创建连接对象，将其传递初始化字符串，然后使用该连接打开命令。 如果你打算反复使用数据库的连接，则使连接保持打开，一个好办法和`CDataConnection`提供一种简便方式做到这一点。  
  
> [!NOTE]
>  如果要创建的数据库应用程序需要处理多个会话，你将需要使用[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)