---
title: "cl.exe 的返回值 | Microsoft Docs"
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
  - "cl.exe 编译器, 返回值"
ms.assetid: 7c2d7f33-ee0d-4199-8ef4-75fe2b007670
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cl.exe 的返回值
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

cl.exe 在成功（无错误）时返回零；否则返回非零值。  
  
 如果从脚本、powershell、.cmd 或 .bat 文件编译，则 cl.exe 的返回值很有用。  建议在出现错误或警告时捕获编译器的输出，以便能解决它们。  
  
 有太多可能的错误退出代码，cl.exe 无法将它们一一列出。  可以在 winerror.h 或 ntstatus.h 文件（包含在 %ProgramFiles\(x86\)%\\Windows Kits\\`version`\\Include\\shared\\ directory 中的 Windows 软件开发工具包中）中查找错误代码。  以十进制返回的错误代码必须转换为十六进制才能搜索。  例如，错误代码 \-1073741620 转换为十六进制为 0xC00000CC。  在 ntstatus.h 中发现了此错误，对应的消息为“无法在远程服务器上找到指定共享名。”有关 Windows 错误代码的可下载列表，请参阅 [&#91;MS\-ERREF&#93;: Windows Error Codes](http://msdn.microsoft.com/zh-cn/1bc92ddf-b79e-413c-bbaa-99a5281a6c90)。  
  
 还可使用 Visual Studio 中的错误查找实用工具来了解编译器错误消息的意思。  在 Visual Studio 命令外壳中，输入 **errlook.exe** 启动此实用工具；或者在 Visual Studio IDE 中的菜单栏上，选择**“工具”**、**“错误查找”**。  输入错误值以查找与错误相关的描述性文本。  有关更多信息，请参见[ERRLOOK 参考](../../build/reference/errlook-reference.md)。  
  
## 备注  
 下面是一个使用 cl.exe 的返回值的示例 .bat 文件。  
  
```  
echo off  
cl /W4 t.cpp  
@if ERRORLEVEL == 0 (  
   goto good  
)  
  
@if ERRORLEVEL != 0 (  
   goto bad  
)  
  
:good  
   echo "clean compile"  
   echo %ERRORLEVEL%  
   goto end  
  
:bad  
   echo "error or warning"  
   echo %ERRORLEVEL%  
   goto end  
  
:end  
```  
  
## 请参阅  
 [编译器命令行语法](../../build/reference/compiler-command-line-syntax.md)