---
title: "生成 C/c + + 独立应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5af0dde80a143166d9824d2739632ca7e7ed4382
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="building-cc-isolated-applications"></a>生成 C/C++ 独立应用程序
独立应用程序仅取决于通过并行程序集，并将绑定到使用清单及其依赖项。 不需要应用程序，以便在 Windows; 上正确运行完全隔离但是，通过在造成应用程序完全隔离方面的投资，你可能节省时间，如果需要应用程序在将来提供服务。 使应用程序完全独立的好处的详细信息，请参阅[独立应用程序](http://msdn.microsoft.com/library/aa375190)。  
  
 生成使用 Visual c + + 本机 C/c + + 应用程序时，则在默认情况下，Visual Studio 项目系统将生成清单文件描述 Visual c + + 库上的应用程序的依赖关系。 如果这些是唯一的依赖项你的应用程序就会具有，则它将成为独立应用程序，只要它使用 Visual Studio 重新生成。 如果你的应用程序在运行时，使用其他库，则可能需要重新这些库生成为通过并行程序集[构建 C/c + + 端并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)。  
  
## <a name="see-also"></a>另请参阅  
 [独立应用程序和通过并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)