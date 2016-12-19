---
title: "CAtlFileMapping Class | Microsoft Docs"
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
  - "ATL::CAtlFileMapping<T>"
  - "ATL.CAtlFileMapping"
  - "ATL::CAtlFileMapping"
  - "CAtlFileMapping"
  - "ATL.CAtlFileMapping<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFileMapping class"
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlFileMapping Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类表示一个内存映射文件，添加转换运算符将 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
typename T= char  
>  
class CAtlFileMapping :  
public CAtlFileMappingBase  
```  
  
#### 参数  
 `T`  
 用于转换运算符的数据类型。  
  
## 成员  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CAtlFileMapping::operator T\*](../Topic/CAtlFileMapping::operator%20T*.md)|允许 `CAtlFileMapping` 对象隐式强制转换为 `T`**\***的。|  
  
## 备注  
 此选件类添加一个转换运算符允许 `CAtlFileMapping` 对象隐式强制转换为 `T`**\***的。  基类提供其他成员，[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)。  
  
## 继承层次结构  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## 要求  
 **Header:** atlfile.h  
  
## 请参阅  
 [CAtlFileMappingBase Class](../../atl/reference/catlfilemappingbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)