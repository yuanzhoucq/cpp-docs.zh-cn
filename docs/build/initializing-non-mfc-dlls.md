---
title: "初始化非 MFC DLL | Microsoft Docs"
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
  - "DLL [C++], 非 MFC"
  - "初始化 DLL"
  - "非 MFC DLL [C++]"
ms.assetid: 2622b32a-28f9-4d61-9e46-6c19aaf8b7ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 初始化非 MFC DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为初始化非 MFC DLL，DLL 源代码必须包含一个名为 `DllMain` 的函数。  下列代码显示了一个基本主干，说明 `DllMain` 定义的大概样子：  
  
```  
BOOL APIENTRY DllMain(HANDLE hModule,   
                      DWORD  ul_reason_for_call,   
                      LPVOID lpReserved)  
{  
    switch( ul_reason_for_call ) {  
    case DLL_PROCESS_ATTACH:  
    ...  
    case DLL_THREAD_ATTACH:  
    ...  
    case DLL_THREAD_DETACH:  
    ...  
    case DLL_PROCESS_DETACH:  
    ...  
    }  
    return TRUE;  
}  
```  
  
> [!NOTE]
>  **DllEntryPoint** 的 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 文档指出，必须在链接器命令行上用 \/ENTRY 选项指定入口点函数的实际名称。  使用 Visual C\+\+ 时，如果入口点函数的名称为 `DllMain`，则无需使用 \/ENTRY 选项。  实际上，如果使用了 \/ENTRY 选项，但没有将入口点函数命名为 `DllMain`，则 C 运行库将不会正确初始化。  
  
## 您想进一步了解什么？  
  
-   [\<caps:sentence id\="tgt7" sentenceid\="58bb7328659bda9ffb73a1dcd39da06b" class\="tgtSentence"\>DllMain 的函数规范 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682583)  
  
-   [\<caps:sentence id\="tgt8" sentenceid\="f29344705c59343b34b642944921cbdf" class\="tgtSentence"\>动态链接库入口点函数 \(Windows SDK\)\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms682596)  
  
-   [C 运行库行为和 \_DllMainCRTStartup](../build/run-time-library-behavior.md)  
  
## 请参阅  
 [初始化 DLL](../build/initializing-a-dll.md)