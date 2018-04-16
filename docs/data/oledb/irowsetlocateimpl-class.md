---
title: "IRowsetLocateImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetLocateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 27af767c9104159d6c398db226a5a45a36e01e2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl 类
实现 OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)接口，从行集提取任意行。  
  
## <a name="syntax"></a>语法

```cpp
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
       T,   
       RowsetInterface,   
       RowClass,   
       MapClass>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 从派生的类`IRowsetLocateImpl`。  
  
 `RowsetInterface`  
 从派生的类`IRowsetImpl`。  
  
 `RowClass`  
 存储单位**HROW**。  
  
 `MapClass`  
 提供程序持有的所有行句柄存储单元。  
  
 `BookmarkKeyType`  
 书签的地方，例如 long 类型的值或字符串类型。 普通书签必须具有至少两个字节的长度。 (单字节长度保留用于 OLE DB[标准书签](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK_FIRST**， **DBBMK_LAST**，和**DBBMK_INVALID**。)  
  
 `BookmarkType`  
 用于维护书签数据关系映射机制。  
  
 `BookmarkMapClass`  
 所有的行句柄的存储单位持有书签。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|比较两个的书签。|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|提取行开头指定偏移量从书签的行。|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|提取匹配指定的书签的行。|  
|[Hash](../../data/oledb/irowsetlocateimpl-hash.md)|返回哈希值用于指定书签。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|书签的数组。|  
  
## <a name="remarks"></a>备注  
 `IRowsetLocateImpl` 是的 OLE DB 模板实现[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)接口。 `IRowsetLocate` 用于从行集提取任意行。 未实现此接口的行集是`sequential`行集。 当`IRowsetLocate`位于第 0 列行集上是行的书签; 读取此列将获取可用来对同一行重新定位一个书签值。  
  
 `IRowsetLocateImpl` 用于在提供程序中实现书签支持。 书签是占位符 （索引行集上），启用快速返回到行的使用者允许高速数据访问。 提供程序确定书签可以唯一标识行。 使用`IRowsetLocateImpl`方法，你可以比较书签、 提取行，偏移量，提取行的书签，并返回用于书签的哈希值。  
  
 若要在行集中支持 OLE DB 书签，请从此类继承的行集。  
  
 有关实现书签支持的信息，请参阅[用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)中*Visual c + + 程序员指南*和[书签](https://msdn.microsoft.com/en-us/library/ms709728.aspx)中*OLE DB 程序员参考*平台 SDK 中。  
  
## <a name="requirements"></a>惠?  
 **标头**: atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [用于书签的提供程序支持](../../data/oledb/provider-support-for-bookmarks.md)   
 [定位标记](https://msdn.microsoft.com/en-us/library/ms709728.aspx)