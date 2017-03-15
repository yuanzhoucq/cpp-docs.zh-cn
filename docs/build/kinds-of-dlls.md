---
title: "DLL 类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DLL [C++], MFC"
  - "DLL [C++], 类型"
  - "MFC DLL [C++], 类型"
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# DLL 类型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题提供有助于确定要生成的 DLL 类型的信息。  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> 可用的不同 DLL 类型  
 使用 Visual C\+\+ 时，可以用 C 或 C\+\+ 生成不使用 Microsoft 基础类 \(MFC\) 库的 Win32 DLL。  可以用“Win32 应用程序向导”创建非 MFC DLL 项目。  
  
 使用“MFC DLL 向导”时，可以在静态链接库或若干 DLL 中使用 MFC 库本身。  如果 DLL 使用的是 MFC，则 Visual C\+\+ 支持三种不同的 DLL 开发方案：  
  
-   生成静态链接 MFC 的规则 DLL  
  
-   生成动态链接 MFC 的规则 DLL  
  
-   生成始终动态链接 MFC 的 MFC 扩展 DLL  
  
### 您想进一步了解什么？  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [扩展 DLL：概述](../build/extension-dlls-overview.md)  
  
-   [要使用的 DLL 类型](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a> 确定要使用的 DLL 类型  
 如果 DLL 不使用 MFC，则使用 Visual C\+\+ 生成非 MFC Win32 DLL。  将 DLL（静态或动态）链接到 MFC 会占用大量磁盘空间和内存。  除非 DLL 确实使用 MFC，否则不要链接到 MFC。  
  
 如果 DLL 要使用 MFC，且将由 MFC 或非 MFC 应用程序使用，则必须生成动态链接到 MFC 的规则 DLL 或静态链接到 MFC 的规则 DLL。  大部分情况下可能需要使用动态链接到 MFC 的规则 DLL，因为这种 DLL 的文件大小要小得多，且使用共享 MFC 版本会节省大量内存。  如果静态链接到 MFC，则由于 DLL 会加载自己的私有 MFC 库代码副本，DLL 的文件大小会较大，且有可能占用额外的内存。  
  
 生成动态链接到 MFC 的 DLL 要比生成静态链接到 MFC 的 DLL 快，因为前者不需链接 MFC 本身。  在链接器必须压缩调试信息的调试版本中尤其如此。  通过与已经包含调试信息的 DLL 链接，DLL 中将只有很少的调试信息需要压缩。  
  
 动态链接到 MFC 的一个缺点是必须用 DLL 发布共享 DLL：Mfcx0.dll 和 Msvcrxx.dll（或类似的文件）。  MFC DLL 可随便重新发布，但仍必须在安装程序中安装 DLL。  另外必须交付 Msvcrxx.dll，它包含程序和 MFC DLL 本身都要使用的 C 运行库。  
  
 如果 DLL 仅由 MFC 可执行文件使用，则可以选择生成规则 DLL 或扩展 DLL。  如果 DLL 实现从现有 MFC 类派生的可重用类，或如果需要在应用程序和 DLL 之间传递 MFC 派生的对象，则必须生成扩展 DLL。  
  
 如果 DLL 动态链接到 MFC，则可能要用 DLL 重新发布 MFC DLL。  当在多个可执行文件之间共享类库以节省磁盘空间和最小化内存使用时，此结构尤其有用。  
  
 在 4.0 版之前，Visual C\+\+ 仅支持两种使用 MFC 的 DLL 类型：USRDLL 和 AFXDLL。  静态链接到 MFC 的规则 DLL 具有与原来的 USRDLL 相同的特性。  MFC 扩展 DLL 具有与原来的 AFXDLL 相同的特性。  
  
### 您想进一步了解什么？  
  
-   [非 MFC DLL：概述](../build/non-mfc-dlls-overview.md)  
  
-   [静态链接到 MFC 的规则 DLL](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [动态链接到 MFC 的规则 DLL](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [扩展 DLL：概述](../build/extension-dlls-overview.md)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)