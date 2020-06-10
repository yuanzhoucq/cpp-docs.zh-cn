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
ms.openlocfilehash: ce044014c5c2e13528cea8b982227b0ec8bc03fc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621544"
---
# <a name="internet-security-c"></a>Internet 安全性 (C++)

对于开发人员和 Internet 应用程序的用户来说，代码安全是一个主要问题。 存在风险：恶意代码、已篡改的代码以及来自未知站点或作者的代码。

针对 Internet 进行开发时，有两种基本的安全方法。 第一种称为 "沙盒"。 在此方法中，应用程序仅限于一组特定的 Api，并从潜在的危险（如文件 i/o，其中程序可能会损坏用户计算机上的数据）中排除。 第二个使用数字签名实现。 对于 Internet，此方法称为 "shrinkwrap"。 使用私钥/公钥技术验证代码并对其签名。 在运行代码之前，将验证其数字签名，以确保代码来自已知的经过身份验证的源，并且代码自签名后未发生更改。

在第一种情况下，你相信该应用程序不会有任何损害，并且你信任该应用程序的来源。 在第二种情况下，数字签名用于验证真实性。 数字签名是一种行业标准，用于标识和提供有关代码发布者的详细信息。 其技术基于标准，包括 RSA 和 x.509。 浏览器通常允许用户选择是否要下载并运行未知来源的代码。

## <a name="see-also"></a>另请参阅

[MFC Internet 编程任务](mfc-internet-programming-tasks.md)<br/>
[MFC Internet 编程基础知识](mfc-internet-programming-basics.md)
