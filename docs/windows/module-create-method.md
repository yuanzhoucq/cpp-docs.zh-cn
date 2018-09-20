---
title: 'Module:: create 方法 |Microsoft Docs'
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
ms.openlocfilehash: a8b84bcaec7dbadfb7b735264df12f7e958dcd20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444689"
---
# <a name="modulecreate-method"></a>Module::Create 方法

创建模块的实例。

## <a name="syntax"></a>语法

```cpp
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

### <a name="parameters"></a>参数

*T*<br/>
模块类型。

*回调*<br/>
释放该模块的最后一个实例对象时调用。

*object*<br/>
*对象*并*方法*结合使用的参数。 点到最后一个实例对象时释放模块中的最后一个实例对象。

*方法*<br/>
*对象*并*方法*结合使用的参数。 指向最后一个实例对象时释放模块中的最后一个实例对象的方法。

## <a name="return-value"></a>返回值

对模块引用。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)