---
title: CDynamicStringAccessorA 类
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorA
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
ms.openlocfilehash: 3a0da9c779230fc1bf58bfa1d685623f844012c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231033"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA 类

可以在不知道数据库架构 （基础结构） 时访问数据源。

## <a name="syntax"></a>语法

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>备注

在这两个请求提供程序提取从字符串数据作为数据存储区访问的所有数据，但`CDynamicStringAccessor`请求 ANSI 字符串数据。

`CDynamicStringAccessorA` 继承`GetString`并`SetString`从`CDynamicStringAccessor`。 使用这些方法时`CDynamicStringAccessorA`对象，`BaseType`是**CHAR**。

## <a name="requirements"></a>要求

**标头**：atldbcli.h

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 类](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 类](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 类](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 类](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
