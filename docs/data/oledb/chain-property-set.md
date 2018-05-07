---
title: CHAIN_PROPERTY_SET |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9db57535f3f0bc7653c80b83c3e0115727eed707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
此宏链接在一起属性组。  
  
## <a name="syntax"></a>语法  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>参数  
 *ChainClass*  
 [in]类链属性的名称。 这是已包含一个映射 （例如会话、 命令或数据源对象类） ATL 项目向导生成的类。  
  
## <a name="remarks"></a>备注  
 你可以链接从另一个类将属性设置为您自己的类，然后直接从你的类访问这些属性。  
  
> [!CAUTION]
>  尽量少使用此宏。 使用不当可能会导致使用者无法 OLE DB 一致性测试。  
  
## <a name="requirements"></a>要求  
 **标头：** atldb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板宏](../../data/oledb/macros-for-ole-db-provider-templates.md)