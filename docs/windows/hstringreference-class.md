---
title: HStringReference 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: de3c7fe60432acfc3096ea19fc00cf371a7c4e92
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610501"
---
# <a name="hstringreference-class"></a>HStringReference 类

表示从现有字符串创建的 HSTRING。

## <a name="syntax"></a>语法

```cpp
class HStringReference;
```

## <a name="remarks"></a>备注

在新 HSTRING 的后备缓冲区的生存期不受 Windows 运行时。 调用方分配堆栈帧，以避免堆分配并消除内存泄漏的风险上的源字符串。 此外，调用方必须确保源字符串在附加 HSTRING 的生存期内保持不变。 有关详细信息，请参阅[WindowsCreateStringReference 函数](http://msdn.microsoft.com/0361bb7e-da49-4289-a93e-de7aab8712ac)。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[HStringReference::HStringReference 构造函数](../windows/hstringreference-hstringreference-constructor.md)|初始化的新实例**HStringReference**类。|

### <a name="members"></a>成员

|成员|描述|
|------------|-----------------|
|[HStringReference::CopyTo 方法](../windows/hstringreference-copyto-method.md)|复制当前**HStringReference**到 HSTRING 对象的对象。|
|[HStringReference::Get 方法](../windows/hstringreference-get-method.md)|检索基础 HSTRING 句柄的值。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[HStringReference::Operator= 运算符](../windows/hstringreference-operator-assign-operator.md)|另一个的值移**HStringReference**对象与当前**HStringReference**对象。|
|[HStringReference::Operator== 运算符](../windows/hstringreference-operator-equality-operator.md)|指示两个参数是否相等。|
|[HStringReference::Operator!= 运算符](../windows/hstringreference-operator-inequality-operator.md)|指示两个参数是否不相等。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`HStringReference`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)