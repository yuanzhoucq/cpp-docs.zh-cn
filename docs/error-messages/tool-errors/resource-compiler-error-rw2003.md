---
title: "资源编译器错误 RW2003 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f388ca21d95e7d675a6b9890a7368765b5c0d7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rw2003"></a>资源编译器错误 RW2003
生成错误  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  **错误： 位图文件的资源文件不是 3.00 格式**  
  
     使用的 Windows 版本 2.x 格式的位图不能用于版本 3.x 资源文件。 必须在重绘该位图，或转换为 3.x 格式。  
  
2.  **错误： 中存在旧 DIB 资源名称。通过 SDKPAINT 传递它**  
  
     设备独立位图 (DIB) 中指定的资源不与 Windows 3.0 格式兼容。 必须在重绘该位图，或转换为 3.x 格式。  
  
3.  **错误： 资源文件的资源名称不是 3.00 格式**  
  
     图标或光标在指定资源使用从以前版本的 Windows 的格式。 图标或光标必须在重绘或转换为 3.x 格式。  
  
4.  **未知的 DIB 标头格式**  
  
     位图标头不是 BITMAPCOREHEADER 或 BITMAPINFOHEADER 结构。  
  
5.  **无法初始化符号信息**  
  
     仅在 Visual c + + 中出现此错误。 可能的原因是已打开的文件太多，或无法打开或写入所需的 Visual c + + 导入你的脚本中的符号的数据文件。 Visual c + + 尝试在指定的目录中创建这些文件**TMP**环境变量，或者如果未指定的当前目录。  
  
6.  **无法保存符号信息**  
  
     仅在 Visual c + + 中出现此错误。 可能的原因是必须打开的文件太多，或者你不能关闭或写入所需的 Visual c + + 导入你的脚本中的符号的数据文件。 Visual c + + 尝试使用这些文件中指定的目录**TMP**环境变量，或者如果未指定的当前目录。  
  
7.  **位图文件的资源文件不是 2.03 格式**  
  
     位图使用了早于 2.03 版的格式。 必须使用 3.00 版或更高版本的格式转换或重绘该位图。  
  
8.  **资源太大**  
  
     对于 Windows 3.1 资源不能超过大约 65000 个字节。 如果你的资源，然后你将不能使用 Visual c + + 或命令行资源编译器来编译。 该限制不适用于游标、图标、位图或其他基于文件的资源。  
  
9. **资源文件不是 3.00 格式**  
  
     光标或图标使用早于版本 3.00 格式。 资源必须是转换后或重绘使用格式 3.00 版或更高版本。  
  
10. **无法打开临时文件**  
  
     资源编译器/Visual C++ 无法打开临时文件。 可能的原因是没有目录的写权限或目录不存在。 资源编译器/Visual C++ 尝试在 **TMP** 环境变量指定的目录或当前目录（如果未指定任何目录）中使用这些文件。