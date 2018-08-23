---
title: IDBCreateCommandImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b67fc55a8af2bed554254732832cbd6486d2420
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572029"
---
# <a name="idbcreatecommandimpl-class"></a>IDBCreateCommandImpl 类
提供的实现[IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\))接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 会话对象派生自`IDBCreateCommandImpl`。  
  
 *CommandClass*  
 命令类。  

## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[CreateCommand](#createcommand)|创建新的命令。|  
  
## <a name="remarks"></a>备注  
 要获取新的命令的会话对象上一可选接口。  

## <a name="createcommand"></a> Idbcreatecommandimpl:: Createcommand
创建新的命令并返回所请求的接口。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[idbcreatecommand:: Createcommand](/previous-versions/windows/desktop/ms709772\(v=vs.85\))中*OLE DB 程序员参考*。  
  
 某些参数对应于*OLE DB 程序员参考*中所述的不同名称的参数`IDBCreateCommand::CreateCommand`:  
  
|OLE DB 模板参数|*OLE DB 程序员参考*参数|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)