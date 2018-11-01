---
title: Internet 安全性 (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: e7892793a82f2b030a99465a712e33e1b9ef4673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486094"
---
# <a name="internet-security-c"></a>Internet 安全性 (C++)

代码安全是一个主要问题对于开发人员和 Internet 应用程序的用户。 有风险： 恶意代码、 被篡改的代码和代码未知的站点或作者。

针对 Internet 进行开发时，有两种基本安全方法。 第一种称为"沙盒处理。" 在这种方法中的应用程序限制为一组特定的 Api，并且从具有潜在危险的服务，例如文件 I/O 程序可能会破坏用户的计算机上的数据中排除。 第二个是使用数字签名实现的。 这种方法称为"shrinkwrap"为 Internet。 代码验证和签名使用私钥/公钥关键技术。 运行代码之前，验证其数字签名以确保代码是从已知的经过身份验证源和代码在已签名后未被修改。

在第一种情况下，您信任应用程序不会执行任何不利影响和信任的应用程序的源。 在第二种，使用数字签名以验证真实性。 数字签名是用来确定，并提供有关代码的发布服务器的详细信息的行业标准。 其技术，基于标准，包括 RSA 和 X.509。 浏览器通常允许用户选择他们想要下载并运行未知来源的代码。

## <a name="see-also"></a>请参阅

[MFC Internet 编程任务](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC Internet 编程基础知识](../mfc/mfc-internet-programming-basics.md)

