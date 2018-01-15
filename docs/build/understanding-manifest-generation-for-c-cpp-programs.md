---
title: "了解 C/c + + 程序的清单生成 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: manifests [C++]
ms.assetid: a1f24221-5b09-4824-be48-92eae5644b53
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 848b4b449fa2c9c8930a616b70a5b61cb28d8fbf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-manifest-generation-for-cc-programs"></a>了解 C/C++ 程序的清单生成
A[清单](http://msdn.microsoft.com/library/aa375365)的 XML 文档可以是外部 XML 文件或资源嵌入到应用程序或程序集。 清单[隔离应用程序](http://msdn.microsoft.com/library/aa375190)用于管理的名称和版本的应用程序应在运行时绑定到的共享的并行程序集。 通过并行程序集清单指定名称、 版本、 资源和其他程序集上的依赖项。  
  
 有两种方法创建的独立应用程序或通过并行程序集清单。 首先，该程序集的作者可以手动创建以下规则和命名要求的清单文件。 或者，如果程序仅依赖于 Visual c + + CRT、 MFC 或 ATL 其他等的程序集，然后清单可以自动生成链接器。  
  
 Visual c + + 库标头包含程序集信息和在应用程序代码中包含这些库后，使用此程序集信息链接器以形成最终二进制文件的清单。 链接器不会嵌入二进制文件中，清单文件，并只能生成清单中的，作为外部文件。 作为外部文件具有一个清单可能不适用于所有方案。 例如，建议专用程序集具有嵌入清单。 在命令行版本中，如那些使用 nmake 若要生成代码，清单可以嵌入使用清单工具有关详细信息请参阅[在命令行的清单生成](../build/manifest-generation-at-the-command-line.md)。 在中构建时[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，可以通过设置的属性中的清单工具嵌入清单**项目属性**对话框，请参阅[Visual Studio 中的清单生成](../build/manifest-generation-in-visual-studio.md)。  
  
## <a name="see-also"></a>请参阅  
 [独立应用程序和通过并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)