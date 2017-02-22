---
title: "初始化 DLL | Microsoft Docs"
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
  - "DLL [C++], 初始化"
  - "初始化 DLL"
  - "终止代码 [C++]"
ms.assetid: f655c5ff-ab5b-493a-a1da-4d1074e60c5b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 初始化 DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DLL 通常具有在 DLL 加载时必须执行的初始化代码（如分配内存）。  使用 Visual C\+\+ 时，在何处添加初始化 DLL 的代码取决于生成的 DLL 类型。  如果不需要添加初始化代码或终止代码，则在生成 DLL 时没有什么特别的事情要做。  如果需要初始化 DLL，则下表描述了应在何处添加代码。  
  
|DLL 类型|添加初始化代码和终止代码的位置|  
|------------|---------------------|  
|规则 DLL|在 DLL 的 `CWinApp` 对象的 `InitInstance` 和 `ExitInstance` 中。|  
|扩展 DLL|在“MFC DLL 向导”生成的 `DllMain` 函数中。|  
|非 MFC DLL|在您提供的称为 `DllMain` 的函数中。|  
  
 在 Win32 中，所有 DLL 都可能包含一个可选入口点函数（通常称为 `DllMain`），初始化和终止时都要调用此函数。  这使您有机会在需要时分配或释放其他资源。  Windows 在四种情况下调用入口点函数：进程附加、进程分离、线程附加和线程分离。  
  
 C 运行库提供了一个名为 **\_DllMainCRTStartup** 的入口点函数，并调用 `DllMain`。  根据 DLL 类型的不同，应在源代码中包含一个名为 `DllMain` 的函数，或应用 MFC 库中提供的 `DllMain`。  
  
## 你希望做什么？  
  
-   [初始化规则 DLL](../build/initializing-regular-dlls.md)  
  
-   [初始化扩展 DLL](../build/initializing-extension-dlls.md)  
  
-   [初始化非 MFC DLL](../build/initializing-non-mfc-dlls.md)  
  
## 您想进一步了解什么？  
  
-   [C 运行库行为和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
-   [\<caps:sentence id\="tgt24" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>DllMain 的函数规范 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt25" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>动态链接库入口点函数 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
## 请参阅  
 [Visual C\+\+ 中的 DLL](../build/dlls-in-visual-cpp.md)