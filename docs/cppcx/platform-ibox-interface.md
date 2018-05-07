---
title: 'Platform:: ibox 接口 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs:
- C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7894eceb2f345303400eec9b0490db58b3c3583f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="platformibox-interface"></a>Platform::IBox 接口
[Platform::IBox](../cppcx/platform-ibox-interface.md) 接口是 `Windows::Foundation::IReference` 接口的 C++ 名称。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 装箱值的类型。  
  
### <a name="remarks"></a>备注  
 `IBox<T>` 接口主要用于在内部表示可以为 null 的值类型，如 [值类和结构 (C++/CX)](../cppcx/value-classes-and-structs-c-cx.md)中所述。 该接口还用于对传递给采用参数类型 `Object^`的 C++ 方法的值类型进行装箱。 可以将输入参数显式声明为 `IBox<SomeValueType>`。 有关示例，请参阅[装箱](../cppcx/boxing-c-cx.md)。  
  
### <a name="requirements"></a>要求  
  
### <a name="members"></a>成员  
 `Platform::IBox` 接口继承自 [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) 接口。 `IBox` 包括以下成员：  
  
 **属性**  
  
|方法|描述|  
|------------|-----------------|  
|[值](#value)|返回此 `IBox` 实例以前存储的未装箱值。|  

## <a name="value"></a> Ibox:: Value 属性
返回此对象中最初存储的值。  
  
### <a name="syntax"></a>语法  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 装箱值的类型。  
  
### <a name="property-valuereturn-value"></a>属性值/返回值  
 返回此对象中最初存储的值。  
  
### <a name="remarks"></a>备注  
 有关示例，请参阅[装箱](../cppcx/boxing-c-cx.md)。  
  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)