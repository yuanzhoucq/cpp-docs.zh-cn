---
title: "编译器错误 C2220 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2220
dev_langs: C++
helpviewer_keywords: C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc31519b2153c66ea9bab42f536ba7c6be5b2a10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2220"></a>编译器错误 C2220
警告视为错误-没有生成的对象文件  
  
 [/WX](../../build/reference/compiler-option-warning-level.md)告知编译器将所有警告视为错误。 由于发生了错误，未生成对象或可执行文件。  
  
 时，此错误仅出现**/WX**设置标志，并且在编译期间出现警告。 若要纠正此错误，必须消除项目中的每个警告。  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>若要纠正错误，请使用以下方法之一  
  
-   解决导致项目中出现警告的问题。  
  
-   在较低警告等级进行编译-例如，使用**/W3**而不是**/W4**。  
  
-   使用[警告](../../preprocessor/warning.md)杂注来禁用还是禁止在某个具体的警告。  
  
-   不要使用**/WX**进行编译。