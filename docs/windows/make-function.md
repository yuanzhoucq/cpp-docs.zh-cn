---
title: Make 函数 |Microsoft 文档
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
ms.openlocfilehash: f381a00b5ac1f105080355f1d3e3cd15efa5abf8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="make-function"></a>Make 函数
初始化指定的 Windows 运行时类。 使用此函数来实例化同一个模块中定义的组件。  
  
## <a name="syntax"></a>语法  
  
```  
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
 A`ComPtr<T>`对象成功; 否则为如果`nullptr`。  
  
## <a name="remarks"></a>备注  
 请参阅[如何： 直接实例化 WRL 组件](../windows/how-to-instantiate-wrl-components-directly.md)若要了解此函数之间的差异和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)，和示例。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)