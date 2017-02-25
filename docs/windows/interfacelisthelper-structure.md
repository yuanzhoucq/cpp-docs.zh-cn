---
title: "InterfaceListHelper 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceListHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InterfaceListHelper 结构"
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# InterfaceListHelper 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename T0,  
   typename T1 = Nil,  
   typename T2 = Nil,  
   typename T3 = Nil,  
   typename T4 = Nil,  
   typename T5 = Nil,  
   typename T6 = Nil,  
   typename T7 = Nil,  
   typename T8 = Nil,  
   typename T9 = Nil  
>  
struct InterfaceListHelper;  
  
template <  
   typename T0  
>  
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;  
```  
  
#### 参数  
 `T0`  
 模板参数，需要 0。  
  
 `T1`  
 模板参数 1 中，默认情况下不指定的。  
  
 `T2`  
 模板参数 2 中，默认情况下不指定的。第三个模板参数。  
  
 `T3`  
 模板参数 3 中，默认情况下不指定的。  
  
 `T4`  
 模板参数 4 中，默认情况下不指定的。  
  
 `T5`  
 模板参数 5 中，默认情况下不指定的。  
  
 `T6`  
 模板参数 6 中，默认情况下不指定的。  
  
 `T7`  
 模板参数 7 中，默认情况下不指定的。  
  
 `T8`  
 模板参数 8 中，默认情况下不指定的。  
  
 `T9`  
 模板参数 9 中，默认情况下不指定的。  
  
## 备注  
 通过以递归方式应用指定的模板参数 InterfaceList 生成类型。  
  
 InterfaceListHelper 模板使用模板参数 `T0` 定义 InterfaceList 结构的第一个数据成员，然后以递归方式应用 InterfaceListHelper 模板给剩余的模板参数。  当没有剩余的模板参数，InterfaceListHelper 停止。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`TypeT`|类型是InterfaceList的同义词。|  
  
## 继承层次结构  
 `InterfaceListHelper`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)