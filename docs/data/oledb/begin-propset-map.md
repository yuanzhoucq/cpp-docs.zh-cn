---
title: "BEGIN_PROPSET_MAP |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_PROPSET_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d92723ec126f23d479189ccb4629f70256949ab6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="beginpropsetmap"></a>BEGIN_PROPSET_MAP
标记的属性的开头设置的映射条目。  
  
## <a name="syntax"></a>语法  
  
```  
  
BEGIN_PROPSET_MAP(  
Class   
)  
  
```  
  
#### <a name="parameters"></a>参数  
 *类*  
 [in]指定设置此属性的类。 可以在以下的 OLE DB 对象中指定属性集：  
  
-   [数据源对象](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [会话对象](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [命令](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## <a name="example"></a>示例  
 下面是示例属性集映射：  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>另请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)   
 [创建 OLE DB 提供程序](../../data/oledb/creating-an-ole-db-provider.md)