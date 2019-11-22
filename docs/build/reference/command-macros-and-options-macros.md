---
title: 命令宏和选项宏
description: 介绍用于生成工具的预定义 NMAKE 宏及其选项。
ms.date: 11/20/2019
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
no-loc:
- AS
- AFLAGS
- CC
- CFLAGS
- CPP
- CPPFLAGS
- CXX
- CXXFLAGS
- RC
- RFLAGS
- ias
- ml
- ml64
- cl
- rc
ms.openlocfilehash: d5c4477fd97e2a6c48dbac4d0ce83f7fd5f12ad6
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303174"
---
# <a name="command-macros-and-options-macros"></a>命令宏和选项宏

为 Microsoft 产品预定义了命令宏。 选项宏表示这些产品的选项，默认情况下未定义。 二者都用于预定义的推理规则中，并且可在描述块或用户定义的推理规则中使用。 可以重新定义命令宏，以表示命令行的部分或全部，包括选项。 如果未定义，选项宏将生成空字符串。

|Microsoft 产品|命令宏|定义为|Options 宏|
|-----------------------|-------------------|----------------|-------------------|
|宏组装器|**AS**|ml、 ias或 ml64|**AFLAGS**|
|C 编译器|**CC**|cl|**CFLAGS**|
|C++ 编译器|**CPP**|cl|**CPPFLAGS**|
|C++ 编译器|**CXX**|cl|**CXXFLAGS**|
|资源编译器|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>另请参阅

[特殊 NMAKE 宏](special-nmake-macros.md)
