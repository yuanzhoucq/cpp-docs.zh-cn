---
title: "错误 C1189 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1189"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1189"
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1189
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#error : 用户提供的错误信息  
  
 C1189 由 `#error` 指令生成。  编写指令代码的开发人员指定错误消息的文本。  有关详细信息，请参阅[\#error 指令](../../preprocessor/hash-error-directive-c-cpp.md)。  
  
 下面的示例生成 C1189。  在示例中，由于未定义 `_WIN32` 标识符，因此开发人员发出自定义错误消息：  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 如果使用 **\/robust** MIDL 编译器选项生成 ATL 项目，也有可能看到此错误。  使用 **\/robust** 开关可仅生成 [!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)] 和 Windows 更高版本。  请执行以下步骤以更正此错误。  
  
-   将 dlldatax.c 文件中的此行：  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 更改为：  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   使用**“MIDL”**属性页文件夹中的**“高级”**属性页移除 **\/robust** 开关，然后指定 **\/no\_robust** 开关。  有关详细信息，请参阅[MIDL 属性页：高级](../../ide/midl-property-pages-advanced.md)。  
  
## 请参阅  
 [\#define 指令](../../preprocessor/hash-define-directive-c-cpp.md)