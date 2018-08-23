---
title: ComPtr 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a20dd5e2fb43dd5caae7a5185260d8c88637d33
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597957"
---
# <a name="comptr-class"></a>ComPtr 类

创建表示模板参数指定的接口的 *智能指针* 类型。 **ComPtr**自动维护基础接口指针的引用计数，并在引用计数变为零时发布接口。

## <a name="syntax"></a>语法

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>参数

*T*  
该接口的**ComPtr**表示。

*U*  
将类传递给其当前**ComPtr**为友元。 （使用此参数的模板受到保护。）

## <a name="remarks"></a>备注

`ComPtr<>` 声明表示基础接口指针的类型。 使用`ComPtr<>`声明一个变量，然后使用箭头成员访问运算符 (`->`) 访问接口成员函数。

有关智能指针的详细信息，请参阅"COM 智能指针"部分[COM Coding Practices](/windows/desktop/LearnWin32/com-coding-practices)MSDN Library 中的主题。

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`InterfaceType`|指定的类型的同义词*T*模板参数。|

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[ComPtr::ComPtr 构造函数](../windows/comptr-comptr-constructor.md)|初始化的新实例**ComPtr**类。 重载提供默认、复制、移动和转换构造函数。|
|[ComPtr::~ComPtr 析构函数](../windows/comptr-tilde-comptr-destructor.md)|取消初始化的实例**ComPtr**。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[ComPtr::As 方法](../windows/comptr-as-method.md)|返回**ComPtr**对象，表示由指定的模板参数标识的接口。|
|[ComPtr::AsIID 方法](../windows/comptr-asiid-method.md)|返回**ComPtr**对象，表示由指定的接口 ID 标识的接口|
|[ComPtr::AsWeak 方法](../windows/comptr-asweak-method.md)|检索对当前对象的弱引用。|
|[ComPtr::Attach 方法](../windows/comptr-attach-method.md)|将相关联这**ComPtr**与由当前模板类型参数指定的接口类型。|
|[ComPtr::CopyTo 方法](../windows/comptr-copyto-method.md)|将复制与此相关联的当前或指定界面**ComPtr**到指定的输出指针。|
|[ComPtr::Detach 方法](../windows/comptr-detach-method.md)|取消关联这**ComPtr**从它所代表的接口。|
|[ComPtr::Get 方法](../windows/comptr-get-method.md)|检索指向与此相关联的接口**ComPtr**。|
|[ComPtr::GetAddressOf 方法](../windows/comptr-getaddressof-method.md)|检索的地址[ptr_](../windows/comptr-ptr-data-member.md)数据成员，其中包含指向表示此接口的指针**ComPtr**。|
|[ComPtr::ReleaseAndGetAddressOf 方法](../windows/comptr-releaseandgetaddressof-method.md)|释放与此关联的接口**ComPtr** ，然后检索的地址[ptr_](../windows/comptr-ptr-data-member.md)数据成员，其中包含指向已释放接口的指针。|
|[ComPtr::Reset](../windows/comptr-reset.md)|释放对与此相关联的接口指针的所有引用**ComPtr**。|
|[ComPtr::Swap 方法](../windows/comptr-swap-method.md)|交换当前管理的接口**ComPtr**管理指定的接口与**ComPtr**。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[ComPtr::InternalAddRef 方法](../windows/comptr-internaladdref-method.md)|与此相关联的接口的引用计数递增**ComPtr**。|
|[ComPtr::InternalRelease 方法](../windows/comptr-internalrelease-method.md)|执行与此相关联的接口上的 COM 释放操作**ComPtr**。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[ComPtr::operator Microsoft::WRL::Details::BoolType 运算符](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|指示是否**ComPtr**管理接口的对象生存期。|
|[ComPtr::operator& 运算符](../windows/comptr-operator-ampersand-operator.md)|检索当前的地址**ComPtr**。|
|[ComPtr::operator= 运算符](../windows/comptr-operator-assign-operator.md)|将值分配给当前**ComPtr**。|
|[ComPtr::operator-> 运算符](../windows/comptr-operator-arrow-operator.md)|检索指向当前模板参数所指定类型的指针。|
|[ComPtr::operator== 运算符](../windows/comptr-operator-equality-operator.md)|指示两个**ComPtr**对象是否相等。|
|[ComPtr::operator!= 运算符](../windows/comptr-operator-inequality-operator.md)|指示两个**ComPtr**对象是否不相等。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[ComPtr::ptr_ 数据成员](../windows/comptr-ptr-data-member.md)|包含指向相关联，并管理此接口的指针**ComPtr**。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`ComPtr`

## <a name="requirements"></a>要求

**标头：** client.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)