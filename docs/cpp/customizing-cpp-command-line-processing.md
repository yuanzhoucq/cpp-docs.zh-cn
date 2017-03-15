---
title: "自定义 C++ 命令行处理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_setenvp"
  - "_setargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setargv 函数"
  - "_setenvp 函数"
  - "命令行, 处理"
  - "命令行, 处理参数"
  - "命令行处理"
  - "环境, 环境处理例程"
  - "启动代码, 自定义命令行处理"
  - "禁止显示环境处理"
ms.assetid: aae01cbb-892b-48b8-8e1f-34f22421f263
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自定义 C++ 命令行处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 如果程序不采用命令行参数，则可以通过取消使用执行命令行处理的库例程来节省少量空间。  此例程称为 **\_setargv**，[通配符扩展](../cpp/wildcard-expansion.md)中对其进行了描述。  若要取消对其的使用，请定义在包含**main** 函数的文件中不执行任何操作的例程并将其命名为 **\_setargv**。  然后，通过 **\_setargv** 的定义满足对 **\_setargv** 的调用，并且不加载库版本。  
  
 同样，如果您从不通过 `envp` 参数访问环境表，则可以提供用于代替 **\_setenvp**（环境处理例程）的您自己的空白例程。  正如使用 **\_setargv** 函数一样，**\_setenvp** 必须声明为 **extern "C"**。  
  
 您的程序可以调用 C 运行库中的 **spawn** 或 `exec` 系列例程。  如果是这样，则不应取消环境处理例程，因为可使用此例程将环境从父进程传递到子进程中。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [main：程序启动](../cpp/main-program-startup.md)