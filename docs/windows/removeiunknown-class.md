---
title: "RemoveIUnknown 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::RemoveIUnknown"
dev_langs: 
  - "C++"
ms.assetid: 998e711a-7d1a-44c6-a016-e6167aa40863
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# RemoveIUnknown 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename T  
>  
struct RemoveIUnknown;  
  
template <  
   typename T  
>  
class RemoveIUnknown : public T;  
```  
  
#### 参数  
 `T`  
 类。  
  
## 备注  
 对与 `IUnknown`等效。的类型，基于类型，但其 `QueryInterface`、`AddRef`和 `Release` 成员函数。  
  
 默认情况下，COM 方法的虚拟 `QueryInterface`、`AddRef`和发布方法。  但是，`ComPtr` 不需要开销虚方法。  `RemoveIUnknown` 通过在 private、其 `QueryInterface`、`AddRef`和 `Release` 方法来消除该系统开销。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`ReturnType`|模板参数与 `T` 等效，但类型的同义词具有其由成员。|  
  
## 继承层次结构  
 `T`  
  
 `RemoveIUnknown`  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)