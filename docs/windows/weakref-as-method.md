---
title: "Weakref:: As 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::As
dev_langs: C++
helpviewer_keywords: As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5160cb93d6660eaf990856a58d5b9379e911125e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="weakrefas-method"></a>WeakRef::As 方法
设置指定的 ComPtr 指针参数以表示指定接口。  
  
## <a name="syntax"></a>语法  
  
```  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<  
   typename U  
>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### <a name="parameters"></a>参数  
 `U`  
 接口 ID。  
  
 `ptr`  
 此操作完成后，返回一个表示参数 `U`的对象。  
  
## <a name="return-value"></a>返回值  
  
-   如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT，并且 `ptr` 被设置为 `nullptr`。  
  
-   如果此操作成功，但已释放当前 WeakRef 对象，则为 S_OK。 参数 `ptr` 被设置为 `nullptr`。  
  
-   如果此操作成功，但当前 WeakRef 对象不是派生自参数 `U`，则为 S_OK。 参数 `ptr` 被设置为 `nullptr`。  
  
## <a name="remarks"></a>备注  
 如果参数 `U` 为 IWeakReference，或者不是派生自 IInspectable，则出现错误。  
  
 第一个模板是应在代码中使用的表单。 第二个模板是支持 [自动](../cpp/auto-cpp.md) 类型推导关键字等 C++ 语言功能的内部专用帮助器。  
  
 从 Windows 10 SDK 开始，如果无法获得弱引用，此方法不再将 WeakRef 实例设置为 `nullptr` ，因此应避免使用检查 `nullptr`的 WeakRef 的错误检查代码。 相反，应检查`ptr`为`nullptr`。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [WeakRef 类](../windows/weakref-class.md)