---
title: 使函数成为 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
dev_langs:
- C++
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0076445f21bcbad5ca7028c088cddfdbdcacf8cd
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013696"
---
# <a name="make-function"></a>Make 函数
初始化指定的 Windows 运行时类。 使用此函数实例化同一个模块中定义的组件。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8,  
   TArg9 &&arg9  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2  
);  
template <  
   typename T,  
   typename TArg1  
>  
ComPtr<T> Make(  
   TArg1 &&arg1  
);  
template <  
   typename T  
>  
ComPtr<T> Make();  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 用户指定的类，该类继承`WRL::RuntimeClass`。  
  
 *TArg1*  
 传递到指定的运行时类的参数 1 的类型。  
  
 *TArg2*  
 传递到指定的运行时类的参数 2 的类型。  
  
 *TArg3*  
 传递到指定的运行时类的参数 3 的类型。  
  
 *TArg4*  
 传递到指定的运行时类的参数 4 的类型。  
  
 *TArg5*  
 参数 5 传递到指定的运行时类的类型。  
  
 *TArg6*  
 自 6 变量传递给指定的运行时类的类型。  
  
 *TArg7*  
 7 传递给自变量指定的运行时类的类型。  
  
 *TArg8*  
 8 传递给自变量指定的运行时类的类型。  
  
 *TArg9*  
 参数 9，传递到指定的运行时类的类型。  
  
 *arg1*  
 传递到指定的运行时类的参数 1。  
  
 *Arg2*  
 传递到指定的运行时类的参数 2。  
  
 *arg3*  
 传递到指定的运行时类的参数 3。  
  
 *了 arg4*  
 传递到指定的运行时类的参数 4。  
  
 *arg5*  
 参数传递到指定的运行时类 5。  
  
 *了 arg6*  
 参数传递到指定的运行时类 6。  
  
 *arg7*  
 参数传递到指定的运行时类 7。  
  
 *arg8*  
 参数传递到指定的运行时类 8。  
  
 *arg9*  
 参数传递到指定的运行时类 9。  
  
## <a name="return-value"></a>返回值  
 一个`ComPtr<T>`对象，如果成功; 否则为**nullptr**。  
  
## <a name="remarks"></a>备注  
 请参阅[如何： 直接实例化 WRL 组件](../windows/how-to-instantiate-wrl-components-directly.md)若要了解此函数之间的差异并[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)，和示例。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)