---
title: "ComPtr::operator!= 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator!="
dev_langs: 
  - "C++"
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator!= 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示两个ComPtr对象是否不相等。  
  
## 语法  
  
```cpp  
bool operator!=(  
   const ComPtr<T>& a,  
   const ComPtr<U>& b  
);  
  
bool operator!=(  
   const ComPtr<T>& a,  
   decltype(__nullptr)  
);  
  
bool operator!=(  
   decltype(__nullptr),  
   const ComPtr<T>& a  
);  
  
```  
  
#### 参数  
 `a`  
 获取ComPtr对象的引用。  
  
 `b`  
 对另一ComPtr对象的引用。  
  
## 返回值  
 如果 `a` 对象不等于的 `b`对象，第一个运算符为 `true` ;否则，返回 `false`。  
  
 如果 `a` 对象不等于 `nullptr`，将第二和第三个运算符为 `true` ;否则，返回 `false`。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)   
 [ComPtr 类](../windows/comptr-class.md)