---
title: 'Comptr:: Comptr 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59a7e67eb27ef72a414e7e8129aa7bf781604426
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr 构造函数
初始化 ComPtr 类的新实例。 重载提供默认、复制、移动和转换构造函数。  
  
## <a name="syntax"></a>语法  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 `other` 参数的类型。  
  
 `other`  
 一个 `U` 类型的对象。  
  
## <a name="return-value"></a>返回值  
  
## <a name="remarks"></a>备注  
 第一个构造函数是默认构造函数，哪些隐式创建一个空对象。 第二个构造函数指定[__nullptr](../windows/nullptr-cpp-component-extensions.md)，这将显式创建一个空对象。  
  
 从指定指针的对象，第三个构造函数创建的对象。  
  
 第四个和第五个构造函数是复制构造函数。 第五个构造函数将对象转换为当前类型的情况下将它复制。  
  
 第六个和第七个构造函数是移动构造函数。 第七个构造函数将对象转换为当前类型的情况下将它移动。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [ComPtr 类](../windows/comptr-class.md)