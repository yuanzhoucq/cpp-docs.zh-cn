---
title: "InterfaceTraits::FillArrayWithIid 方法 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FillArrayWithIid 方法"
ms.assetid: 73583177-adc9-4fcb-917d-fa7e6d07c990
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InterfaceTraits::FillArrayWithIid 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
__forceinline static void FillArrayWithIid(  
   _Inout_ unsigned long &index,  
   _In_ IID* iids  
);  
  
```  
  
#### 参数  
 `index`  
 对包含一个从零开始的索引的字段上。  
  
 `iids`  
 测试用例 ID 的数组。  
  
## 备注  
 `Base` 接口 ID 分配给索引参数指定数组的元素。  
  
 数组元素，仅修改对 API 的相反；此名称并非是整个数组。  
  
 有关 `Base`的更多信息，请参见 [InterfaceTraits 结构](../windows/interfacetraits-structure.md)Typedefs 的公共部分。  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [InterfaceTraits 结构](../windows/interfacetraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)