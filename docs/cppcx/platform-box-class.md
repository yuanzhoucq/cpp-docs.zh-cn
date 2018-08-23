---
title: 'Platform:: box 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
dev_langs:
- C++
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7def63199666a9dba0a1628031129ce584e0fcec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605954"
---
# <a name="platformbox-class"></a>Platform::Box 类
使值类型（例如 `Windows::Foundation::DateTime` ）或标量类型（例如 `int` ）能够存储在 `Platform::Object` 类型中。 通常没有必要显式使用 `Box` ，因为当你将值类型强制转换为 `Object^`时会发生隐式装箱：  
  
### <a name="syntax"></a>语法  
  
```cpp  
ref class Box abstract;  
```  
  ### <a name="remarks"></a>备注  
  
### <a name="requirements"></a>要求  
 **标头：** vccorlib.h  
  
 **命名空间：** Platform
|成员|描述|  
|------------|-----------------|
|[Box](#ctor)|创建`Box`，它可封装指定类型的值。|
|[运算符框&lt;const T&gt;^](#box-const-t)|实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。|
|[运算符框&lt;const 易失性 T&gt;^](#box-const-volatile-t)|启用从 `const volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。 |
|[运算符框&lt;T&gt;^](#box-t)|实现从值类 `T` 到 `Box<T>` 的装箱转换。|
|[运算符框&lt;易失性 T&gt;^](#box-volatile-t)|启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。|
|[Box:: operator T](#t)|实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。| 
## <a name="ctor"></a> Box:: box 构造函数
创建`Box`，它可封装指定类型的值。 | |[Value 属性](#value)|返回值，封装在`Box`对象。 |  
### <a name="syntax"></a>语法  
  
```cpp  
Box(T valueArg);  
```  
  
### <a name="parameters"></a>参数  
 `valueArg`  
 要将装箱值的类型，例如， `int`， `bool`， `float64`， `DateTime`。  
  

## <a name="box-const-t"></a> Box:: operator 框&lt;const T&gt;^ 运算符
实现从 `const` 值类 `T` 或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。  
  
### <a name="syntax"></a>语法  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 任何值类、值结构或枚举类型。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>返回值  
 一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。  
  
## <a name="box-const-volatile-t"></a> Box:: operator 框&lt;const 易失性 T&gt;^ 运算符
启用从 `const volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。  
  
### <a name="syntax"></a>语法  
  
```cpp  
operator Box<const volatile T>^(const volatile T valueType);  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>返回值  
 一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。  
  
## <a name="box-t"></a> Box:: operator 框&lt;T&gt;^ 运算符
实现从值类 `T` 到 `Box<T>` 的装箱转换。  
  
### <a name="syntax"></a>语法  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>返回值  
 一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。  
  
## <a name="box-volatile-t"></a> Box:: operator 框&lt;易失性 T&gt;^ 运算符
启用从 `volatile` 值类 `T` 或 `enum` 类型 `T` 到 `Box<T>` 的装箱转换。  
  
### <a name="syntax"></a>语法  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>返回值  
 一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。  
  
## <a name="t"></a>  Box:: operator T 运算符
实现从 `T` 值类或 `enum` 类 `T` 到 `Box<T>` 的装箱转换。  
  
### <a name="syntax"></a>语法  
  
```cpp  
operator Box<T>^(T valueType);  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 任何枚举类型、值类或值结构。 包括中的内置类型[默认命名空间](../cppcx/default-namespace.md)。  
  
### <a name="return-value"></a>返回值  
 一个`Platform::Box<T>^`在一个 ref 类的实例，它表示原始值装箱。  
  

## <a name="value"></a> Box:: value 属性
返回在 `Box` 对象中封装的值。  
  
### <a name="syntax"></a>语法  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
### <a name="return-value"></a>返回值  
 返回具有和其装箱前最初具有的类型相同类型的装箱值。  
  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)   
 [装箱](../cppcx/boxing-c-cx.md)