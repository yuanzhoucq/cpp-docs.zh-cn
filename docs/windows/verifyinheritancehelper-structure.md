---
title: "VerifyInheritanceHelper 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::VerifyInheritanceHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VerifyInheritanceHelper 结构"
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# VerifyInheritanceHelper 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
#### 参数  
 `I`  
 一个类型。  
  
 `Base`  
 另一个类型。  
  
## 备注  
 测试一个接口如果从另一个接口派生。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[VerifyInheritanceHelper::Verify 方法](../windows/verifyinheritancehelper-verify-method.md)|测试当前模板参数指定两的接口并确定一个接口如果从其他派生。|  
  
## 继承层次结构  
 `VerifyInheritanceHelper`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)