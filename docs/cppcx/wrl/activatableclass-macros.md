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
ms.openlocfilehash: 7bc3d789d6c0d304aa170d59dff23a97a67061d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214254"
---
# <a name="activatableclass-macros"></a>ActivatableClass 宏

填充内部缓存，其中包含可创建指定类的实例的工厂。

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

### <a name="parameters"></a>parameters

*className*<br/>
要创建的类的名称。

*集*<br/>
将创建指定类的实例的工厂。

*serverName*<br/>
指定模块中工厂子集的名称。

## <a name="remarks"></a>备注

不要将这些宏与经典 COM 一起使用，除非使用 `#undef` 指令来确保删除 `__WRL_WINRT_STRICT__` 宏定义。

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Module 类](module-class.md)
