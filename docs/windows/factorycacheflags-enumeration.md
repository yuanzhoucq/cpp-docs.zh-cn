---
title: "FactoryCacheFlags 枚举 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::FactoryCacheFlags
dev_langs: C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb4efeb716255ae67a01fca7cf04a54816e227d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 枚举
确定是否缓存工厂对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，将工厂缓存策略指定为[ModuleType](../windows/moduletype-enumeration.md)模板参数在创建时[模块](../windows/module-class.md)对象。 若要重写此策略，请在创建工厂对象时指定 `FactoryCacheFlags` 值。  
  
|||  
|-|-|  
|`FactoryCacheDefault`|将使用 `Module` 对象的缓存策略。|  
|`FactoryCacheEnabled`|启用工厂缓存，无论用于创建 `ModuleType` 对象的 `Module` 模板参数如何都是如此。|  
|`FactoryCacheDisabled`|禁用工厂缓存，无论用于创建 `ModuleType` 对象的 `Module` 模板参数如何都是如此。|  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)