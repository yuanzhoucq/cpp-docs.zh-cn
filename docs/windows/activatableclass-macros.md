---
title: "ActivatableClass 宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs: C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6cd75d4075cfe590151f7746281640febb334ce9
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="activatableclass-macros"></a>ActivatableClass 宏

填充内部缓存包含一个工厂，它可以创建指定的类的实例。

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

### <a name="parameters"></a>参数

*类名*  
要创建的类名称。  

*工厂*  
将创建指定类的实例的工厂。

*serverName*  
模块中指定工厂的子集名称。

## <a name="remarks"></a>备注

执行不与经典 COM 一起使用这些宏，除非使用`#undef`指令以确保**&#95; &#95;WRL_WINRT_STRICT &#95; &#95;**删除宏定义。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Module 类](../windows/module-class.md)