---
title: "编译器警告 （等级 4） C4001 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4001
dev_langs: C++
helpviewer_keywords: C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 808b51724ce626371c011057295d3343cc02c984
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4001"></a>编译器警告 （等级 4） C4001
使用非标准扩展单行注释  

> [!NOTE] 
> 此警告是在 Visual Studio 2017 版本 15.5 中删除，这是因为单行注释在 C99 标准。
  
 单行注释 + 中是标准 c + + 中 C 开头 C99 标准。 在严格 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，C 文件包含单行注释，因非标准扩展的使用情况而生成 C4001。 由于单行注释都是标准 c + + 中，包含单行注释 C 文件不会生成 C4001 编译具有 Microsoft 扩展 (/Ze) 时。  
  
## <a name="example"></a>示例  
 若要禁用警告，请取消注释[#pragma warning(disable:4001)](../../preprocessor/warning.md)。  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```