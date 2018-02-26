---
title: "CEnumerator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d0ac9fe73b2d8b37e345ddcf602dd98316eedf46
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cenumerator-class"></a>CEnumerator 类
使用一个 OLE DB 枚举器对象，它公开[ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx)接口以返回行集描述所有数据源和枚举数。  
  
## <a name="syntax"></a>语法

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[查找](../../data/oledb/cenumerator-find.md)|搜索可用的提供程序（数据源），查找一个具有指定名称的提供程序。|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|检索当前记录的 `IMoniker` 接口。|  
|[打开](../../data/oledb/cenumerator-open.md)|打开枚举器。|  
  
## <a name="remarks"></a>备注  
 你可以检索**ISourcesRowset**从此类间接的数据。  
  
## <a name="requirements"></a>惠?  
 **标头：**atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)