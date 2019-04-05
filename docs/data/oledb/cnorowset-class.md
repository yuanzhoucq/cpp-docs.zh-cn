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
ms.openlocfilehash: 6193e2d461761c53fb05e5c16b3914c56d545173
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035671"
---
# <a name="cnorowset-class"></a>CNoRowset 类

可以用作模板自变量 (`TRowset`) 用于[CCommand](../../data/oledb/ccommand-class.md)或[CTable](../../data/oledb/ctable-class.md)。

## <a name="syntax"></a>语法

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>参数

*TAccessor*<br/>
一个访问器类。 默认值为 `CAccessorBase`。

## <a name="remarks"></a>备注

如果命令不返回行集，请将 `CNoRowset` 用作模板参数。

`CNoRowset` 实现以下存根方法，其中每个对应于其他访问器类方法：

- `BindFinished` -指示绑定操作何时完成 (返回`S_OK`)。

- `Close` -释放行和当前 IRowset 接口。

- `GetIID` -检索连接点的接口 ID。

- `GetInterface` -检索接口。

- `GetInterfacePtr` -检索封装的接口指针。

- `SetAccessor` -将指针设置为访问器。

- `SetupOptionalRowsetInterfaces` -设置设置为行集的可选接口。

## <a name="requirements"></a>要求

**标头:** atldbcli.h

## <a name="see-also"></a>请参阅

[OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)