---
title: "FactoryCacheFlags 枚举 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::FactoryCacheFlags"
dev_langs: 
  - "C++"
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# FactoryCacheFlags 枚举
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定是否缓存工厂对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，将工厂缓存策略指定为 [ModuleType](../windows/moduletype-enumeration.md) 模板参数在创建时 [模块](../windows/module-class.md) 对象。 若要重写此策略，请在创建工厂对象时指定 `FactoryCacheFlags` 值。  
  
|||  
|-|-|  
|`FactoryCacheDefault`|将使用 `Module` 对象的缓存策略。|  
|`FactoryCacheEnabled`|启用工厂缓存，无论用于创建 `ModuleType` 对象的 `Module` 模板参数如何都是如此。|  
|`FactoryCacheDisabled`|禁用工厂缓存，无论用于创建 `ModuleType` 对象的 `Module` 模板参数如何都是如此。|  
  
## <a name="requirements"></a>要求  
 **标头︰** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft:: wrl Namespace](../windows/microsoft-wrl-namespace.md)