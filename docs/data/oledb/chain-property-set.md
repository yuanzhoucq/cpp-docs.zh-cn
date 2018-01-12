---
title: "CHAIN_PROPERTY_SET |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CHAIN_PROPERTY_SET
dev_langs: C++
helpviewer_keywords: CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1de482b285f24ce9ed68bd70fa7b21b0b66a4d56
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
此宏链接在一起属性组。  
  
## <a name="syntax"></a>语法  
  
```  
  
CHAIN_PROPERTY_SET(  
ChainClass   
)  
  
```  
  
#### <a name="parameters"></a>参数  
 *ChainClass*  
 [in]类链属性的名称。 这是已包含一个映射 （例如会话、 命令或数据源对象类） ATL 项目向导生成的类。  
  
## <a name="remarks"></a>备注  
 你可以链接从另一个类将属性设置为您自己的类，然后直接从你的类访问这些属性。  
  
> [!CAUTION]
>  尽量少使用此宏。 使用不当可能会导致使用者无法 OLE DB 一致性测试。  
  
## <a name="requirements"></a>惠?  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)