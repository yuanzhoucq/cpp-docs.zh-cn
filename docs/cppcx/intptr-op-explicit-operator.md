---
title: "IntPtr::op_explicit 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::IntPtr::op_explicit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IntPtr::op_explicit 方法"
ms.assetid: cc52e9d5-fe73-471b-8cff-d9f684ba6e20
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# IntPtr::op_explicit 运算符
将指定参数转换为 IntPtr 或指向 IntPtr 值的指针。  
  
## 语法  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
#### 参数  
 value1  
 指向句柄或 IntPtr 的指针。  
  
 value2  
 可以转换为 IntPtr 的 32 位整数。  
  
 value3  
 一个 IntPtr。  
  
## 返回值  
 第一个和第二个运算符返回 IntPtr。 第三个运算符返回指向当前 IntPtr 表示的值的指针。  
  
## 要求  
 **支持的最低客户端版本：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **支持的最低服务器版本：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空间：**Platform  
  
 **元数据：**platform.winmd  
  
## 请参阅  
 [Platform::IntPtr 值类](../cppcx/platform-intptr-value-class.md)