---
title: "region、endregion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.endregion"
  - "endregion_CPP"
  - "region_CPP"
  - "vc-pragma.region"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "endregion 杂注"
  - "杂注, endregion"
  - "杂注, 区域"
  - "区域杂注"
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# region、endregion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

利用 **\#pragma region**，您可以指定在使用 Visual Studio 代码编辑器的[大纲功能](../Topic/Outlining.md)时可展开或折叠的代码块。  
  
## 语法  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### 参数  
 `comment`（可选）  
 将在代码编辑器中显示的注释。  
  
 *name*（可选）  
 区域的名称。此名称将显示在代码编辑器中。  
  
## 备注  
 **\#pragma endregion** 标记 **\#pragma region** 块的结尾。  
  
 `#region` 块必须通过 **\#pragma endregion** 指令终止。  
  
## 示例  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)