---
title: GetActivationFactory 函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2cbb5be3603f79a7df1cb330ca06775357666854
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570306"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory 函数
检索指定模板参数的类型的激活工厂。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 模板参数，用于指定的激活工厂的类型。  
  
 *activatableClassId*  
 激活工厂可以生成的类的名称。  
  
 *工厂*  
 此操作完成后，对类型的激活工厂的引用*T*。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为错误 HRESULT，指示此操作失败的原因。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** windows:: foundation  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation 命名空间](../windows/windows-foundation-namespace.md)