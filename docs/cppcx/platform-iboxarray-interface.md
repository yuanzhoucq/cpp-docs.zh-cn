---
title: "Platform:: iboxarray 接口 |Microsoft 文档"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs: C++
helpviewer_keywords: Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 421f8517b8a96c40bb44dd959eba90b1bf903113
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray 接口
`IBoxArray` 是在应用程序二进制接口 (ABI) 之间传递或在 `Platform::Object^` 元素的集合中存储（如 XAML 控件）的值类型数组的包装器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 每个数组元素中的装箱值的类型。  
  
### <a name="remarks"></a>备注  
 `IBoxArray`是 C + + /cli CX 名称`Windows::Foundation::IReferenceArray`。  
  
### <a name="members"></a>成员  
 `IBoxArray` 接口继承自 `IValueType` 接口。 `IBoxArray` 还包括这些成员：  
  
|方法|描述|  
|------------|-----------------|  
|[值](#value)|返回此 `IBoxArray` 实例以前存储的未装箱数组。|  

## <a name="value"></a>Iboxarray:: Value 属性
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
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)