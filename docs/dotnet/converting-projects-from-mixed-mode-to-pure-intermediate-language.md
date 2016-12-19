---
title: "将项目从混合模式转换为纯中间语言项目 | Microsoft Docs"
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
  - "中间语言, 混合模式应用程序"
  - "混合模式应用程序"
  - "混合模式应用程序, 中间语言"
  - "项目 [C++], 转换到中间语言"
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将项目从混合模式转换为纯中间语言项目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，所有 Visual C\+\+ CLR 项目链接到 C 运行库。  由于这些项目联合使用了本机代码和面向公共语言运行时的代码（托管代码），所以它们被划分为混合模式的应用程序。  编译时，它们被编译为中间语言（IL），也称为 Microsoft 中间语言 \(MSIL\)。  
  
### 将混合模式应用程序转换为纯中间语言  
  
1.  移除指向 [C 运行库](../c-runtime-library/crt-library-features.md) \(CRT\) 的链接：  
  
    1.  在定义应用程序入口点的 .cpp 文件中，将入口点更改为 `Main()`。  使用 `Main()` 指示项目不链接到 CRT。  
  
    2.  在解决方案资源管理器中右击项目，选择快捷菜单上的**“属性”**以打开应用程序的属性页。  
  
    3.  在“链接器”的**“高级”**项目属性页中选择“入口点”，然后在此字段中输入 **Main**。  
  
    4.  对于控制台应用程序，在“链接器”的“系统”项目属性页中，选择“子系统”字段，然后将该字段更改为“控制台 \(\/SUBSYSTEM:CONSOLE\)”。  
  
        > [!NOTE]
        >  不必为 Windows 窗体应用程序设置此属性，因为默认情况下，“SubSystem”字段设置为“Windows \(\/SUBSYSTEM:WINDOWS\)”。  
  
    5.  在 stdafx.h 中，注释掉所有 `#include` 语句。  例如，在控制台应用程序中：  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         \- 或 \-  
  
         例如，在 Windows 窗体应用程序中：  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  对于 Windows 窗体应用程序，在 Form1.cpp 中，注释掉引用 windows.h 的 `#include` 语句。  例如：  
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  在 stdafx.h 中，添加下列代码：  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  移除所有非托管类型：  
  
    1.  在适当的情况下，将非托管类型替换为对 [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) 命名空间中结构的引用。  下表列出了常用的托管类型：  
  
        |结构|说明|  
        |--------|--------|  
        |[\<caps:sentence id\="tgt24" sentenceid\="84e2c64f38f78ba3ea5c905ab5a2da27" class\="tgtSentence"\>Boolean\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|表示布尔值。|  
        |[\<caps:sentence id\="tgt26" sentenceid\="40ea57d3ee3c07bf1c102b466e1c3091" class\="tgtSentence"\>Byte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|表示一个 8 位无符号整数。|  
        |[\<caps:sentence id\="tgt28" sentenceid\="a87deb01c5f539e6bda34829c8ef2368" class\="tgtSentence"\>Char\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|表示一个 Unicode 字符。|  
        |[\<caps:sentence id\="tgt30" sentenceid\="dfeaaeb4316477bd556ea5e8c3295887" class\="tgtSentence"\>DateTime\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|表示时间上的一刻，通常以日期和当天的时间表示。|  
        |[\<caps:sentence id\="tgt32" sentenceid\="bdaa3c20a3e3851599514f7c6be5f62f" class\="tgtSentence"\>小数\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|表示十进制数。|  
        |[\<caps:sentence id\="tgt34" sentenceid\="e8cd7da078a86726031ad64f35f5a6c0" class\="tgtSentence"\>Double\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|表示一个双精度浮点数。|  
        |[\<caps:sentence id\="tgt36" sentenceid\="1e0ca5b1252f1f6b1e0ac91be7e7219e" class\="tgtSentence"\>Guid\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|表示全局唯一标识符 \(GUID\)。|  
        |[\<caps:sentence id\="tgt38" sentenceid\="ce80d5ec65b1d2a2f1049eadc100db23" class\="tgtSentence"\>Int16\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|表示 16 位有符号整数。|  
        |[\<caps:sentence id\="tgt40" sentenceid\="0241adbbd83925f051b694d40f02747f" class\="tgtSentence"\>Int32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|表示 32 位有符号整数。|  
        |[\<caps:sentence id\="tgt42" sentenceid\="ff9b3f96d37353c528517bc3656a00a8" class\="tgtSentence"\>Int64\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|表示 64 位有符号整数。|  
        |[\<caps:sentence id\="tgt44" sentenceid\="7f1db863563907cf33604ed7fad6b111" class\="tgtSentence"\>IntPtr\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|用于表示指针或句柄的平台特定类型。|  
        |[\<caps:sentence id\="tgt46" sentenceid\="943756eb7841efcc43b7cd37d7254c76" class\="tgtSentence"\>SByte\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|表示 8 位有符号整数。|  
        |[\<caps:sentence id\="tgt48" sentenceid\="dd5c07036f2975ff4bce568b6511d3bc" class\="tgtSentence"\>Single\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.single.aspx)|表示一个单精度浮点数字。|  
        |[\<caps:sentence id\="tgt50" sentenceid\="90150402997ea9c8dc45cc4d41bb28cb" class\="tgtSentence"\>TimeSpan\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|表示一个时间间隔。|  
        |[\<caps:sentence id\="tgt52" sentenceid\="a00ef2ef85ff67b7b39339886f19044f" class\="tgtSentence"\>UInt16\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|表示 16 位无符号整数。|  
        |[\<caps:sentence id\="tgt54" sentenceid\="3de84ad0700f2a1571f633d399e1900e" class\="tgtSentence"\>UInt32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|表示 32 位无符号整数。|  
        |[\<caps:sentence id\="tgt56" sentenceid\="2e8d31865e5d4b9d8611e1b991baed07" class\="tgtSentence"\>UInt64\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|表示 64 位无符号整数。|  
        |[\<caps:sentence id\="tgt58" sentenceid\="92d74abda31865424016b16e2c806a66" class\="tgtSentence"\>UIntPtr\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|用于表示指针或句柄的平台特定类型。|  
        |[\<caps:sentence id\="tgt60" sentenceid\="cab8111fd0b710a336c898e539090e34" class\="tgtSentence"\>Void\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|指示不返回值的方法；即，该方法的返回类型为 void。|