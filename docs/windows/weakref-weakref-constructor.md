---
title: "WeakRef::WeakRef 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef::WeakRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakRef, 构造函数"
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# WeakRef::WeakRef 构造函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

初始化 WeakRef 类的新实例。  
  
## 语法  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### 参数  
 `ptr`  
 指针、引用或 Rvalue 引用初始化当前 WeakRef 对象的现有对象。  
  
## 备注  
 第一构造函数初始化空的 WeakRef 对象。  第二个构造函数初始化从指针的一 WeakRef 对象到 IWeakReference 接口。  第三个构造函数初始化从一个引用 WeakRef 对象到 ComPtr\< IWeakReference\> 对象。  第四、第五构造函数初始化另一个 WeakRef 对象的一 WeakRef 对象。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [WeakRef 类](../windows/weakref-class.md)