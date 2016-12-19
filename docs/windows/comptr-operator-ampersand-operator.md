---
title: "ComPtr::operator&amp; 运算符 | Microsoft Docs"
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
  - "client/Microsoft::WRL::ComPtr::operator&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator& 运算符"
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtr::operator&amp; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放接口与此 `ComPtr` 对象然后检索 `ComPtr` 对象的地址。  
  
## 语法  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## 返回值  
 对当前 `ComPtr` 操作的弱引用。  
  
## 备注  
 此方法不同于 [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) 此方法释放对接口指针的引用。  使用 `ComPtr::GetAddressOf`，当需要接口指针的地址，但不要释放该接口。  
  
## 要求  
 **标头：**client.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [ComPtr 类](../windows/comptr-class.md)