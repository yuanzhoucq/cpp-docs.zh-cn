---
title: "Internet 安全性 (C++) | Microsoft Docs"
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
  - "代码访问安全性 [C++], Internet 安全注意事项"
  - "代码签名 [C++]"
  - "代码签名 [C++], Internet 安全性"
  - "数字签名, Internet 安全性"
  - "Internet 应用程序, 安全性"
  - "沙盒"
  - "安全性 [MFC]"
  - "安全性 [MFC], Internet"
  - "Web 应用程序安全性"
  - "Web 应用程序安全性, Internet 安全方法"
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Internet 安全性 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代码安全性是一个主要问题开发人员以及 Internet 应用程序的用户。  有风险：恶意的篡改的代码、来自未知的站点或代码作者的和代码。  
  
 当 Internet 开发为时，有两个基本方法到安全性。  第一个称为“沙盒”。在这种方法，应用程序只限于特定组 API，并且是从可能存在危险中排除这些可能损坏 \(如程序在用户的计算机上的数据文件 I\/O。  使用数字签名，第二个实现。  此方法称为“用于 Internet 中热缩塑料打包”。  使用私钥\/公钥技术，则代码验证并签名。  在代码运行前，其数字签名验证确保代码来自已知验证的源代码，因此，未被修改，因为它签名。  
  
 在第一种情况下，您认为，应用程序将无法执行任何损害，您信任应用程序的原点。  在第二个中，数字签名用于验证。  是行业标准的数字签名的标识和提供有关代码的出版的详细信息。  根据标准，该技术包括 RSA 和 X.509。  如果他们要下载并运行应用不明，代码浏览器通常允许用户选择。  
  
 有关代码签名和其他安全措施的附加信息是在 Web 上可用。  信息可以在 MSDN Online 研讨会上 Web 站点访问 [http:\/\/msdn.microsoft.com\/](http://msdn.microsoft.com/)，或者通过万维网联盟上 [http:\/\/www.w3.org\/](http://www.w3.org/)的。  
  
## 请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)