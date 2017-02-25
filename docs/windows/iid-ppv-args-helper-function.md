---
title: "IID_PPV_ARGS_Helper 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/IID_PPV_ARGS_Helper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IID_PPV_ARGS_Helper 函数"
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IID_PPV_ARGS_Helper 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

验证指定的参数类型从 `IUnknown` 接口派生。  
  
> [!IMPORTANT]
>  此模版支持WRL基础结构，但不应在代码中直接使用。  请改用 [IID\_PPV\_ARGS](http://msdn.microsoft.com/library/windows/desktop/ee330727.aspx) 。  
  
## 语法  
  
```  
template<  
   typename T  
>  
void** IID_PPV_ARGS_Helper(  
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp  
);  
```  
  
#### 参数  
 `T`  
 参数的类型`pp`  
  
 `pp`  
 双间接指针。  
  
## 返回值  
 参数转换为 `pp` 指针指向 `void`。  
  
## 备注  
 如果模板参数 `T` 从 `IUnknown`派生，而编译时错误。  
  
## 要求  
 **标头：**client.h  
  
## 请参阅  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/zh-cn/00000000-0000-0000-0000-000000000000)