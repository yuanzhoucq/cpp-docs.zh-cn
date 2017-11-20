---
title: "如何： 将迁移到的 clr： 纯 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- /clr compiler option [C++], migrating to /clr:pure
- migration [C++], pure MSIL
- pure MSIL [C++], porting to
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ebff4ae1ac304ee0af073de49f4ee988922247d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-migrate-to-clrpure-ccli"></a>如何：迁移到 /clr:pure (C++/CLI)
本主题讨论了将迁移到纯 MSIL 使用时可能出现的问题**/clr: pure** (请参阅[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)有关详细信息)。 本主题假定正在迁移的代码当前编译为混合程序集使用**/clr**选项，因为纯 MSIL 从非托管代码的迁移路径不是一个直接。 对于非托管代码，请参阅[如何： 迁移到 /clr](../dotnet/how-to-migrate-to-clr.md)然后再尝试将迁移到纯 MSIL。  
  
## <a name="basic-changes"></a>基本的更改  
 纯 MSIL 组成 MSIL 指令，因此包含无法在 MSIL 中表示的函数的代码将阻止编译。 这包括函数定义为使用调用约定不[__clrcall](../cpp/clrcall.md)。 （非 __clrcall 函数可以调用在纯 MSIL 组件中，但未定义。）  
  
 若要确保任何运行时错误，应启用 C4412 警告。 通过添加以下方法启用 C4412`#pragma warning (default : 4412)`到使用编译每个编译单位**/clr： 纯**和，通过 c + + 类型与其他 IJW (**/clr)**或本机代码。 请参阅[编译器警告 （等级 2） C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)有关详细信息。  
  
## <a name="architectural-considerations"></a>体系结构注意事项  
 中列出的纯 MSIL 程序集的限制的一些[纯代码和可验证代码 (C + + /cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)高级对产生影响应用程序设计和迁移策略。 最值得注意的是，与混合程序集，不同的是纯 MSIL 程序集不享受与非托管模块完全兼容。  
  
 纯 MSIL 程序集可以调用非托管的函数，但不能由非托管函数调用。 因此，纯 MSIL 是更适合于使用非托管的函数，不是它适用于由非托管函数的服务器代码的客户端代码。 如果要使用非托管函数中的纯 MSIL 程序集包含的功能，必须作为接口层使用混合程序集。  
  
 使用 ATL 或 MFC 应用程序不适合进行迁移到纯 MSIL，因为此版本中不支持这些库。 同样，[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]包含不在编译的标头文件**/clr: pure**。  
  
 尽管纯 MSIL 程序集可以调用非托管的函数，此功能将被限制为简单的 C 样式函数。 更复杂的非托管 Api 的使用很可能需要公开的 COM 接口或可以充当纯 MSIL 和非托管的组件之间的接口的混合程序集的形式的非托管的功能。 使用混合程序集层是使用采用回调函数，例如的非托管的函数，如纯程序集不能用作回调提供本机可调用函数的唯一方法。  
  
## <a name="application-domains-and-calling-conventions"></a>应用程序域和调用约定  
 但也可以纯 MSIL 程序集可以使用非托管的功能，函数和静态数据的处理方式不同。 在纯程序集，函数的实现是与[__clrcall](../cpp/clrcall.md)调用约定和静态数据是存储每个应用程序域。 这不同于默认值对于非托管和混合程序集，使用该对话框[__cdecl](../cpp/cdecl.md)函数的调用约定，并且在每个进程的基础上存储静态数据。  
  
 纯 MSIL （和使用 /clr: safe 编译的可验证代码） 的上下文中这些默认设置是透明的因为[__clrcall](../cpp/clrcall.md)是的 clr 的默认调用约定和应用程序域是静态的本机作用域和在.NET 应用程序的全局数据。 但是，当与非托管或混合的组件交互，不同的函数和全局数据的处理可能导致问题。  
  
 例如，如果纯 MSIL 组件是在非托管或混合 DLL 中调用函数，则 DLL 的头文件将用于编译纯程序集。 但是，除非没有显式指定的标头中的每个函数的调用约定，它们将所有被认为在[__clrcall](../cpp/clrcall.md)。 这将更高版本会导致运行时失败，因为这些函数很可能会与实现[__cdecl](../cpp/cdecl.md)约定。 非托管的标头文件中的函数可以显式标记为[__cdecl](../cpp/cdecl.md)，或必须在重新编译整个 DLL 源代码**/clr: pure**。  
  
 同样，假定函数指针到指向[__clrcall](../cpp/clrcall.md)下函数**/clr: pure**编译。 这些太必须显式添加批注使用正确的调用约定。  
  
 有关详细信息，请参阅[应用程序域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)。  
  
## <a name="linking-limitations"></a>链接限制  
 Visual c + + 链接器将不尝试链接混合和纯 OBJ 文件，因为存储作用域和调用约定不相同。  
  
## <a name="see-also"></a>另请参阅  
 [纯代码和可验证代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)