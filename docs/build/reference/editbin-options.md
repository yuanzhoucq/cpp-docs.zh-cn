---
title: "EDITBIN 选项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "editbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EDITBIN 程序, 选项"
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# EDITBIN 选项
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使用 EDITBIN 修改对象文件、可执行文件和动态链接库 \(DLLs\)。  选项指定 EDITBIN 做的更改。  
  
 选项由选项说明符（短划线 \(–\) 或正斜杠 \(\/\)）后跟选项的名称组成。  选项名不能缩写。  某些选项带参数，参数在冒号 \(:\) 后指定。  在选项规范内不允许有空格或制表符。  使用一个或多个空格或制表符来分隔命令行中的选项规范。  选项名及其关键字参数或文件名参数不区分大小写。  例如， \- bind和\/BIND意义完全相同。  
  
 EDITBIN 具有下列选项：  
  
|选项|用途|  
|--------|--------|  
|[\/ALLOWBIND](../../build/reference/allowbind.md)|指定一个DLL是否可以绑定 。|  
|[\/ALLOWISOLATION](../../build/reference/allowisolation.md)|指定 DLL 或可执行文件标记查找行为。|  
|[\/APPCONTAINER](../../build/reference/appcontainer.md)|指定应用程序是否必须在 appcontainer 进程环境中运行——例如，一个[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用程序。|  
|[\/BIND](../../build/reference/bind.md)|将指定的对象的入口点地址设为速度加载时间。|  
|[\/DYNAMICBASE](../../build/reference/dynamicbase.md)|使用地址空间布局随机化 \(ASLR\) 功能，指定是否可在加载时随机重新设定DLL或可执行图像的基址。|  
|[\/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|向 Microsoft 报告内部错误。|  
|[\/HEAP](../../build/reference/heap.md)|以字节设置可执行图像中堆的大小。|  
|[\/HIGHENTROPYVA](../../build/reference/highentropyva.md)|指定 DLL或可执行图像是否支持高熵 64 位地址空间布局随机化 \(ASLR\)。|  
|[\/INTEGRITYCHECK](../../build/reference/integritycheck.md)|指定是否检查数字签名在加载时。|  
|[\/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|指定对象是否支持比大于2 GB 的地址。|  
|[\/NOLOGO](../../build/reference/nologo-editbin.md)|取消显示EDITBIN启动横幅。|  
|[\/NXCOMPAT](../../build/reference/nxcompat.md)|指定可执行映像是否使用 Windows 数据执行保护兼容。|  
|[\/REBASE](../../build/reference/rebase.md)|设置指定的基址。|  
|[\/RELEASE](../../build/reference/release.md)|在 头中设置校验和。|  
|[\/SECTION](../../build/reference/section-editbin.md)|重写节的特性。|  
|[\/STACK](../../build/reference/stack.md)|以字节设置可执行图像中栈的大小。|  
|[\/SUBSYSTEM](../../build/reference/subsystem.md)|指定执行环境。|  
|[\/SWAPRUN](../../build/reference/swaprun.md)|指定必须复制可执行文件图像到交换文件，然后从其中运行。|  
|[\/TSAWARE](../../build/reference/tsaware.md)|指定应用设计在多用户环境运行。|  
|[\/VERSION](../../build/reference/version.md)|在标头设置版本号。|  
  
## 请参阅  
 [C\/C\+\+ 生成工具](../../build/reference/c-cpp-build-tools.md)   
 [EDITBIN 参考](../../build/reference/editbin-reference.md)