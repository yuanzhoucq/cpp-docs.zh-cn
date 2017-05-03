---
title: "String::CompareOrdinal 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::CompareOrdinal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::CompareOrdinal"
ms.assetid: dd4a7acc-fd23-4f1e-af85-64b9086f63f8
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::CompareOrdinal 方法
通过估计对象所表示的两个字符值中相应字符的数字值来比较两个 `String` 对象。  
  
## 语法  
  
```cpp  
  
int CompareOrdinal(  
           String^ str1,   
           String^ str2)  
  
```  
  
#### 参数  
 `str1`  
 第一个字符串对象。  
  
 `str2`  
 第二个字符串对象。  
  
## 返回值  
 一个整数，指示两个比较字之间的词法关系。 下表列出可能的返回值。  
  
|值|条件|  
|-------|--------|  
|\-1|`str1` 小于 `str2`。|  
|0|`str1` 等于 `str2`。|  
|1|`str1` 大于 `str2`。|  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**vccorlib.h  
  
## 请参阅  
 [Platform::String 类](../cppcx/platform-string-class.md)