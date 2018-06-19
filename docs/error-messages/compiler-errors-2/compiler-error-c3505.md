---
title: 编译器错误 C3505 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3505
dev_langs:
- C++
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0ea8edd3237db2085365450f43b4b955d36f33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257651"
---
# <a name="compiler-error-c3505"></a>编译器错误 C3505

> 无法加载类型库*guid*  
  
如果你正在运行 32 位、 x86 承载交叉编译器 64 位的则可能导致 C3505，x64 目标在 64 位计算机，因为编译器在 WOW64 下运行，并且只能读取 32 位注册表配置单元。  
  
你可以通过构建你尝试导入，类型库的 32 位和 64 位版本中解决此错误，然后注册这两个。  或者可以使用本机 64 位编译器，要求你将更改你**VC + + 目录**IDE 以指向的 64 位编译器中的属性。  
  
有关详细信息，请参阅  
  
-   [如何：在命令行上启用 64 位 Visual C++ 工具集](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [如何：针对 64 位 x64 平台配置 Visual C++ 项目](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)