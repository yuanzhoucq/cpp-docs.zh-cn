---
title: ActivateInstance 函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0bf945dd8225ca3c153d7f497ded6b83ebd022d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855570"
---
# <a name="activateinstance-function"></a>ActivateInstance 函数
注册并检索在指定的类 id。 定义的指定类型的实例  
  
## <a name="syntax"></a>语法  
  
```  
template<typename T>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 要激活的类型。  
  
 `activatableClassId`  
 定义参数的类 ID 的名称`T`。  
  
 `instance`  
 此操作完成后，对的实例的引用`T`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为指示错误的原因的 HRESULT 错误。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** windows:: foundation  
  
## <a name="see-also"></a>请参阅  
 [Windows::Foundation 命名空间](../windows/windows-foundation-namespace.md)