---
title: ActivatableClass 宏
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
ms.openlocfilehash: 1b50d9ba59ef8aebe4eca388ee30449f4ddd53de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660663"
---
# <a name="activatableclass-macros"></a>ActivatableClass 宏

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

### <a name="parameters"></a>参数

*类名*<br/>
要创建的类的名称。

*工厂*<br/>
将创建指定类的实例的工厂。

*服务器名称*<br/>
一个模块中指定的工厂的子集的名称。

## <a name="remarks"></a>备注

执行不使用经典 COM 使用这些宏，除非使用`#undef`指令以确保`__WRL_WINRT_STRICT__`移除宏定义。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)