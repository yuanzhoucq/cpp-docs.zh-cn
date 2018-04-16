---
title: 'Comptr:: Operator = 运算符 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b221ff75e250830feefbbd2d3db0d8697095c96
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="comptroperator-operator"></a>ComPtr::operator= 运算符
为当前 ComPtr 赋值。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <typename U>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 一个类。  
  
 `other`  
 对某个类型或另一个 ComPtr 的指针、 引用或右值引用。  
  
## <a name="return-value"></a>返回值  
 对当前 ComPtr 的引用。  
  
## <a name="remarks"></a>备注  
 此运算符的第一个版本将分配给当前 ComPtr 的空值。  
  
 在第二个版本中，如果分配的接口指针不是当前 ComPtr 接口指针相同，则第二个的接口指针分配给当前 ComPtr 中。  
  
 在第三个版本中，分配的接口指针分配给当前 ComPtr。  
  
 在第四个版本中，如果分配的值的接口指针不是当前 ComPtr 接口指针相同，则第二个的接口指针分配给当前 ComPtr 中。  
  
 第五个版本是复制运算符;ComPtr 的引用分配给当前 ComPtr。  
  
 第六个版本是复制运算符使用移动语义;对 ComPtr 如果任何类型已进行静态强制转换，然后分配给当前 ComPtr 的右值引用。  
  
 第七个版本是复制运算符使用移动语义;对类型的 ComPtr 的右值引用`U`是静态然后强制转换和分配给当前 ComPtr。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)