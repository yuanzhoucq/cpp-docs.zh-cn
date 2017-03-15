---
title: "DontUseNewUseMake 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::DontUseNewUseMake"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DontUseNewUseMake 类"
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# DontUseNewUseMake 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
class DontUseNewUseMake;  
```  
  
## 备注  
 阻止使用 `new` 运算符在 RuntimeClass。  因此，您必须使用。[执行函数](../windows/make-function.md)  
  
## 成员  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[DontUseNewUseMake::operator new 运算符](../windows/dontusenewusemake-operator-new-operator.md)|在 RuntimeClass 重载运算符 `new` 并防止它。|  
  
## 继承层次结构  
 `DontUseNewUseMake`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)   
 [Make 函数](../windows/make-function.md)