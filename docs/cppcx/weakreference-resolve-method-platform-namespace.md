---
title: "WeakReference::Resolve 方法（平台命名空间） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/WeakReference::Resolve"
ms.assetid: 78bbcadd-89d0-4863-a4e8-1d84040eed7d
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WeakReference::Resolve 方法（平台命名空间）
如果对象不再存在，则返回原始 ref 类的句柄或 `nullptr`。  
  
## 语法  
  
```vb  
  
template<typename T>  
T^ Resolve() const  
```  
  
#### 参数  
  
## 属性值\/返回值  
 WeakReference 对象先前关联的 ref 类的句柄或 nullptr。  
  
## 备注  
  
## 示例  
 这是代码示例的描述。  
  
```  
  
Bar^ bar = ref new Bar(); //use bar... if (bar != nullptr) { WeakReference wr(bar); Bar^ newReference = wr.Resolve<Bar>(); }  
```  
  
 注意类型参数是 T 而非 T^。  
  
## 请参阅  
 [Platform 命名空间](../cppcx/platform-namespace-c-cx.md)