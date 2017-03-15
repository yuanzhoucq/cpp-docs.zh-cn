---
title: "/ORDER（按顺序放置函数） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.FunctionOrder"
  - "/order"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ORDER 链接器选项"
  - "LINK 工具 [C++], 程序优化"
  - "LINK 工具 [C++], 交换优化"
  - "ORDER 链接器选项"
  - "-ORDER 链接器选项"
  - "分页, 优化"
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /ORDER（按顺序放置函数）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ORDER:@filename  
```  
  
## 参数  
 *filename*  
 指定 COMDAT 函数链接顺序的文本文件。  
  
## 备注  
 \/ORDER 选项告知 LINK 通过按预设的顺序将特定的 COMDAT 放置到映像中来优化程序。  LINK 按指定的顺序将函数放置到映像中的每一节内。  
  
 在 *filename* 中指定顺序，这是按照您希望链接 COMDAT 的顺序列出 COMDAT 的文本文件（响应文件）。  *filename* 中的每一行包含一个 COMDAT 的名称。  如果对象已经用 \/Gy 选项编译过，它包含 COMDAT。  函数名区分大小写。  
  
 LINK 使用标识符的修饰形式。  编译器在创建 .obj 文件时修饰标识符。  当需要将标识符的修饰形式指定给链接器时，可使用 [DUMPBIN](../../build/reference/dumpbin-reference.md) 工具获取它。  有关修饰名的更多信息，请参见[修饰名](../../build/reference/decorated-names.md)。  
  
 如果使用了多个 \/ORDER 规范，指定的最后一个规范有效。  
  
 排序允许将一个函数与该函数调用的函数组合，通过交换优化来优化程序的分页行为。  还可将经常调用的函数分在一组。  这些技术增加了调用的函数在需要它时位于内存中从而不必从磁盘分页的可能性。  
  
 链接器在 *filename* 中的每个修饰名前放置一个下划线 \(\_\)，只要名称不是以问号 \(?\) 或 at 符 \(@\) 开头。  例如，如果对象文件包含 `extern "C" int func(int)` 和 `int main(void)`，则 DUMPBIN [\/SYMBOLS](../../build/reference/symbols.md) 将列出这些修饰名：  
  
```  
009 00000000 SECT3  notype ()    External     | _func  
00A 00000008 SECT3  notype ()    External     | _main  
```  
  
 不过，在顺序文件中指定的名称应为 `func` 和 `main`。  
  
 \/ORDER 选项禁用增量链接。  
  
> [!NOTE]
>  LINK 无法对静态函数进行排序，因为静态函数名不是公共符号名。  如果指定了 \/ORDER，在顺序文件中将为每个静态的或者没有找到的符号生成链接器警告 LNK4037。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“优化”属性页。  
  
4.  修改“函数顺序”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)