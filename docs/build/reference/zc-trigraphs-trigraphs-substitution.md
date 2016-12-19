---
title: "/Zc:trigraphs（Trigraphs 替换） | Microsoft Docs"
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
  - "/Zc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 (C++)"
  - "Conformance 编译器选项"
  - "Zc 编译器选项 (C++)"
  - "-Zc 编译器选项 (C++)"
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zc:trigraphs（Trigraphs 替换）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 **\/Zc:trigraphs** 时，编译器会通过使用相应的标点字符替换 trigraph 字符序列。  若要关闭 trigraph 替换，请指定 **\/Zc:trigraphs\-**。  默认情况下，**\/Zc:trigraphs** 处于关闭状态。  
  
## 语法  
  
```  
/Zc:trigraphs[-]  
```  
  
## 备注  
 三字符组由两个连续的问号（“??”）及后跟的第三个唯一字符组成。  例如，编译器将通过使用‘\#’替换“??\=”三字符组。  对于使用的字符集未包含某些标点字符的便捷图形表示形式的 C 源文件，可在其中使用三字符组。  
  
 有关 C\/C\+\+ trigraphs 的列表以及说明如何使用 trigraphs 的示例，请参见 [三字符组](../../c-language/trigraphs.md)。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)   
 [三字符组](../../c-language/trigraphs.md)