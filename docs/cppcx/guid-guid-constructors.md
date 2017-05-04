---
title: "Guid::Guid 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Guid::Guid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform, Guid::Guid"
  - "Guid::Guid"
ms.assetid: dfa4dcad-1c3b-481f-9f60-05141b9788d1
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Guid::Guid 构造函数
初始化 Guid 结构的新实例。  
  
## 语法  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  
);  
  
    Guid(   
        GUID m  
);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n  
);  
```  
  
#### 参数  
 `a`  
 GUID 的前 4 个字节。  
  
 `b`  
 GUID 的下两个字节。  
  
 `c`  
 GUID 的下两个字节。  
  
 `d`  
 GUID 的下一个字节。  
  
 `e`  
 GUID 的下一个字节。  
  
 `f`  
 GUID 的下一个字节。  
  
 `g`  
 GUID 的下一个字节。  
  
 `h`  
 GUID 的下一个字节。  
  
 `i`  
 GUID 的下一个字节。  
  
 `j`  
 GUID 的下一个字节。  
  
 `k`  
 GUID 的下一个字节。  
  
 `m`  
 所定义的 GUID。  
  
 `n`  
 GUID 的其余 8 个字节。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::Guid 值类](../cppcx/platform-guid-value-class.md)