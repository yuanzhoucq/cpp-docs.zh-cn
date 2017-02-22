---
title: "Module::Create 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module::Create"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Create 方法"
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Module::Create 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建模块的实例。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW static Module& Create();  
template<  
   typename T  
>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<  
   typename T  
>  
WRL_NOTHROW static Module& Create(  
   _In_ T* object,  
   _In_ void (T::* method)()  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 模块类型。  
  
 `callback`  
 释放该模块的最后一个实例对象时调用。  
  
 `object`  
  `object` 和 `method` 参数结合使用。 点到最后一个实例对象时在释放模块中的最后一个实例对象。  
  
 `method`  
  `object` 和 `method` 参数结合使用。 指向该方法在释放模块中的最后一个实例对象时的最后一个实例对象。  
  
## <a name="return-value"></a>返回值  
 对该模块的引用。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
[Module 类](../windows/module-class.md)

 