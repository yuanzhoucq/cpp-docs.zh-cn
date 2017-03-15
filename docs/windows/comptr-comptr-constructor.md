---
title: "ComPtr::ComPtr 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::ComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtr, 构造函数"
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# ComPtr::ComPtr 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 ComPtr 类的新实例。  重载提供默认，复制个，、移动和转换该构造函数。  
  
## 语法  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### 参数  
 `U`  
 `other` 参数的类型。  
  
 `other`  
 `U` 类型的对象。  
  
## 返回值  
  
## 备注  
 第一个构造函数。默认构造函数，显示创建空的对象。  第二个构造函数 [\_\_nullptr](../windows/nullptr-cpp-component-extensions.md)，显式创建一个对象。  
  
 第三个构造函数创建从指向指定的对象。  
  
 第四、第五构造函数是复制构造函数。  第五构造函数将对象是当前转换为类型。  
  
 第六和第七构造函数是将构造函数。  第七构造函数将对象是当前转换为类型。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)