---
title: IAccessorImpl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d62deeb487fded5895bbd47332a0f8a6ad7bbce6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl 类
提供的实现[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, 
          class BindType = ATLBINDINGS,
          class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 行集或命令对象类。  
  
 `BindType`  
 绑定信息的存储单位。 默认值是**ATLBINDINGS**结构 （请参阅 atldb.h）。  
  
 `BindingVector`  
 列信息的存储单位。 默认值是[CAtlMap](../../atl/reference/catlmap-class.md)其中一个关键因素是**HACCESSOR**值和值的元素是一个指向`BindType`结构。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|构造函数。|  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|将引用计数添加到现有的访问器。|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|从一组绑定创建一个访问器。|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|访问器中返回的绑定。|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|释放访问器。|  
  
## <a name="remarks"></a>备注  
 这是必需的对于行集和命令。 OLE DB 需要提供程序实现**HACCESSOR**，即指向数组的标记[DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx)结构。 **HACCESSOR**s 由`IAccessorImpl`是地址`BindType`结构。 默认情况下，`BindType`定义为**ATLBINDINGS**中`IAccessorImpl`的模板定义。 `BindType` 提供使用一种机制`IAccessorImpl`跟踪中的元素数其**DBBINDING**数组以及引用计数和访问器标志。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)