---
title: "Platform::IBoxArray 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IBoxArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::IBoxArray"
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 5
---
# Platform::IBoxArray 接口
`IBoxArray` 是在应用程序二进制接口 \(ABI\) 之间传递或在 `Platform::Object^` 元素的集合中存储（如 XAML 控件）的值类型数组的包装器。  
  
## 语法  
  
```cpp  
template <typename T>  
interface class IBoxArray  
```  
  
#### 参数  
 `T`  
 每个数组元素中的装箱值的类型。  
  
## 备注  
 `IBoxArray` 是 [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] 的 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] \(`Windows::Foundation::IReferenceArray`\) 名称。  
  
## 成员  
 `IBoxArray` 接口继承自 `IValueType` 接口。`IBoxArray` 还包括这些成员：  
  
|方法|描述|  
|--------|--------|  
|值|返回此 `IBoxArray` 实例以前存储的未装箱数组。|  
  
## 请参阅  
 [Array 和 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)