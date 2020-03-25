---
title: CAccessor 类
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212285"
---
# <a name="caccessor-class"></a>CAccessor 类

表示取值函数类型之一。

## <a name="syntax"></a>语法

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>parameters

*T*<br/>
用户记录类。

## <a name="remarks"></a>备注

它在记录静态绑定到数据源时使用。 记录包含缓冲区。 此类对行集支持多个访问器。

当您知道数据库的结构和类型时，请使用此访问器类型。

如果访问器包含指向必须释放的内存（如 `BSTR` 或接口）的字段，则在读取下一条记录之前调用成员函数[CAccessorRowset：： FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) 。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
