---
title: 默认信号 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- default signals
- defaults, signals
ms.assetid: db9fc17b-75c0-4d33-86be-c536584bbede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78c369665d398d4b326cf8d27ad0944a594fe1a4
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43758932"
---
# <a name="default-signals"></a>默认信号

ANSI 4.7.1.1 调用信号处理程序前未执行 `signal(sig, SIG_DFL)` 的等效项时，对所执行信号的阻止

程序开始运行时，信号将设置为其默认状态。  
  
## <a name="see-also"></a>请参阅

[库函数](../c-language/library-functions.md)