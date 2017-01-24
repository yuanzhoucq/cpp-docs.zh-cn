---
title: "scoped_d3d_access_lock 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scoped_d3d_access_lock 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

快捷键视图对象上的 D3D 访问锁的 RAII 包装器。  
  
## 语法  
  
```  
class scoped_d3d_access_lock;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[scoped\_d3d\_access\_lock::scoped\_d3d\_access\_lock 构造函数](../Topic/scoped_d3d_access_lock::scoped_d3d_access_lock%20Constructor.md)|已重载。  构造 `scoped_d3d_access_lock` 对象。  当对象超出范围时，释放锁。|  
|[scoped\_d3d\_access\_lock::~scoped\_d3d\_access\_lock 析构函数](../Topic/scoped_d3d_access_lock::~scoped_d3d_access_lock%20Destructor.md)|释放关联 `accelerator_view` 对象上的 D3D 访问锁定。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[scoped\_d3d\_access\_lock::operator\= 运算符](../Topic/scoped_d3d_access_lock::operator=%20Operator.md)|从另一 `scoped_d3d_access_lock` 取得锁的所有权。|  
  
## 继承层次结构  
 `scoped_d3d_access_lock`  
  
## 要求  
 **标头：**amprt.h  
  
 **命名空间：**concurrency::direct3d  
  
## 请参阅  
 [Concurrency::direct3d 命名空间](../../../parallel/amp/reference/concurrency-direct3d-namespace.md)