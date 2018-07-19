---
title: 编译器警告 （等级 1） C4727 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c92e42fe275f821e333a0f04a116034a5bb849a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282777"
---
# <a name="compiler-warning-level-1-c4727"></a>编译器警告（等级 1）C4727
"PCH 相同的时间戳 obj_file_1 和 obj_file_2 中找到的名为 pch_file。  使用第一个 PCH。  
  
 编译与多个编译单位时发生 C4727 **/Yc**，和编译器已可以将标记所有具有相同的.pch 时间戳的.obj 文件。  
  
 若要解决，编译一个源文件 **/Yc /c** （创建 pch） 和其他使用单独编译 **/Yu /c** （使用 pch），然后将它们链接在一起。  
  
 因此，如果未以下并生成 C4727:  
  
 **cl /clr /GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 你将执行以下操作改为：  
  
 **cl /clr /GL a.cpp /Ycstdafx.h /c**  
  
 **cl /clr /GL b.cpp c.cpp /Yustdafx.h /link a.obj**  
  
 有关详细信息，请参见  
  
-   [/Yc（创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu（使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)