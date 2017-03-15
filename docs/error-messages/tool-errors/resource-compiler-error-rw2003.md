---
title: "资源编译器错误 RW2003 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW2003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW2003"
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 资源编译器错误 RW2003
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成错误  
  
### 通过检查以下可能的原因进行修复  
  
1.  **错误：位图文件的资源文件不是 3.00 格式**  
  
     使用 Windows 2.x 版格式的位图不能用于 3.x 版的资源文件。  该位图文件必须重绘或转换为 3.x 格式。  
  
2.  **错误: 资源名称中含有旧的 DIB。  通过 SDKPAINT 传递它**  
  
     指定资源中的与设备无关的位图 \(DIB\) 与 Windows 3.0 格式不兼容。  该位图必须重绘或转换为 3.x 格式。  
  
3.  **错误：资源文件的资源名称不是 3.00 格式**  
  
     指定资源中的图标或游标使用 Windows 早期版本的格式。  该图标或游标必须重绘或转换为 3.x 格式。  
  
4.  **未知的 DIB 标头格式**  
  
     该位图头不是 BITMAPCOREHEADER 或 BITMAPINFOHEADER 结构。  
  
5.  **无法初始化符号信息**  
  
     该错误只发生在 Visual C\+\+ 中。  可能的原因是，打开的文件太多或者无法打开或写入 Visual C\+\+ 向脚本导入符号所需的数据文件。  Visual C\+\+ 尝试在 **TMP** 环境变量所指定的目录（如果没有指定则在当前目录）中创建这些文件。  
  
6.  **无法保存符号信息**  
  
     该错误只发生在 Visual C\+\+ 中。  可能的原因是，打开的文件太多或者无法关闭或写入 Visual C\+\+ 向脚本导入符号所需的数据文件。  Visual C\+\+ 尝试在 **TMP** 环境变量所指定的目录（如果没有指定则在当前目录）中使用这些文件。  
  
7.  **位图文件的资源文件不是 2.03 格式**  
  
     该位图使用了早于 2.03 版的格式。  必须使用 3.00 版或更高版本的格式转换或重绘该位图。  
  
8.  **资源太大**  
  
     对于 Windows 3.1，资源不能超过大约 65000 个字节。  如果资源超过 65000 个字节，您将无法用 Visual C\+\+ 或命令行资源编译器编译该资源。  该限制不适用于游标、图标、位图或其他基于文件的资源。  
  
9. **资源文件的格式并非 3.00 格式**  
  
     游标或图标使用早于 3.00 版本的格式。  必须使用 3.00 版或更高版本的格式转换或重绘该资源。  
  
10. **无法打开临时文件**  
  
     资源编译器\/Visual C\+\+ 无法打开临时文件。  可能的原因是您没有该目录的写权限或该目录不存在。  资源编译器\/Visual C\+\+ 尝试在 **TMP** 环境变量指定的目录（或者如果没有指定则在当前目录）中使用这些文件。