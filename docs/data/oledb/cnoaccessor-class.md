---
title: CNoAccessor 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs:
- C++
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 97cfefc679391cb54ff40f38285f22f40d068553
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063830"
---
# <a name="cnoaccessor-class"></a>CNoAccessor 类

可以用作模板自变量 (`TAccessor`) 的模板类，如`CCommand`和`CTable`，需要访问器类参数。

## <a name="syntax"></a>语法

```cpp
class CNoAccessor
```

## <a name="remarks"></a>备注

使用`CNoAccessor`作为模板参数，如果不想要支持参数或输出列的类。

`CNoAccessor` 将实现以下存根方法，其中每个方法都对应于其他访问器类方法：

- `BindColumns` -将列绑定到访问器。

- `BindParameters` -将创建的参数绑定到列。

- `Bind` -创建绑定。

- `Close` -关闭访问器。

- `ReleaseAccessors` -释放访问器类创建的。

- `FreeRecordMemory` -释放需要释放的当前记录中的任何列。

- `GetColumnInfo` -从打开的行集中获取列信息。

- `GetNumAccessors` -检索类创建的取值函数的数目。

- `IsAutoAccessor` 的如果自动检索数据的访问器在移动操作过程返回 true。

- `GetHAccessor` -检索指定的访问器的访问器句柄。

- `GetBuffer` -检索到的书签缓冲区的指针。

- `NoBindOnNullRowset` -可以防止在空的行集上的数据绑定。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)