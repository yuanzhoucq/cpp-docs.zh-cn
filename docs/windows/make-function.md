---
title: "Make 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Make"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Make 函数"
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Make 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化指定的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  使用此函数实例化在同一模块中定义的组件。  
  
## 语法  
  
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
  
#### 参数  
 `T`  
 从 `WRL::RuntimeClass`中继承的用户指定的类。  
  
 `TArg1`  
 传递给指定的运行时类参数 1 的类型。  
  
 `TArg2`  
 传递给指定的运行时类参数 2 的类型。  
  
 `TArg3`  
 传递给指定的运行时类参数 3 的类型。  
  
 `TArg4`  
 传递给指定的运行时类参数 4 的类型。  
  
 `TArg5`  
 传递给指定的运行时类参数 5 的类型。  
  
 `TArg6`  
 传递给指定的运行时类参数 6 的类型。  
  
 `TArg7`  
 传递给指定的运行时类参数 7 的类型。  
  
 `TArg8`  
 传递给指定的运行时类参数 8 的类型。  
  
 `TArg9`  
 传递给指定的运行时类参数 9 的类型。  
  
 `arg1`  
 传递给指定的运行时类参数的类型。  
  
 `arg2`  
 传递给参数4的运行时类参数的类型。  
  
 `arg3`  
 传递给参数4的运行时类参数的类型。  
  
 `arg4`  
 传递给参数4的运行时类参数的类型。  
  
 `arg5`  
 传递给指参数5运行时类参数的类型。  
  
 `arg6`  
 传递给参数6的运行时类参数的类型。  
  
 `arg7`  
 传递给的运行时类参数的类型。  
  
 `arg8`  
 传递给指定的运行时类参数的类型。  
  
 `arg9`  
 传递给参数9的运行时类参数的类型。  
  
## 返回值  
 如果成功；`ComPtr<T>` 对象，否则，返回 `nullptr`。  
  
## 备注  
 参见 [如何：直接实例化 WRL 组件](../windows/how-to-instantiate-wrl-components-directly.md) 理解差异此函数\) 和 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)之间和的示例。  
  
## 要求  
 **头文件：**implements.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)