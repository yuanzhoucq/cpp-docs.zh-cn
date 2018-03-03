---
title: "Module:: create 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f025c446dd6a7dab9b37d126d65e640a02b939b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="modulecreate-method"></a>Module::Create 方法
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
 `object`和`method`结合使用参数。 点到最后一个实例对象在释放模块中的最后一个实例对象时。  
  
 `method`  
 `object`和`method`结合使用参数。 指向方法的最后一个实例的对象在释放模块中的最后一个实例对象时。  
  
## <a name="return-value"></a>返回值  
 对模块的引用。  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
[Module 类](../windows/module-class.md)

 