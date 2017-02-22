---
title: "资源编译器错误 RC2144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2144"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2144"
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 资源编译器错误 RC2144
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

主语言 ID 不是数字  
  
 主语言 ID 必须是十六进制语言 ID。  有关有效的语言 ID 的列表，请参阅*《运行时库参考》*中的[语言和国家\/地区字符串](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)。  
  
 如果已使用工具添加资源并将其从 .RC 文件中删除，也可能发生此错误。  若要解决此问题，请在文本编辑器中打开 .RC 文件并手动清理任何未使用的资源。