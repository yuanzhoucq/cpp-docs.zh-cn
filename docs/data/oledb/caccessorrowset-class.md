---
title: CAccessorRowset 类
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
ms.openlocfilehash: 77c4eebae6ede5d74e24421cc4d3951c78e08777
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546019"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset 类

在一个类中封装行集及其关联的访问器。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
```

### <a name="parameters"></a>parameters

*TAccessor*<br/>
一个访问器类。

*TRowset*<br/>
行集类。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="members"></a>成员

### <a name="methods"></a>方法

|||
|-|-|
|[Bind](#bind)|创建绑定（在[CCommand：： Open](../../data/oledb/ccommand-open.md)中将 `bBind` 指定为**false**时使用。|
|[CAccessorRowset](#caccessorrowset)|构造函数。|
|[关闭](#close)|关闭行集和任何访问器。|
|[FreeRecordMemory](#freerecordmemory)|释放当前记录中需要释放的所有列。|
|[GetColumnInfo](#getcolumninfo)|实现[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))。|

## <a name="remarks"></a>备注

类 `TAccessor` 管理访问器。 类*TRowset*管理行集。

## <a name="caccessorrowsetbind"></a><a name="bind"></a>CAccessorRowset：： Bind

如果在[CCommand：： Open](../../data/oledb/ccommand-open.md)中指定 `bBind` 为**false** ，则创建绑定。

### <a name="syntax"></a>语法

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>返回值

标准的 HRESULT。

## <a name="caccessorrowsetcaccessorrowset"></a><a name="caccessorrowset"></a>CAccessorRowset：： CAccessorRowset

初始化 `CAccessorRowset` 对象。

### <a name="syntax"></a>语法

```cpp
CAccessorRowset();
```

## <a name="caccessorrowsetclose"></a><a name="close"></a>CAccessorRowset：： Close

释放所有活动的访问器和行集。

### <a name="syntax"></a>语法

```cpp
void Close();
```

### <a name="remarks"></a>备注

释放任何关联的内存。

## <a name="caccessorrowsetfreerecordmemory"></a><a name="freerecordmemory"></a>CAccessorRowset：： FreeRecordMemory

释放当前记录中需要释放的所有列。

### <a name="syntax"></a>语法

```cpp
void FreeRecordMemory();
```

## <a name="caccessorrowsetgetcolumninfo"></a><a name="getcolumninfo"></a>CAccessorRowset：： GetColumnInfo

从打开的行集中获取列信息。

### <a name="syntax"></a>语法

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 。

### <a name="return-value"></a>返回值

标准的 HRESULT。

### <a name="remarks"></a>备注

用户必须释放返回的列信息和字符串缓冲区。 当你使用[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)时，请使用此方法的第二个版本，并需要重写绑定。

有关详细信息，请参阅*OLE DB 程序员参考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 。

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)