---
title: "CEnumerator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CEnumerator
dev_langs: C++
helpviewer_keywords: CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a64ac02e7b16bfab70966ffaf2a1897ae955f8c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cenumerator-class"></a>CEnumerator 类
使用一个 OLE DB 枚举器对象，它公开[ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx)接口以返回行集描述所有数据源和枚举数。  
  
## <a name="syntax"></a>语法  
  
```  
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