---
title: IDBCreateCommandImpl 类
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: 4a4978401ba90e3a7a91ac40cc1b0668adf12ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210712"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl 类

提供[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))接口的实现。

## <a name="syntax"></a>语法

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>parameters

*T*<br/>
派生自 `IDBCreateCommandImpl`的会话对象。

*CommandClass*<br/>
Command 类。

## <a name="requirements"></a>要求

**标头：** atldb.h

## <a name="members"></a>成员

### <a name="interface-methods"></a>接口方法

|||
|-|-|
|[CreateCommand](#createcommand)|创建新的命令。|

## <a name="remarks"></a>备注

用于获取新命令的 session 对象上的可选接口。

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a>IDBCreateCommandImpl：： CreateCommand

创建新的命令并返回所请求的接口。

### <a name="syntax"></a>语法

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>parameters

请参阅*OLE DB 程序员参考*中的[IDBCreateCommand：： CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) 。

一些参数对应于*OLE DB 程序员的*不同名称的引用参数，如 `IDBCreateCommand::CreateCommand`中所述：

|OLE DB 模板参数|*OLE DB 程序员引用*参数|
|--------------------------------|------------------------------------------------|
|*ppvCommand*|*ppCommand*|

## <a name="see-also"></a>另请参阅

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
