---
title: 'Chaininterfaces:: Iidcount 常量 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs:
- C++
helpviewer_keywords:
- IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5327b706fb6b461d7bbe449df5482c8f0c485ae
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount 常量
模板参数 `I0` 到 `I9` 指定的接口中包含的接口 ID 总数。  
  
## <a name="syntax"></a>语法  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>返回值  
 接口 ID 的总数。  
  
## <a name="remarks"></a>备注  
 模板参数 `I0` 和 `I1` 为必需，参数 `I2` 到 `I9` 为可选。每个接口的 IID 计数一般为 1。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ChainInterfaces 结构](../windows/chaininterfaces-structure.md)