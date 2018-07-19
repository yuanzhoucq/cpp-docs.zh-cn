---
title: 'Module:: create 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99ede64c239909956f1f767db34a2a6a14c02314
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874884"
---
# <a name="modulecreate-method"></a>Module::Create 方法
创建模块的实例。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW static Module& Create();  
template<typename T>  
WRL_NOTHROW static Module& Create(  
   T callback  
);  
template<typename T>  
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
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
[Module 类](../windows/module-class.md)

 