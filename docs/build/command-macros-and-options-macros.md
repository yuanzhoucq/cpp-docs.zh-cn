---
title: 命令宏和选项宏
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: daf8c243f95f7cc12a3d3b1c5cf16f5a384c9671
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418292"
---
# <a name="command-macros-and-options-macros"></a>命令宏和选项宏

命令宏是 Microsoft 产品的预定义的。 选项宏表示这些产品的选项，默认情况下未定义。 同时在预定义的推理规则中使用，并可以描述块或用户定义的推理规则中使用。 可以重新定义命令宏来表示部分或全部的命令行，其中包括选项。 如果未定义，选项宏生成空字符串。

|Microsoft 产品|命令宏|定义为|选项宏|
|-----------------------|-------------------|----------------|-------------------|
|宏汇编程序|**AS**|ml|**AFLAGS**|
|基本编译器|**BC**|bc|**BFLAGS**|
|C 编译器|**CC**|cl|**CFLAGS**|
|C++ 编译器|**CPP**|cl|**CPPFLAGS**|
|C++ 编译器|**CXX**|cl|**CXXFLAGS**|
|资源编译器|**RC**|rc|**RFLAGS**|

## <a name="see-also"></a>请参阅

[特殊 NMAKE 宏](../build/special-nmake-macros.md)
