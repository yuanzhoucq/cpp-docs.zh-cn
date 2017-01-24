---
title: "组件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.component"
  - "component_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "组件杂注"
  - "杂注, 组件"
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制对源文件中的浏览信息或依赖项信息的收集。  
  
## 语法  
  
```  
  
      #pragma component( browser, { on | off }[, references [, name ]] )  
#pragma component( minrebuild, on | off )  
#pragma component( mintypeinfo, on | off )  
```  
  
## 备注  
  
## 浏览器  
 您可以打开或关闭收集，也可以指定在收集信息时忽略特定名称。  
  
 使用打开或关闭来控制对之前的杂注中的浏览信息的收集。  例如：  
  
```  
#pragma component(browser, off)  
```  
  
 停止编译器收集浏览信息。  
  
> [!NOTE]
>  若要打开对带此杂注的浏览信息的收集，则[必须先启用浏览信息](../build/reference/building-browse-information-files-overview.md)。  
  
 可以在有或没有 *name* 参数的情况下使用 **references** 选项。  在不带 *name* 的情况下使用 **references** 来打开或关闭对引用的收集（但会继续收集其他浏览信息）。  例如：  
  
```  
#pragma component(browser, off, references)  
```  
  
 停止编译器收集引用信息。  
  
 在带 *name* 和 **off** 的情况下使用 **references** 将阻止对 *name* 的引用显示在浏览信息窗口中。  使用此语法可忽略您不感兴趣的名称和类型，并减小浏览信息文件的大小。  例如：  
  
```  
#pragma component(browser, off, references, DWORD)  
```  
  
 此时忽略对 **DWORD** 的引用。  您可以通过使用 **on** 重新启用对 `DWORD` 的引用的收集：  
  
```  
#pragma component(browser, on, references, DWORD)  
```  
  
 这是恢复对 *name* 的引用的收集的唯一方式；您必须显式打开已关闭的任何 *name*。  
  
 若要防止预处理器扩展 *name*（如将 **NULL** 扩展到 **0**），请用引号将其引起来：  
  
```  
#pragma component(browser, off, references, "NULL")  
```  
  
## 最小重新生成  
 Visual C\+\+ 最小重新生成功能要求编译器创建并存储将占用磁盘空间的 C\+\+ 类依赖项信息。  若要节省磁盘空间，可以在不需要收集依赖项信息时使用  `#pragma component( minrebuild, off )` （例如，在不变的头文件中）。  在不变的类的后面插入  `#pragma component(minrebuild, on)` 可重新启用依赖项收集。  
  
## 减少类型信息  
 **mintypeinfo** 选项将减少指定区域的调试信息。  此信息的量相当大，会影响 .pdb 和 .obj 文件。  您不能在 mintypeinfo 区域中调试类和结构。  使用 mintypeinfo 选项可帮助避免以下警告：  
  
```  
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information  
```  
  
 有关详细信息，请参阅[启用最小重新生成](../build/reference/gm-enable-minimal-rebuild.md) \(\/Gm\) 编译器选项。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)