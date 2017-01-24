---
title: "/BASE（基址） | Microsoft Docs"
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
  - "/base"
  - "VC.Project.VCLinkerTool.BaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/BASE 链接器选项"
  - "@ 符号表示基址"
  - "根据基址的符号"
  - "基址 [C++]"
  - "BASE 链接器选项"
  - "-BASE 链接器选项"
  - "DLL [C++], 链接"
  - "环境变量 [C++], LIB"
  - "可执行文件 [C++], 基址"
  - "键地址大小"
  - "LIB 环境变量"
  - "程序 [C++], 基址"
  - "程序 [C++], 禁止重定位"
  - "分号 [C++], 说明符"
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
caps.latest.revision: 15
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /BASE（基址）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/BASE:{address[,size] | @filename,key}  
```  
  
 \/BASE 选项设置程序的基址，重写 .exe 文件（在 0x400000 处）或 DLL（在 0x10000000 处）的默认位置。  操作系统首先尝试在程序的指定或默认基址加载程序。  如果该基址处没有足够的空间可用，则系统将重定位程序。  若要防止重定位，请使用 [\/FIXED](../../build/reference/fixed-fixed-base-address.md) 选项。  
  
 如果 *address* 不是 64K 的倍数，链接器将发出错误。您可以选择指定程序的大小，以便链接器在程序超过您指定的大小时发出警告。  
  
 在命令行上，另一种指定基址的方法是在文件中使用前面有 at 符 \(@\) 的 *filename* 以及 `key`。  *文件名* 是包含程序将使用的所有 DLL 的位置和大小的文本文件。  链接器在指定的路径中查找*文件名*，如果没有指定路径，则在 LIB 环境变量中指定的目录中查找。  *文件名* 中的每一行表示一个 DLL 并具有以下语法：  
  
```  
  
key address [size] ;comment  
```  
  
 `key` 是字母数字字符串，不区分大小写。  它通常是 DLL 的名称，但不必非是。  `key` 后跟 C 语言、十六进制或十进制表示法的基址和可选的最大 `size`。  所有三个参数由空格或制表符分隔。  如果指定的 `size` 小于程序所要求的虚拟地址空间，则链接器发出警告。  `comment` 由分号 \(;\) 指定，可以在同一行上，也可以在单独的行上。  链接器忽略从分号到行尾的所有文本。  下面的示例显示这种文件的一部分：  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 如果包含这些行的文件名为 DLLS.txt，则下面的示例命令应用此信息：  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## 备注  
 通过分配基址以使 DLL 在地址空间中不重叠，可以减少分页并提高程序性能。  
  
 设置基址的另一种方法是在 [NAME](../../build/reference/name-c-cpp.md) 或 [LIBRARY](../../build/reference/library.md) 语句中使用 *BASE* 参数。  将 \/BASE 和 [\/DLL](../../build/reference/dll-build-a-dll.md) 选项连用等效于 **LIBRARY** 语句。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“高级”**属性页。  
  
4.  修改“基址”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)