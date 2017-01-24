---
title: "ComPtr::operator= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= 运算符"
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator= 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将值分配给当前 ComPtr。  
  
## 语法  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <  
   typename U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### 参数  
 `U`  
 类。  
  
 `other`  
 类型或其他 ComPtr的指针、引用、rvalue 引用。  
  
## 返回值  
 当前ComPtr的引用。  
  
## 备注  
 此运算符第一个版本将空值赋值给当前 ComPtr。  
  
 在第二个版本，如果指定的接口指针与当前 ComPtr 接口指针不一样，第二个接口指针分配给当前 ComPtr。  
  
 在第三版，分配的接口指针分配给当前 ComPtr。  
  
 在第四个版本，如果指定值的接口指针与当前 ComPtr 接口指针不一样，第二个接口指针分配给当前 ComPtr。  
  
 第五个版本是复制运算符；ComPtr 的引用分配给当前 ComPtr。  
  
 第六版本为使用移动语义的副本运算符；如果任何类型为静态转换然后分配给当前 ComPtr，为 ComPtr 的 rvalue 引用。  
  
 第七版本为使用移动语义的副本运算符；类型`U` 的ComPtr的右值引用是静态转换，分配给当前ComPtr。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)