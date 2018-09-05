---
title: 'Platform:: array 类 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Array Constructors
- VCCORLIB/Namespace not found::Platform::Array::Value
dev_langs:
- C++
helpviewer_keywords:
- Platform::Array Class
ms.assetid: 7815ab40-88c5-42b0-83b8-081cef0cda31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa689035a6e95db7f9471d4972063ec35486e0cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753212"
---
# <a name="platformarray-class"></a>Platform::Array 类
表示可以跨应用程序二进制接口 (ABI) 接收和传递的一维可修改数组。  
  
## <a name="syntax"></a>语法  
  
```cpp    
template <typename T>  
private ref class Array<TArg, 1> :   
    public WriteOnlyArray<TArg, 1>,  
    public IBoxArray<TArg>   
```  
  
### <a name="members"></a>成员  
 Platform:: array 继承其所有方法从[platform:: writeonlyarray 类](../cppcx/platform-writeonlyarray-class.md)并实现`Value`的属性[platform:: iboxarray 接口](../cppcx/platform-iboxarray-interface.md)。  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Array 构造函数](#ctor)|初始化指定的类模板参数类型的一维可数组*T*。|  
  
### <a name="methods"></a>方法  
 请参阅[platform:: writeonlyarray 类](../cppcx/platform-writeonlyarray-class.md)。  
  
### <a name="properties"></a>属性  
  
|||  
|-|-|  
|[Array::Value](#value)|检索当前数组的句柄。|  
  
### <a name="remarks"></a>备注  
 Array 类是密封类，不能被继承。  
  
 Windows 运行时类型系统不支持交错数组的概念，因此不能将传递 IVector < platform:: array\<T >> 作为返回值或方法参数。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。  
  
 有关何时以及如何使用 platform:: array 的详细信息，请参阅[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。  
  
 Windows 运行时类型系统不支持交错数组的概念，因此不能将传递 IVector < platform:: array\<T >> 作为返回值或方法参数。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。  
  
 此类在编译器会自动包括的 vccorlib.h 标头中定义。 它是在 IntelliSense 中而不是在对象浏览器中可见的因为它不是在 platform.winmd 中定义的公共类型。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  

 
## <a name="ctor"></a>  Array 构造函数
初始化指定的类模板参数类型的一维可数组*T*。  
  
## <a name="syntax"></a>语法  
  
```cpp  
Array(unsigned int size);  
Array(T* data, unsigned int size);    
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 类模板参数。  
  
 `size`  
 数组中的元素数。  
  
 `data`  
 指向用于初始化该数组对象的类型 `T` 的数据数组的指针。  
  
### <a name="remarks"></a>备注  
 有关如何创建 platform:: array 实例的详细信息，请参阅[Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)。

## <a name="get"></a>  Array:: get 方法
检索对指定索引位置上数组元素的引用。  
  
## <a name="syntax"></a>语法  
  
```cpp    
T& get(unsigned int index)  const;  
```  
  
#### <a name="parameters"></a>参数  
 `index`  
 从零开始的索引，用来标识数组元素。 最小索引为 0，最大索引为指定的值`size`中的参数[Array 构造函数](#ctor)。  
  
### <a name="return-value"></a>返回值  
 `index` 参数指定的数组元素。  
  
## <a name="value"></a>  Array:: value 属性
检索当前数组的句柄。  
  
## <a name="syntax"></a>语法  
  
```cpp 
property Array^ Value;  
```  
  
### <a name="return-value"></a>返回值  
 当前数组的句柄。  

## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)   
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)