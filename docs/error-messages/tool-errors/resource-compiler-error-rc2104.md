---
title: "资源编译器错误 RC2104 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2104
dev_langs: C++
helpviewer_keywords: RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce7fa189e03ec907c4b42f381096f095d5df734a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2104"></a>资源编译器错误 RC2104
未定义的关键字或密钥名称： 密钥  
  
 未定义指定的关键字或密钥名称。  
  
 此错误通常是由资源定义或附带的头文件中的拼写错误造成的。 也可能由头文件缺失造成。  
  
 若要解决此问题，请找到应包含已定义关键字或密钥名称的头文件，并验证其是否已包含在资源文件中以及关键字或密钥名称是否拼写正确。 如果你的项目是用预编译标头创建的且随后将其删除，请确保该资源文件仍包含所有所需标头。  
  
 若要验证的已定义的关键字和密钥名称在资源文件中，在 Visual Studio 中，打开**资源视图**窗口 — 在菜单栏上，选择**视图**，**资源视图**-和然后打开.rc 文件的快捷菜单并选择**资源符号**以查看定义的符号列表。 若要修改附带的标头，打开.rc 文件的快捷菜单，然后选择**资源包括**。  
  
 如果遇到以下消息：  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 打开 \MCL\MFC\Include\AfxRes.h 并添加此 Include 指令：  
  
```  
#include <winresrc.h>  
```