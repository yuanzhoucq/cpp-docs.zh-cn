---
title: CreateClassFactory 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214053"
---
# <a name="createclassfactory-function"></a>CreateClassFactory 函数

创建为指定类生成实例的工厂。

## <a name="syntax"></a>语法

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>parameters

*flag*<br/>
一个或多个[RuntimeClassType](runtimeclasstype-enumeration.md)枚举值的组合。

*entry*<br/>
指向包含参数*riid*的初始化和注册信息的[CreatorMap](creatormap-structure.md)的指针。

*riid*<br/>
对接口 ID 的引用。

*ppFactory*<br/>
如果此操作成功完成，则为指向类工厂的指针。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="remarks"></a>备注

如果模板参数*工厂*不是从接口 `IClassFactory`派生的，则会发出断言错误。

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL::Wrappers::Details 命名空间](microsoft-wrl-wrappers-details-namespace.md)
