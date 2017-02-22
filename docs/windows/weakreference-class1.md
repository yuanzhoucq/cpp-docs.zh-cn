---
title: "WeakReference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::WeakReference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakReference 类"
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# WeakReference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
class WeakReference;  
```  
  
## 备注  
 表示可与 Windows 运行时还是经典 COM 的 *弱引用*。  弱引用表示可能发生或可能不可访问对象。  
  
 `WeakReference` 对象维护强 *引用*，是指针对对象和 *强引用计数*，在强引用副本数由 Resolve\(\) 方法中。  在强引用计数是非零时，强引用有效，并且对象是可访问的。  在强引用计数成为零时，强引用无效，并且对象是不可访问的。  
  
 弱对象通常表示由外部线程或应用程序控制其存在性的对象。  例如，构造从一个引用 WeakReference 对象到对象文件。  当文件打开时，强引用有效。  但是，文件，则关闭，强引用将失效。  
  
 WeakReference 方法是线程安全的。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[WeakReference::WeakReference 构造函数](../windows/weakreference-weakreference-constructor.md)|初始化 WeakReference 类的新实例。|  
|[WeakReference::~WeakReference 析构函数](../windows/weakreference-tilde-weakreference-destructor.md)|Deinitializes \(销毁\) WeakReference 类的当前实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[WeakReference::DecrementStrongReference 方法](../windows/weakreference-decrementstrongreference-method.md)|递减当前 WeakReference 对象的强引用计数。|  
|[WeakReference::IncrementStrongReference 方法](../windows/weakreference-incrementstrongreference-method.md)|递增当前 WeakReference 对象的强引用计数。|  
|[WeakReference::Resolve 方法](../windows/weakreference-resolve-method.md)|则强引用计数是非零，将指定的强引用指向当前的值。|  
|[WeakReference::SetUnknown 方法](../windows/weakreference-setunknown-method.md)|设置当前 WeakReference 对象的强引用为指定接口的指针。|  
  
## 继承层次结构  
 `WeakReference`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)