---
title: "错误 C1510 |Microsoft 文档"
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d4128580facdc87239d0087fef1cf9eff701854
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1510"></a>错误 C1510
无法打开语言资源 clui.dll  
  
 编译器无法加载语言资源 DLL。  
  
没有针对此问题的两个常见原因。 使用 32 位编译器和工具时，可能会看到此错误适用于在链接过程中使用的内存超过 2 GB 的大型项目。 在 64 位 Windows 系统上可能的解决方法是使用 64 位本机或跨编译器和工具来生成你的代码。 这可利用的更大的内存空间提供给 64 位应用程序。 如果因为在 32 位系统上运行，必须使用 32 位编译器，在某些情况下，可以增加到链接器为 3 GB 的可用内存量。 有关详细信息，请参阅[4 千兆字节优化： BCDEdit 和 Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx)和[BCDEdit 设置increaseuserva/](https://msdn.microsoft.com/library/ff542202.aspx)命令。  

其他常见的原因是 Visual Studio 安装损坏或不完整。 在这种情况下，运行安装程序以修复或重新安装 Visual Studio。  
  