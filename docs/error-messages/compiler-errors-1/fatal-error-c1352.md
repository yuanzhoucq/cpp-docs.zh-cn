---
title: 错误 C1352 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1352
dev_langs:
- C++
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 524b0bf5d25953c5c38cbe0e23dc5c7d9f3cb7be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1352"></a>错误 C1352
函数“function”(模块“file”中)的 MSIL 无效或已损坏  
  
 向编译器传递了一个 .netmodule 文件，但编译器检测出该文件已损坏。  向生成该 .netmodule 文件的人员询问有关情况。  
  
 编译器并不检查 .netmodule 文件中所有类型的损坏。  但它检查函数中的所有控制路径是否包含返回语句。  
  
 有关详细信息，请参阅 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。