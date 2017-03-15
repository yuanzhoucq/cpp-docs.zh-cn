---
title: "如何：创建可验证的 C++ 项目 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "转换, C++ 项目"
  - "可验证程序集 [C++], 创建"
  - "Visual C++ 项目"
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：创建可验证的 C++ 项目 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 应用程序向导不创建可验证的项目，但项目可以转换为可验证的。  本主题介绍如何设置项目属性和修改项目源文件来转换 Visual C\+\+ 项目，以生成可验证的应用程序。  
  
## 编译器和链接器设置  
 默认情况下，.NET 项目使用 \/clr 编译器标志并将链接器配置为用于 x86 硬件。  对于可验证的代码，必须使用 \/clr:safe 标志，并且必须指示链接器生成 MSIL，而不是本机机器指令。  
  
#### 更改编译器和链接器设置  
  
1.  显示项目属性页。  有关详细信息，请参阅[如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)。  
  
2.  在**“配置属性”**节点下的**“常规”**页上，将**“公共语言运行时支持”**属性设置为**“安全 MSIL 公共语言运行时支持 \(\/clr:safe\)”**。  
  
3.  在**“链接器”**节点下的**“高级”**页上，将**“CLR 映像类型”**属性设置为**“强制安全 IL 映像 \(\/CLRIMAGETYPE:SAFE\)”**。  
  
## 移除本机数据类型  
 由于本机数据类型是不可验证的，因此，即使实际上并没有使用，也必须移除所有包含本机数据类型的头文件。  
  
> [!NOTE]
>  下面的过程适用于 Windows 窗体应用程序 \(.NET\) 项目和控制台应用程序 \(.NET\) 项目。  
  
#### 移除对本机数据类型的引用  
  
1.  注释掉 Stdafx.h 文件中的所有内容。  
  
## 配置入口点  
 由于可验证的应用程序无法使用 C 运行库 \(CRT\)，因此无法依赖 CRT 来调用主函数作为标准入口点。  这意味着必须显式地向链接器提供最开始要调用的函数的名称。（这种情况下，使用 Main\(\) 而不是 main\(\) 或 \_tmain\(\) 来指示非 CRT 入口点，但由于入口点必须显式指定，因此，可为任意名称。）  
  
> [!NOTE]
>  下面的过程适用于控制台应用程序 \(.NET\) 项目。  
  
#### 配置入口点  
  
1.  在项目的 main .cpp 文件中将 \_tmain\(\) 更改为 Main\(\)。  
  
2.  显示项目属性页。  有关详细信息，请参阅[如何：打开项目属性页](../misc/how-to-open-project-property-pages.md)。  
  
3.  在**“链接器”**节点下的**“高级”**页上，输入 `Main` 作为**“入口点”**属性值。  
  
## 请参阅  
 [纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)