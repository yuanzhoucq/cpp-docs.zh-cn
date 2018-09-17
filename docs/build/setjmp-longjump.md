---
title: setjmp longjump |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f53160a5deeb3ea0db111fc0aae7429b19b7cc86
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703269"
---
# <a name="setjmplongjump"></a>setjmp/longjump

当包含 setjmpex.h 或 setjmp.h 时，所有调用[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)将导致展开代码的调用析构函数，并最后调用。  这不同于 x86，其中包括 setjmp.h 结果在 finally 子句和析构函数不调用。

调用`setjmp`保留当前的堆栈指针、 非易失寄存器和 MxCsr 寄存器。  调用`longjmp`返回到最新`setjmp`调用堆栈指针、 非易失寄存器和 MxCsr 注册时，返回到状态为已保留的最新的站点和重置`setjmp`调用。

## <a name="see-also"></a>请参阅

[调用约定](../build/calling-convention.md)