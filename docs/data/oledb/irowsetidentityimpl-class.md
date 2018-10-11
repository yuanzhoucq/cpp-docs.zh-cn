---
title: IRowsetIdentityImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b47cbf2b30323cf51881ebaae9f546001a2d61b3
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081495"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl 类

实现 OLE DB [IRowsetIdentity](/previous-versions/windows/desktop/ms715913)接口，可对行标识进行测试。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, class RowClass = CSimpleRow>  
class ATL_NO_VTABLE IRowsetIdentityImpl   
   : public IRowsetIdentity  
```  
  
### <a name="parameters"></a>参数  

*T*<br/>
一个类派生自`IRowsetIdentityImpl`。  
  
*RowClass*<br/>
为存储单元`HROW`。  

## <a name="requirements"></a>要求  

**标头：** atldb.h  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IsSameRow](#issamerow)|比较两个行句柄，以了解它们是否引用同一行。|  
  
## <a name="issamerow"></a> Irowsetidentityimpl:: Issamerow

比较两个行句柄，以了解它们是否引用同一行。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[IRowsetIdentity::IsSameRow](/previous-versions/windows/desktop/ms719629)中*OLE DB 程序员参考*。  
  
### <a name="remarks"></a>备注  

若要比较的行句柄，此方法强制转换`HROW`句柄`RowClass`成员和调用`memcmp`指针。  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)