---
title: "Internet 安全性 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 879078481cde75841cf180329ef67a6badfa4b61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="internet-security-c"></a>Internet 安全性 (C++)
代码安全性是一个主要问题对于开发人员和 Internet 应用程序的用户。 有风险： 恶意代码、 被篡改的代码和代码未知的站点或作者。  
  
 在开发用于 Internet 时，有两种基本方法安全。 第一种称为"沙盒处理。" 在此方法中，应用程序是限于一组特定的 Api，以及从具有潜在危险的字体，例如，程序可能会破坏用户的计算机上的数据的文件 I/O 排除。 第二个是使用数字签名实现的。 这种方法称为"shrinkwrap"互联网。 代码验证和签名使用私钥/公钥关键技术。 运行代码之前，验证其数字签名以确保代码是从已知的经过身份验证源，并后已签名的代码未被修改。  
  
 在第一种情况，你可以信任应用程序不会执行任何损害，而您信任的源的应用程序。 在第二个数字签名用于验证真实性。 数字签名是用来标识和提供有关代码的发布者详细信息的行业标准。 其技术基于标准，包括 RSA 和 X.509。 浏览器通常允许用户选择他们想要下载并运行未知来源的代码。  
  
  
## <a name="see-also"></a>另请参阅  
 [MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)   
 [MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)

