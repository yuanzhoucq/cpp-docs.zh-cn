---
title: "runtime_exception 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::direct3d_abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "runtime_exception 类"
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# runtime_exception 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

在C\+\+ Accelerated Massive Parallelism \(AMP\) library库中的异常的基础类型。  
  
## 语法  
  
```  
class runtime_exception : public std::exception;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[runtime\_exception::runtime\_exception 构造函数](../Topic/runtime_exception::runtime_exception%20Constructor.md)|初始化 `runtime_exception` 类的新实例。|  
|[runtime\_exception::~runtime\_exception 析构函数](../Topic/runtime_exception::~runtime_exception%20Destructor.md)|销毁 `runtime_exception` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[runtime\_exception::get\_error\_code 方法](../Topic/runtime_exception::get_error_code%20Method.md)|返回导致异常的错误代码。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[runtime\_exception::operator\= 运算符](../Topic/runtime_exception::operator=%20Operator.md)|将指定的 `runtime_exception` 对象的内容复制到此对象中。|  
  
## 继承层次结构  
 `exception`  
  
 `runtime_exception`  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [Concurrency 命名空间 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)