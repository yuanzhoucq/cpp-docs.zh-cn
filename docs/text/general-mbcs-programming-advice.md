---
title: "常规 MBCS 编程建议 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "对话框 [C++], 字体"
  - "MBCS [C++], 对话框字体"
  - "MBCS [C++], 编程"
  - "MS Shell Dlg"
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# 常规 MBCS 编程建议
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用下列提示：  
  
-   为获得灵活性，尽可能地使用运行时宏（如 `_tcschr` 和 `_tcscpy`）。  有关更多信息，请参见 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
-   使用 C 运行时 `_getmbcp` 函数获取有关当前代码页的信息。  
  
-   不要重复使用字符串资源。  根据目标语言，给定的字符串翻译后可能具有不同的含义。  例如，应用程序主菜单上的“文件”与对话框中的“文件”字符串翻译后的含义可能不同。  如果需要使用同名的几个字符串，则对每个字符串使用不同的字符串 ID。  
  
-   您可能想知道应用程序是否正在一个支持 MBCS 的操作系统上运行。  若要这样做，请在程序启动时设置标志；而不要依赖 API 调用。  
  
-   设计对话框时，在静态文本控件结尾处留出约 30% 的额外空间用于 MBCS 翻译。  
  
-   为应用程序选择字体时要小心，因为有些字体并非适用于所有系统。  例如，Windows 2000 的日文版不支持 Helvetica 字体。  
  
-   为对话框选择字体时，请使用[宋体](http://msdn.microsoft.com/library/windows/desktop/dd374112)而不是 MS Sans Serif 或 Helvetica。  在创建对话框之前，系统将用正确的字体替换 MS Shell Dlg。  使用 MS Shell Dlg 确保将自动获得操作系统中为处理此字体而进行的任何更改。（MFC 用 DEFAULT\_GUI\_FONT 或 Windows 95、Windows 98 和 Windows NT 4 上的系统字体来替换 MS Shell Dlg，原因是这些系统不能正确处理 MS Shell Dlg。）  
  
-   设计应用程序时，确定哪些字符串可以本地化。  如果存在疑问，则假定任何给定的字符串都可以本地化。  在这种情况下，不要混合使用可以本地化的字符串和不能本地化的字符串。  
  
## 请参阅  
 [MBCS 编程提示](../text/mbcs-programming-tips.md)   
 [递增和递减指针](../text/incrementing-and-decrementing-pointers.md)