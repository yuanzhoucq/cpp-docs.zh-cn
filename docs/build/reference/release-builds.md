---
title: 发行版本 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ae18c5e2dcdb735880509fd158dac4ccaa1462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="release-builds"></a>发行版本
发布版本使用优化。 当使用优化以创建发行版本时，编译器不会生成符号化调试信息。 符号化调试信息，以及不的跟踪和断言生成代码的事实没有调用，表示可执行文件的大小会减少，因此将更快。  
  
 本部分提供有关原因和时间你想要将从调试版本更改为发布版本信息。 它还介绍了一些从调试版本更改为发布版本时可能遇到的问题：  
  
-   [创建发布版本](../../build/reference/how-to-create-a-release-build.md)  
  
-   [创建发行版本时遇到的常见问题](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)  
  
    -   [检查 ASSERT 语句](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [使用调试版本检查内存改写](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [调试的发布版本](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [检查内存改写](../../build/reference/checking-for-memory-overwrites.md)  
  
## <a name="see-also"></a>请参阅  
 [生成 Visual Studio 中的 c + + 项目](../../ide/building-cpp-projects-in-visual-studio.md)   
 [C/C++ 生成参考](../../build/reference/c-cpp-building-reference.md)