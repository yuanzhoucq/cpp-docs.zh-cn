---
title: InterfaceListHelper 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
dev_langs:
- C++
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ad091114d6be6f35f1a0341961dc5122840ace8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### <a name="parameters"></a>参数  
 `T0`  
 模板参数 0，这是必需的。  
  
 `T1`  
 模板参数，1，即默认情况下未指定。  
  
 `T2`  
 模板参数，2，即默认情况下未指定。第三个模板参数。  
  
 `T3`  
 模板参数，3，即默认情况下未指定。  
  
 `T4`  
 模板参数，4，即默认情况下未指定。  
  
 `T5`  
 模板参数，5，即默认情况下未指定。  
  
 `T6`  
 模板参数，6，即默认情况下未指定。  
  
 `T7`  
 模板参数，7，即默认情况下未指定。  
  
 `T8`  
 模板参数，8，即默认情况下未指定。  
  
 `T9`  
 模板参数，9，即默认情况下未指定。  
  
## <a name="remarks"></a>备注  
 通过应用指定的模板参数自变量的以递归方式构建 InterfaceList 类型。  
  
 InterfaceListHelper 模板使用模板参数`T0`来定义的第一个数据成员 InterfaceList 结构，然后以递归方式应用 InterfaceListHelper 模板剩余的任何模板参数。 InterfaceListHelper 停止时没有剩余的模板参数。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`TypeT`|InterfaceList 类型的同义词。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `InterfaceListHelper`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)