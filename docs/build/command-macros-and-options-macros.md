---
title: 命令宏和选项宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c66295a42fff6a2e6dde5205fb5d9139e6eceb6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705531"
---
# <a name="command-macros-and-options-macros"></a>命令宏和选项宏

命令宏是 Microsoft 产品的预定义的。 选项宏表示这些产品的选项，默认情况下未定义。 同时在预定义的推理规则中使用，并可以描述块或用户定义的推理规则中使用。 可以重新定义命令宏来表示部分或全部的命令行，其中包括选项。 如果未定义，选项宏生成空字符串。

|Microsoft 产品|命令宏|定义为|选项宏|
|-----------------------|-------------------|----------------|-------------------|
|宏汇编程序|**为**|ml|**AFLAGS**|
|基本编译器|**业务连续性**|业务连续性|**BFLAGS**|
|C 编译器|**抄送**|cl|**那**|
|C++ 编译器|**CPP**|cl|**CPPFLAGS**|
|C++ 编译器|**CXX**|cl|**CXXFLAGS**|
|资源编译器|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>请参阅

[特殊 NMAKE 宏](../build/special-nmake-macros.md)