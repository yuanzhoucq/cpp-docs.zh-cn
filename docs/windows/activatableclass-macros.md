---
title: "ActivatableClass 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ActivatableClass"
  - "ActivatableClassWithFactory"
  - "ActivatableClassWithFactoryEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivatableClassWithFactory"
  - "ActivatableClass"
  - "ActivatableClassWithFactoryEx"
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ActivatableClass 宏
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
ActivatableClass(  
   className  
);  
  
ActivatableClassWithFactory(  
   className,   
   factory  
);  
  
ActivatableClassWithFactoryEx(  
   className,   
   factory,   
   serverName  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `className`  
 要创建的类的名称。  
  
 `factory`  
 将创建指定类的实例的工厂。  
  
 `serverName`  
 在模块中指定工厂的子集的名称。  
  
## <a name="remarks"></a>备注  
 不要将这些宏与经典 COM 除非您使用 `#undef` 指令以确保 **__WRL_WINRT_STRICT\_\_** 移除宏定义。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [Module 类](../windows/module-class.md)