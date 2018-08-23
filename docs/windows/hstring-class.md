---
title: HString 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eea40f989e7d41afbff2773fcc5e6e5b2cfbafd2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613648"
---
# <a name="hstring-class"></a>HString 类

用于管理使用 RAII 模式 HSTRING 的生存期的帮助器类。

## <a name="syntax"></a>语法

```cpp
class HString;
```

## <a name="remarks"></a>备注

Windows 运行时提供通过 HSTRING 句柄的字符串的访问权限。 **HString**类提供便利函数和运算符以简化使用 HSTRING 句柄。 此类可以处理它拥有通过 RAII 模式在 HSTRING 的生存期。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[HString::HString 构造函数](../windows/hstring-hstring-constructor.md)|初始化的新实例**HString**类。|
|[HString::~HString 析构函数](../windows/hstring-tilde-hstring-destructor.md)|销毁的当前实例**HString**类。|

### <a name="members"></a>成员

|名称|描述|
|----------|-----------------|
|[HString::Set 方法](../windows/hstring-set-method.md)|设置的当前值**HString**为指定的宽字符字符串的对象或**HString**参数。|
|[HString::Attach 方法](../windows/hstring-attach-method.md)|将指定相关联**HString**对象与当前**HString**对象。|
|[HString::CopyTo 方法](../windows/hstring-copyto-method.md)|复制当前**HString**到 HSTRING 对象的对象。|
|[HString::Detach 方法](../windows/hstring-detach-method.md)|解除指定的关联**HString**从其基础值的对象。|
|[HString::GetAddressOf 方法](../windows/hstring-getaddressof-method.md)|检索指向基础 HSTRING 句柄。|
|[HString::Get 方法](../windows/hstring-get-method.md)|检索基础 HSTRING 句柄的值。|
|[HString::Release 方法](../windows/hstring-release-method.md)|删除基础字符串值，并初始化当前**HString**对象为空值。|
|[HString::MakeReference 方法](../windows/hstring-makereference-method.md)|创建`HStringReference`从指定的字符串参数的对象。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[HString::Operator= 运算符](../windows/hstring-operator-assign-operator.md)|另一个的值移**HString**对象与当前**HString**对象。|
|[HString::Operator== 运算符](../windows/hstring-operator-equality-operator.md)|指示两个参数是否相等。|
|[HString::Operator!= 运算符](../windows/hstring-operator-inequality-operator.md)|指示两个参数是否不相等。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`HString`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)