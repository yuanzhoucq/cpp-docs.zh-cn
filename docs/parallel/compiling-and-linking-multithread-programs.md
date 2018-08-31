---
title: 编译和链接多线程程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ab667e372c8118a83b7a93444abbfbc5c19b6e0
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131513"
---
# <a name="compiling-and-linking-multithread-programs"></a>编译和链接多线程程序
Bounce.c 程序在中引入[多线程 C 程序示例](sample-multithread-c-program.md)。  
  
编译的程序默认情况下多线程。  
  
### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>若要编译和链接的开发环境中的多线程程序从 Bounce.c  
  
1.  在 **“文件”** 菜单上，单击 **“新建”**，然后单击 **“项目”**。  
  
2.  在中**项目类型**窗格中，单击**Win32**。  
  
3.  在中**模板**窗格中，单击**Win32 控制台应用程序**，然后命名项目。  
  
4.  添加包含项目的 C 源代码的文件。  
  
5.  上**构建**菜单中，通过单击生成项目**生成**命令。  
  
### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>若要编译和链接多线程程序 Bounce.c 从命令行  
  
1.  编译和链接程序：  
  
    ```  
    CL BOUNCE.C  
    ```  
  
## <a name="see-also"></a>请参阅

[使用 C 和 Win32 进行多线程编程](multithreading-with-c-and-win32.md)