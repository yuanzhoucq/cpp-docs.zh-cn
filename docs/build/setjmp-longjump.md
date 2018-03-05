---
title: "setjmp longjump |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 744b855d1b867507b54973f17e2a4f98b63e2b67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setjmplongjump"></a>setjmp/longjump
当您包括 setjmpex.h 或 setjmp.h 时，则所有调用[setjmp](../c-runtime-library/reference/setjmp.md)或[longjmp](../c-runtime-library/reference/longjmp.md)将导致展开时，将调用析构函数，最后调用。  这不同于 x86、 最后子句中包括 setjmp.h 结果的位置以及析构函数不调用。  
  
 调用`setjmp`保留当前的堆栈指针、 非易失寄存器和 MxCsr 寄存器。  调用`longjmp`返回到最新`setjmp`调用堆栈指针、 非易失寄存器和 MxCsr 注册时，回状态因为保留的最新的站点，并重置`setjmp`调用。  
  
## <a name="see-also"></a>请参阅  
 [调用约定](../build/calling-convention.md)