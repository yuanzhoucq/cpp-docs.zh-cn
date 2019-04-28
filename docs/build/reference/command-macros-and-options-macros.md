---
title: 命令宏和选项宏
ms.date: 11/04/2016
helpviewer_keywords:
- options macros
- command macros in NMAKE
- macros, options macros
- macros, command macros
ms.assetid: 50dff03c-0dc3-4a8a-9a17-57e0e4ea9bac
ms.openlocfilehash: c6dad7b50d265a1460a98747665d48051078163a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272433"
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

[特殊 NMAKE 宏](special-nmake-macros.md)
