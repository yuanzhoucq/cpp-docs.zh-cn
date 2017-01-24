---
title: "ComPtrRef::operator== 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator=="
dev_langs: 
  - "C++"
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator== 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```cpp  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   const Details::ComPtrRef<ComPtr<U>>& b  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   decltype(__nullptr)  
);  
  
bool operator==(  
   decltype(__nullptr),  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
  
bool operator==(  
   const Details::ComPtrRef<ComPtr<T>>& a,  
   void* b  
);  
  
bool operator==(  
   void* b,  
   const Details::ComPtrRef<ComPtr<T>>& a  
);  
```  
  
#### 参数  
 `a`  
 获取 ComPtrRef对象的引用。  
  
 `b`  
 对另一个 ComPtrRef 对象的引用或是指向匿名类型 \(`void*`\)。  
  
## 返回值  
 如果 `a` 对象不等于的 `b`对象，第一个运算符为 `true` ;否则，返回 `false`。  
  
 如果 `a` 对象不等于 `nullptr`，将第二和第三个运算符为 `true` ;否则，返回 `false`。  
  
 如果对象的 `a` 相等的 `b`对象，第四、第五和运算符以生成 `true` ;否则，返回 `false`。  
  
## 备注  
 指示两个ComPtrRef 对象是否不相等。  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtrRef 类](../windows/comptrref-class.md)