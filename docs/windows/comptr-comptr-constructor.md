---
title: 'Comptr:: Comptr 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3a632c96c39ccd40f008556287af95944530cdc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871170"
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
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)