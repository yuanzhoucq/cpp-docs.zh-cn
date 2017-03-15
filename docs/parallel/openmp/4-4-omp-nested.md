---
title: "4.4 OMP_NESTED | Microsoft Docs"
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
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.4 OMP_NESTED
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`OMP_NESTED` 环境变量启用或禁用嵌套并行，除非嵌套并行通过调用 `o`**mp\_set\_nested** 库实例启用或禁用。  设置为 **TRUE**，嵌套并行有效;如果它设置为 **错误**，嵌套并行被禁用。  默认值为 **错误**。  
  
 示例：  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## 交叉引用:  
  
-   `omp_set_nested` 功能，请参见中的第 40 页的 [第3.1.9部分](../../parallel/openmp/3-1-9-omp-set-nested-function.md) 。