---
title: "VerifyInterfaceHelper 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::VerifyInterfaceHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VerifyInterfaceHelper 结构"
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# VerifyInterfaceHelper 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   bool isWinRTInterface,  
   typename I  
>  
struct VerifyInterfaceHelper;  
  
template <  
   typename I  
>  
struct VerifyInterfaceHelper<false, I>;  
```  
  
#### 参数  
 `I`  
 分辨接口：  
  
 `isWinRTInterface`  
  
## 备注  
 验证当前模板参数指定的接口满足特定要求。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[VerifyInterfaceHelper::Verify 方法](../windows/verifyinterfacehelper-verify-method.md)||  
  
## 继承层次结构  
 `VerifyInterfaceHelper`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)