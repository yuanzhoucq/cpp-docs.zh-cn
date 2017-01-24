---
title: "WeakReference::Resolve 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::WeakReference::Resolve"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Resolve 方法"
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakReference::Resolve 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### 参数  
 `riid`  
 是一个ID接口。  
  
 `ppvObject`  
 该操作完成，强烈当前的引用复制，则强引用计数是非零值。  
  
## 返回值  
  
-   S\_OK，如果该操作成功和强引用计数为零。  `ppvObject` 参数设置为 `nullptr`。  
  
-   S\_OK，如果该操作成功和强引用计数为非零。  `ppvObject` 参数设置为强引用。  
  
-   否则，此 HRESULT 指示原因的此操作失败。  
  
## 备注  
 则强引用计数是非零，将指定的强引用指向当前的值。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [WeakReference 类](../windows/weakreference-class1.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)