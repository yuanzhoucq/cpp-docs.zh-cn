---
title: Naked 函数调用 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e395bcb32858bc63b3e848f20a7d794156876e26
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402024"
---
# <a name="naked-function-calls"></a>Naked 函数调用
## <a name="microsoft-specific"></a>Microsoft 专用  
 使用声明函数**裸**属性发出而无需 prolog 或 epilog 代码，使您能够编写你自己使用的自定义 prolog/epilog 序列[内联汇编程序](../assembler/inline/inline-assembler.md)。 将裸函数作为高级功能提供。 利用这些函数，您可以声明从 C/C++ 之外的上下文中调用的函数，从而作出有关参数位置或保留哪些寄存器的各种假设。 示例包括例程（如中断处理程序）。 此功能对于虚拟设备驱动程序 (VxDs) 的编写器特别有用。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么？  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [裸函数的规则和限制](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [有关编写 Prolog/Epilog 代码的注意事项](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../cpp/calling-conventions.md)