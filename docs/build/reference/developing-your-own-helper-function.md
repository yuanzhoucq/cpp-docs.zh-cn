---
title: "开发你自己的 Helper 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3a2683fbc259cbac3551840f9ebe6e7c651430bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="developing-your-own-helper-function"></a>开发您自己的 Helper 函数
你可能想要提供您自己执行基于名称的 DLL 或导入的特定处理例程的版本。 执行此操作的两种方法： 编码你自己的基于提供的代码，或只将挂钩使用前面详细介绍通知挂钩所提供的版本。  
  
 代码自己  
 这是相当简单，因为你实际上可以用提供的代码作为参考新。 当然，它必须遵守的调用约定，并且如果它返回到链接器生成的 thunk，它必须返回正确的函数指针。 一次在代码中，你可以执行几乎任何所需以便满足调用或通过调用。  
  
 使用启动处理通知挂钩  
 可能是最简单的方法只需提供对接收通知 dliStartProcessing 上的默认帮助程序相同的值的用户提供通知挂钩函数的新指针。 此时，挂钩函数可以实质上是将成为新的帮助器函数，如成功返回到默认帮助器将绕过默认帮助程序中的所有进一步处理。  
  
## <a name="see-also"></a>另请参阅  
 [延迟加载 DLL 的链接器支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)