---
title: "资源编译器错误 RC2104 | Microsoft Docs"
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
  - "RC2104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2104"
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 资源编译器错误 RC2104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未定义的关键字或密钥名称：密钥  
  
 未定义指定的关键字或密钥名称。  
  
 此错误通常是由资源定义或附带的头文件中的拼写错误造成的。  也可能由头文件缺失造成。  
  
 若要解决此问题，请找到应包含已定义关键字或密钥名称的头文件，并验证其是否已包含在资源文件中以及关键字或密钥名称是否拼写正确。  如果你的项目是用预编译头创建的且随后将其删除，请确保该资源文件仍包含所有所需标头。  
  
 若要验证资源文件中的已定义关键字和密钥名称，请在 Visual Studio 中打开“资源视图”窗口，在菜单栏上依次选择“视图”和“资源视图”，然后打开 .rc 文件的快捷菜单，并选择“资源符号”查看已定义符号的列表。  若要修改附带的标头，请打开 .rc 文件的快捷菜单，然后选择“资源包括”。  
  
 如果遇到以下消息：  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 打开 \\MCL\\MFC\\Include\\AfxRes.h 并添加此 Include 指令：  
  
```  
#include <winresrc.h>  
```