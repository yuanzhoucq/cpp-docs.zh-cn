---
title: "CRestrictions 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df38bc85775c67084e8952210ab368d930439114
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="crestrictions-class"></a>CRestrictions 类
泛型类，您可以指定架构行集的限制。  
  
## <a name="syntax"></a>语法

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
        public CSchemaRowset <T, nRestrictions>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 访问器使用的类。  
  
 `nRestrictions`  
 架构行集的限制列数。  
  
 `pguid`  
 指向架构的 GUID 的指针。  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[打开](../../data/oledb/crestrictions-open.md)|返回一个结果集，根据用户提供的限制。|  
  
## <a name="requirements"></a>惠?  
 **标头：** atldbsch.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 使用者模板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 使用者模板参考](../../data/oledb/ole-db-consumer-templates-reference.md)