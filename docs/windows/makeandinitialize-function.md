---
title: "MakeAndInitialize 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f759a71117d00e5f01f2f0f53f93fef2ba47a4fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize 函数
初始化指定的 Windows 运行时类。 使用此函数来实例化同一个模块中定义的组件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <typename T, typename I,   
typename TArg1,   
typename TArg2,   
typename TArg3,   
typename TArg4,   
typename TArg5,   
typename TArg6,   
typename TArg7,   
typename TArg8,   
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 用户指定的类，该类继承`WRL::RuntimeClass`。  
  
 `TArg1`  
 传递到指定的运行时类的参数 1 的类型。  
  
 `TArg2`  
 传递到指定的运行时类的参数 2 的类型。  
  
 `TArg3`  
 传递到指定的运行时类的参数 3 的类型。  
  
 `TArg4`  
 传递到指定的运行时类的参数 4 的类型。  
  
 `TArg5`  
 传递到指定的运行时类的参数 5 的类型。  
  
 `TArg6`  
 传递到指定的运行时类的参数 6 的类型。  
  
 `TArg7`  
 参数 7 传递给指定的运行时类的类型。  
  
 `TArg8`  
 参数 8 传递给指定的运行时类的类型。  
  
 `TArg9`  
 传递到指定的运行时类的参数 9 的类型。  
  
 `arg1`  
 传递到指定的运行时类的参数 1。  
  
 `arg2`  
 传递到指定的运行时类的参数 2。  
  
 `arg3`  
 参数传递到指定的运行时类 3。  
  
 `arg4`  
 参数传递到指定的运行时类 4。  
  
 `arg5`  
 参数传递到指定的运行时类 5。  
  
 `arg6`  
 参数传递到指定的运行时类 6。  
  
 `arg7`  
 参数传递到指定的运行时类 7。  
  
 `arg8`  
 参数传递到指定的运行时类 8。  
  
 `arg9`  
 参数传递到指定的运行时类 9。  
  
## <a name="return-value"></a>返回值  
 一个 `HRESULT` 值。  
  
## <a name="remarks"></a>备注  
 请参阅[如何： 直接实例化 WRL 组件](../windows/how-to-instantiate-wrl-components-directly.md)若要了解此函数之间的差异和[Microsoft::WRL::Make](../windows/make-function.md)，和示例。  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)