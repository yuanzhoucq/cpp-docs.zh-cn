---
title: 附加启动注意事项 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d629451161d94853558887eb7029fc165d13d9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079214"
---
# <a name="additional-startup-considerations"></a>附加启动注意事项

在 C++ 中，对象构造和析构可能涉及执行用户代码。 因此，务必了解到的项之前发生的初始化`main`退出后调用的析构函数和`main`。 (有关构造和析构的对象的详细信息，请参阅[构造函数](../cpp/constructors-cpp.md)并[析构函数](../cpp/destructors-cpp.md)。)

到条目之前发生以下初始化`main`:

- 静态数据默认初始化为零。 没有显式初始值设定项的所有静态数据在执行任何其他代码（包括运行时初始化）前设置为零。 静态数据成员仍必须显式定义。

- 翻译单元中的全局静态对象的初始化。 这可能是之前进入`main`或首次使用的任何函数或对象的翻译单元中的对象之前。

**Microsoft 专用**

Microsoft c + + 中的全局静态对象之前，将初始化进入`main`。

**结束 Microsoft 专用**

相互依赖但位于不同翻译单元中的全局静态对象会导致错误行为。

## <a name="see-also"></a>请参阅

[启动和终止](../cpp/startup-and-termination-cpp.md)