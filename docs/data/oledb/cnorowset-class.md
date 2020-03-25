---
title: CNoRowset 类
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211466"
---
# <a name="cnorowset-class"></a>CNoRowset 类

可用作[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md)的模板参数（`TRowset`）。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>parameters

*TAccessor*<br/>
一个访问器类。 默认为 `CAccessorBase`。

## <a name="remarks"></a>备注

如果命令不返回行集，请将 `CNoRowset` 用作模板参数。

`CNoRowset` 将实现以下存根方法，其中每个方法都对应于其他访问器类方法：

- `BindFinished`-表示绑定完成（返回 `S_OK`）。

- `Close`-释放行和当前的 IRowset 接口。

- `GetIID` - 检索连接点的接口 ID。

- `GetInterface`-检索接口。

- `GetInterfacePtr` - 检索封装的接口指针。

- `SetAccessor`-设置指向访问器的指针。

- `SetupOptionalRowsetInterfaces`-设置行集的可选接口。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>另请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)
