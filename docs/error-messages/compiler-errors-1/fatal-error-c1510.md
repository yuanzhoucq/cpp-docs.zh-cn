---
title: 错误 C1510 |Microsoft Docs
ms.custom: ''
ms.date: 04/11/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25b1c3f83b770dc7b346e83e9675afe423af2516
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42543113"
---
# <a name="fatal-error-c1510"></a>错误 C1510
无法打开语言资源 clui.dll  
  
 编译器无法加载语言资源 DLL。  
  
有两个此问题的常见原因。 使用 32 位编译器和工具时，可能会看到此错误，以便在链接过程中使用的内存超过 2 GB 的大型项目。 在 64 位 Windows 系统上可能的解决方案是使用 64 位本机或跨编译器和工具，用于生成你的代码。 这充分利用较大的内存空间可用于 64 位应用程序。 如果因为在 32 位系统上运行，必须使用 32 位编译器，可以在某些情况下增加到链接器 3 gb 可用内存量。 有关详细信息，请参阅[4gb 的优化： BCDEdit 和 Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473\(v=vs.85\).aspx)并[BCDEdit /set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx)命令。  

其他常见原因是已损坏的或不完整的 Visual Studio 安装。 在这种情况下，运行安装程序以修复或重新安装 Visual Studio。  
  