---
title: "TN035： 使用 Visual c + + 中使用多个资源文件和头文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.resources
dev_langs: C++
helpviewer_keywords:
- resource files, multiple
- TN035
ms.assetid: 1f08ce5e-a912-44cc-ac56-7dd93ad73fb6
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9c03c642dfc3524f69f4aa8d1a397f750b42db27
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="tn035-using-multiple-resource-files-and-header-files-with-visual-c"></a>TN035：在 Visual C++ 中使用多个资源文件和头文件
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 本说明介绍 Visual C++ 资源编辑器如何支持在单个项目中或多个项目间共享的多个资源文件与头文件，并说明如何利用这一支持。 本说明回答以下问题：  
  
-   如果可能想要拆分到多个资源文件和/或标头文件的项目和如何操作  
  
-   如何共享常见标头。H 之间两个文件。RC 文件  
  
-   如何将项目资源划分为多个。RC 文件  
  
-   你 （和工具） 如何管理之间建立依赖关系。RC。CPP，和。H 文件  
  
 请注意，如果向项目添加其他资源文件，ClassWizard 不会识别此添加文件中的资源。  
  
 本说明按如下结构回答上述问题：  
  
- **概述如何 Visual c + + 管理资源文件和头文件**提供 Visual c + + 中的资源设置包括命令如何允许你使用多个资源文件和同一项目中的标头文件的概述。  
  
- **AppWizard 创建的分析。RC 和。H 文件**由 AppWizard 创建的应用程序的多个资源和标头文件中查找。 这些文件用作你可能需要添加到项目的其他资源文件和头文件的很好模型。  
  
- **包括其他头文件**介绍何时可能想要包括多个标头文件，并提供如何执行此操作的详细信息。  
  
- **共享之间两个标头文件。RC 文件**显示如何可以共享多个之间的一个标头文件。RC 文件在不同项目中，也可以在同一项目。  
  
- **使用同一项目中的多个资源文件**介绍你可能想要分解成多个项目。RC 文件，并提供如何执行此操作的详细信息。  
  
- **强制非可编辑的 Visual c + + 文件**介绍如何才能确保 Visual c + + 不编辑，无意中重新设置格式的自定义资源。  
  
- **管理共享的多个 Visual c + + 编辑符号。RC 文件**描述如何在多个共享同一符号。RC 文件以及如何避免将重复 ID 数值分配。  
  
- **管理之间的依赖关系。RC。CPP，和。H 文件**介绍 Visual c + + 如何避免不必要的重新编译。依赖于资源符号文件的 CPP 文件。  
  
- **如何 Visual c + + 管理设置包括信息**提供有关如何将跟踪 Visual c + + 的多个 （嵌套） 的技术详细信息。RC 文件和多个标头文件的 # include 指令包括的。RC 文件。  
  
 **如何 Visual c + + 的概述管理资源文件和头文件**  
  
 Visual C++ 将单个 .RC 资源文件和相应的 .H 头文件作为紧密关联的文件对进行管理。 编辑并保存 .RC 文件中的资源时，将间接编辑并保存相应 .H 文件中的符号。 虽然可以同时打开并编辑多个 .RC 文件（使用 Visual C++ 的 MDI 用户界面），但对于任何给定 .RC 文件，仅间接编辑一个相应的头文件。  
  
 **符号头文件**  
  
 默认情况下，无论资源文件的名称为何（例如 MYAPP.RC），Visual C++ 始终将相应的头文件命名为 RESOURCE.H。 使用**资源包括**命令**视图**Visual c + + 中的菜单上，你可以通过更新符号头文件文件中的更改此标头文件的名称**设置包括**对话框。  
  
 **只读符号指令**  
  
 虽然 Visual C++ 对于任何给定 .RC 文件仅编辑一个头文件，但 Visual C++ 支持引用在其他只读头文件中定义的符号。 使用**资源包括**命令**视图**菜单在 Visual c + + 中，你可以作为只读符号指令中指定任意数量的其他只读头文件。 在“只读”限制下，当你在 .RC 文件中添加新资源时，可使用只读头文件中定义的符号；但如果删除此资源，符号仍将保留在只读头文件中。 无法更改分配给只读符号的数值。  
  
 **编译时指令**  
  
 Visual C++ 还支持嵌套资源文件，即通过 #include 指令将一个 .RC 文件包括在另一 .RC 文件中。 使用 Visual C++ 编辑给定 .RC 文件时，通过 #include 指令包括的文件中的任何资源将不可见。 但当你编译此 .RC 文件时，也将编译通过 #include 指令包括的文件。 使用**资源包括**命令**视图**Visual c + + 中的菜单上，你可以指定任意数量的 # include 指令包括的。RC 文件作为编译时指令。  
  
 请注意会发生什么情况如果读取到 Visual c + +。RC 文件的 #include 的另一个。RC 文件*不*指定为编译时指令。 如果将先前通过文本编辑器手动维护的 .RC 文件置于 Visual C++ 中，则可能会发生此情况。 Visual C++ 读取通过 #include 指令包括的 .RC 文件时，会将通过 #include 指令包括的资源合并到父 .RC 文件。 保存父 .RC 文件时，#include 语句实际上将被通过 #include 指令包括的资源替代。 如果您不希望合并，则应该删除 #include 语句从父节点。RC 文件*以前*读取到 Visual c + +; 然后使用 Visual c + +，将返回同一 #include 语句作为编译时指令。  
  
 Visual c + + 将保存在。RC 文件以上三种设置包括信息 （符号头文件、 只读符号指令和编译时指令） 在 #include 指令*和*TEXTINCLUDE 资源中。 TEXTINCLUDE 资源，你通常不必处理的实现细节详见[如何 Visual c + + 管理设置包括信息](#_mfcnotes_tn035_set_includes)。  
  
 **AppWizard 创建的分析。RC 和。H 文件**  
  
 通过检查 AppWizard 生成的应用程序代码，可以了解 Visual C++ 如何管理多个资源文件和头文件。 下面检查的代码摘自 AppWizard 使用默认选项生成的 MYAPP 应用程序。  
  
 AppWizard 创建的应用程序使用多个资源文件和多个头文件，如下图汇总所示：  
  
```  
RESOURCE.H     AFXRES.H      
 \       /                
 \     /  
    MYAPP.RC 
 |  
 |                
    RES\MYAPP.RC2 
    AFXRES.RC 
    AFXPRINT.RC 
```  
  
 可使用 Visual C++“文件包括”/“设置包括”命令查看其中多个文件关系。  
  
 MYAPP.RC  
 使用 Visual C++ 编辑的应用程序资源文件。  
  
 RESOURCE.H 是特定于应用程序的头文件。 AppWizard 始终将此文件命名为 RESOURCE.H，与 Visual C++ 的默认头文件命名方式一致。 此头文件的 #include 是资源文件 (MYAPP.RC) 中的第一个语句：  
  
```  
//Microsoft Visual C++ generated resource script  
//  
#include "resource.h"  
```  
  
 RES\MYAPP.RC2  
 包含不会由 Visual C++ 编辑，但将包括在最终编译 .EXE 文件中的资源。 默认情况下，AppWizard 不创建此类资源，因为 Visual C++ 可编辑所有标准资源，包括版本资源（此版本中的新功能）。 AppWizard 将生成空文件，以便你将已设置格式的自有自定义资源添加到此文件。  
  
 如果使用已设置格式的自定义资源，可将这些资源添加到 RES\MYAPP.RC2 并使用 Visual C++ 进行编辑。  
  
 AFXRES.RC 和 AFXPRINT.RC 包含框架的某些功能所需的标准资源。 与 RES\MYAPP.RC2 类似，框架提供的这两个资源文件通过 #include 指令包括在 MYAPP.RC 末尾，并且这两个资源文件在“设置包括”对话框的编译时指令中指定。 因此，在 Visual C++ 中编辑 MYAPP.RC 时，无法直接查看或编辑这些框架资源，但这些资源将编译到应用程序的二进制 .RES 文件和最终 .EXE 文件。 有关标准框架资源，包括修改它们，过程的详细信息请参阅[技术说明 23](../mfc/tn023-standard-mfc-resources.md)。  
  
 AFXRES.H 定义框架使用（尤其是在 AFXRES.RC 中使用）的标准符号，例如 `ID_FILE_NEW`。 AFXRES.H 还通过 #include 指令包括 WINRES.H，其中包含 Visual C++ 生成的 .RC 文件及 AFXRES.RC 所需的 WINDOWS.H 的一部分。 AFXRES.H 中定义的符号在你编辑应用程序资源文件 (MYAPP.RC) 时可用。 例如，`ID_FILE_NEW` 用于 MYAPP.RC 菜单资源中的“文件新建”菜单项。 无法更改或删除这些框架定义的符号。  
  
## <a name="_mfcnotes_tn035_including"></a>包括其他头文件  
  
 AppWizard 创建的应用程序仅包括两个头文件：RESOURCE.H 和 AFXRES.H。 只有 RESOURCE.H 特定于应用程序。 在以下情况下，你可能需要包括其他只读头文件：  
  
 头文件由外部源提供，或者你希望在多个项目之间或同一项目的多个部分之间共享头文件。  
  
 头文件包含你不希望 Visual C++ 在保存文件时更改或筛选出的格式与注释。 例如，你可能希望保留使用符号算术的 #define，例如：  
  
```  
#define RED 0  
#define BLUE 1  
#define GREEN 2  
#define ID_COLOR_BUTTON 1001  
#define ID_RED_BUTTON (ID_COLOR_BUTTON + RED)  
#define ID_BLUE_BUTTON (ID_COLOR_BUTTON + BLUE)  
#define ID_GREEN_BUTTON (ID_COLOR_BUTTON + GREEN)  
```  
  
 您可以通过使用包括其他只读头文件**资源包括**命令指定 #include 语句为第二个只读符号指令，如：  
  
```  
#include "afxres.h"  
#include "second.h"  
```  
  
 新文件关系图现在如下所示：  
  
```  
    AFXRES.H 
RESOURCE.H     SECOND.H      
 \       /                
 \     /  
    MYAPP.RC 
 |  
 |                
    RES\MYAPP.RC2 
    AFXRES.RC 
    AFXPRINT.RC 
```  
  
 **共享之间两个标头文件。RC 文件**  
  
 你可能需要在位于不同项目或同一项目中的两个 .RC 文件之间共享头文件。 为此，只需对这两个 .RC 文件应用上述只读指令技巧。 如果两个 .RC 文件用于不同应用程序（不同项目），结果将如下图所示：  
  
```  
    RESOURCE.H AFXRES.H   RESOURCE.H    
 (for MYAPP1) SECOND.H   (for MYAPP2)               
 \       /     \       /             
 \     /       \     /               
    MYAPP1.RC MYAPP2.RC */    \        /     \ */      \      /       \              
RES\MYAPP1.RC2  AFXRES.RC     RES\MYAPP2.RC2                
    AFXPRINT.RC 
```  
  
 下面将讨论同一应用程序（项目）中的两个 .RC 文件共享另一头文件的情况。  
  
 **使用同一项目中的多个资源文件**  
  
 Visual C++ 和资源编译器通过 #include 指令将一个 .RC 文件包括在另一 .RC 文件中，以此支持同一项目中的多个 .RC 文件。 允许多层嵌套。 将项目资源拆分到多个 .RC 文件有着多种原因：  
  
-   如果将资源拆分到多个 .RC 文件，将更易于管理多个项目团队成员间的大量资源。 如果使用源控件管理包来签出文件和签入更改，将资源拆分到多个 .RC 文件可使你更细致地控制对资源更改的管理。  
  
-   如果要使用预处理器指令（如 #ifdef、#endif 和 #define），你必须将部分资源隔离在将由资源编译器编译的只读资源中。  
  
-   与一个复合 .RC 文件相比，多个组件 .RC 文件可在 Visual C++ 中更快加载和保存。  
  
-   如果要通过文本编辑器以可读格式维护资源，应将资源保留在 Visual C++ 未编辑的 .RC 文件中。  
  
-   如果需要以其他专用数据编辑器可解释的二进制格式或文本格式保留用户定义的资源，则应将资源保留在单独 .RC 文件中，以防 Visual C++ 将格式更改为十六进制数据。 。在 MFC 高级概念示例 WAV （声音） 文件资源[SPEAKN](../visual-cpp-samples.md)是一个很好示例。  
  
 还可以在“设置包括”对话框的编译时指令中通过 #include 指令包括另一 .RC 文件：  
  
```  
#include "res\myapp.rc2"  // non-Visual C++ edited resources  
#include "second.rc"  // THE SECOND .RC FILE  
  
#include "afxres.rc"  // Standard components  
#include "afxprint.rc"  // printing/print preview resources  
```  
  
 结果如下图所示：  
  
```  
RESOURCE.H     AFXRES.H      
 \       /                
 \     /  
    MYAPP.RC 
 |  
 |                
    RES\MYAPP.RC2 
    SECOND.RC 
    AFXRES.RC 
    AFXPRINT.RC 
```  
  
 使用编译时指令时，可以将 Visual C++ 可编辑和不可编辑的资源组织到多个 .RC 文件中，其中，“主”MYAPP.RC 不执行任何操作，但会通过 #include 指令包括其他 .RC 文件。 如果使用 Visual C++ 项目 .MAK 文件，则应包括项目中的“主”.RC 文件，以便所有通过 #include 指令包括的资源随应用程序一起编译。  
  
 **强制执行的不可编辑的 Visual c + + 文件**  
  
 应用程序向导创建 RES\MYAPP 中。RC2 文件是包含你执行操作的资源的文件的示例*不*想要被意外读取到 Visual c + +，然后将其写回丢失格式信息。 要避免此问题，请将以下各行置于 RES\MYAPP.RC2 文件的开头：  
  
```  
#ifdef APSTUDIO_INVOKED  
 #error this file is not editable by Visual C++  
#endif //APSTUDIO_INVOKED  
```  
  
 当 Visual c + + 编译。RC 文件，它定义**APSTUDIO_INVOKED**以及**RC_INVOKED**。 如果 AppWizard 创建的文件结构被破坏，并且 Visual C++ 读取上述 #error 行，则它将报告错误，并中止读取 .RC 文件。  
  
 **管理共享的多个 Visual c + + 编辑符号。RC 文件**  
  
 将资源拆分到你要在 Visual C++ 中单独编辑的多个 .RC 文件时，将产生两个问题：  
  
-   你可能需要在多个 .RC 文件之间共享同一符号。  
  
-   你需要帮助 Visual C++ 避免将相同 ID 数值分配到不同资源（符号）。  
  
 下图说明了解决第一个问题的 .RC 和 .H 文件的组织：  
  
```  
    MYAPP.RC */         \ */           \  
MYSTRS.H   / MYSHARED.H  \  MYMENUS.H  
 \    /    /      \   \    \  
 \  /    /        \   \    \  
    MYSTRS.RC MYMENUS.RC  
```  
  
 在此示例中，字符串资源保留在一个资源文件 MYSTRS.RC 中，菜单保留在另一资源文件 MYMENUS.RC 中。 某些符号（如命令）可能需要在两个文件之间共享。 例如，ID_TOOLS_SPELL 可能是“工具”菜单中“拼写”项的菜单命令 ID；也可能是应用程序主窗口状态栏中的框架所显示的命令提示符的字符串 ID。  
  
 ID_TOOLS_SPELL 符号保留在共享头文件 MYSHARED.H 中。 可使用文本编辑器手动维护此共享头文件；Visual C++ 不会直接编辑此文件。 在两个资源文件 MYSTRS。RC 和 MYMENUS。指定 RC，#include MYSHARED。H 为 MYAPP 的只读指令中。RC，使用**资源包括**命令，如前面所述。  
  
 最方便的做法是，先预计将共享的符号，然后再尝试使用此符号标识任何资源。 将符号添加到共享头文件，如果尚未通过 #include 指令将共享头文件包括在 .RC 文件的只读指令中，请先完成此操作再使用符号。 如果未预计到以此方式共享符号，则在 MYSTRS.RC 中使用符号前，必须手动（使用文本编辑器）将符号的 #define 语句从比如 MYMENUS.H 移至 MYSHARED.H。  
  
 管理多个 .RC 文件中的符号时，还必须帮助 Visual C++ 避免将相同 ID 数值分配到不同资源（符号）。 对于任何给定 .RC 文件，Visual C++ 将以增量方式在四个 ID 域的每个域中分配 ID。 在编辑会话之间，Visual C++ 将跟踪它在 .RC 文件的符号头文件的每个域中分配的最后一个 ID。 下面是空（新）.RC 文件的 APS_NEXT 值：  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  101  
#define _APS_NEXT_COMMAND_VALUE   40001  
#define _APS_NEXT_CONTROL_VALUE   1000  
#define _APS_NEXT_SYMED_VALUE     101  
```  
  
 **_APS_NEXT_RESOURCE_VALUE**是将用于对话框资源、 菜单资源等的下一符号值。 资源符号值的有效范围为 1 到 0x6FFF。  
  
 **_APS_NEXT_COMMAND_VALUE**是将用于命令标识的下一符号值。 命令符号值的有效范围为 0x8000 到 0xDFFF。  
  
 **_APS_NEXT_CONTROL_VALUE**是将用于对话框控件的下一符号值。 对话框控件符号值的有效范围为 8 到 0xDFFF。  
  
 **_APS_NEXT_SYMED_VALUE**是当你手动分配符号值在符号浏览器中使用新命令，将发出的下一符号值。  
  
 创建新 .RC 文件时，Visual C++ 先使用略高于最低合法值的值。 AppWizard 还会初始化这些值以更适于 MFC 应用程序。 有关 ID 值范围的详细信息，请参阅[技术说明 20](../mfc/tn020-id-naming-and-numbering-conventions.md)。  
  
 现在 Visual c + + 每次创建新的资源文件，即使在同一项目中，定义相同**_APS_NEXT\_** 值。 因此，如果你在两个不同 .RC 文件中添加比如多个对话框，则 Visual C++ 很可能会将相同 #define 值分配到不同对话框。 例如，第一个 .RC 文件中的 IDD_MY_DLG1 可能会获得与第二个 .RC 文件中的 IDD_MY_DLG2 相同的数字 101。  
  
 若要避免此问题，应在各自 .RC 文件中对四个 ID 域中的每个域保留不同的数值范围。 执行此操作通过手动更新**_APS_NEXT**中每个值。RC 文件`before`开始将资源添加。 例如，如果第一个。RC 文件使用默认值**_APS_NEXT**值，则你可能想要分配以下**_APS_NEXT**第二个值。RC 文件：  
  
```  
#define _APS_NEXT_RESOURCE_VALUE  2000  
#define _APS_NEXT_COMMAND_VALUE   42000  
#define _APS_NEXT_CONTROL_VALUE   2000  
#define _APS_NEXT_SYMED_VALUE     2000  
```  
  
 当然，Visual C++ 仍可能会在第一个 .RC 文件中分配多个 ID，导致这些数值开始与为第二个 .RC 文件保留的数值重叠。 你应保留足够大的范围，避免此情况发生。  
  
 **管理之间的依赖关系。RC。CPP，和。H 文件**  
  
 Visual C++ 保存 .RC 文件时，还会保存对相应 RESOURCE.H 文件的符号更改。 引用 .RC 文件中的资源的任何 .CPP 文件必须通过 #include 指令包括 RESOURCE.H 文件，此文件通常位于你项目的主头文件中。 这将导致意外的副作用，因为开发环境的内部项目管理将浏览源文件的头依赖关系。 每次在 Visual C++ 中添加新符号时，均需重新编译通过 #include 指令包括 RESOURCE.H 的所有 .CPP 文件。  
  
 Visual C++ 通过包括以下注释作为 RESOURCE.H 文件的第一行来避开对 RESOURCE.H 的依赖：  
  
```  
//{{NO_DEPENDENCIES}}  
```  
  
 开发环境将解释此注释，忽略对 RESOURCE.H 的更改，从而无需重新编译依赖的 .CPP 文件。  
  
 Visual C++ 每次保存 .RC 文件时，均会将 //{{NO_DEPENDENCIES}} 注释行添加到此文件。 某些情况下，避开对 RESOURCE.H 的生成依赖可能会导致在链接时检测不到运行时错误。 例如，使用符号浏览器来更改分配到资源符号的数值时，如果未重新编译引用资源的 .CPP 文件，则无法在应用程序运行时正确查找和加载资源。 在这种情况下，则应显式重新编译任何。在资源中符号更改会影响你知道的 CPP 文件。H 或选择**全部重新生成**。 如果你具有需要频繁更改一组资源的符号值，您可能会发现它更加方便和安全准备好这些符号置于单独只读头文件中，如上面的部分中所述[包括其他头文件](#_mfcnotes_tn035_including)。  
  
## <a name="_mfcnotes_tn035_set_includes"></a>如何管理 Visual c + + 集包括信息 * *  
  
 如上所述，使用“文件”菜单的“设置包括”命令可指定三种类型的信息：  
  
-   符号头文件  
  
-   只读符号指令  
  
-   编译时指令  
  
 下面说明了 Visual C++ 如何维护 .RC 文件中的这些信息。 你不需要这些信息来使用 Visual C++，但是，这能够加强你的理解，使你能够更自信地使用“设置包括”功能。  
  
 上述所有这三种类型的设置包括信息均以两种格式存储在 .RC 文件中：(1) 作为 #include 或资源编译器可解释的其他指令；(2) 作为只能由 Visual C++ 解释的特殊 TEXTINCLUDE 资源。  
  
 TEXTINCLUDE 资源的目的是设置包括信息安全存储是易于演示 Visual c + + 的窗体中**设置包括**对话框。 TEXTINCLUDE 是*资源类型*定义由 Visual c + +。 Visual C++ 可识别具有资源标识符 1、2 和 3 的三种特定 TEXTINCLUDE 资源：  
  
|TEXTINCLUDE 资源 ID|设置包括信息的类型|  
|-----------------------------|--------------------------------------|  
|1|符号头文件|  
|2|只读符号指令|  
|3|编译时指令|  
  
 所有这三种类型的设置包括信息均由 AppWizard 创建的默认 MYAPP.RC 和 RESOURCE.H 文件阐释（如下所述）。 RC 语法需在 BEGIN 和 END 块之间使用额外的 \0 和 "" 标记来分别指定以零结尾的字符串和双引号字符。  
  
## <a name="symbol-header-file"></a>符号头文件  
 资源编译器解释的符号头文件信息的格式只是一个 #include 语句：  
  
```  
#include "resource.h"  
```  
  
 相应的 TEXTINCLUDE 资源是：  
  
```  
1 TEXTINCLUDE DISCARDABLE  
BEGIN  
 "resource.h\0"  
END  
```  
  
## <a name="read-only-symbol-directives"></a>只读符号指令  
 只读符号指令以资源编译器可解释的以下格式包括在 MYAPP.RC 顶部：  
  
```  
#include "afxres.h"  
```  
  
 相应的 TEXTINCLUDE 资源是：  
  
```  
2 TEXTINCLUDE DISCARDABLE  
BEGIN  
   "#include ""afxres.h""\r\n"  
   "\0"  
END  
```  
  
## <a name="compile-time-directives"></a>编译时指令  
 编译时指令以资源编译器可解释的以下格式包括在 MYAPP.RC 末尾：  
  
```  
#ifndef APSTUDIO_INVOKED  
///////////////////////  
//  
// From TEXTINCLUDE 3  
//  
#include "res\myapp.rc2"  // non-Visual C++ edited resources  
  
#include "afxres.rc"  // Standard components  
#include "afxprint.rc"  // printing/print preview resources  
#endif  // not APSTUDIO_INVOKED  
```  
  
 #ifndef APSTUDIO_INVOKED 指令指示 Visual C++ 跳过编译时指令。  
  
 相应的 TEXTINCLUDE 资源是：  
  
```  
3 TEXTINCLUDE DISCARDABLE  
BEGIN  
"#include ""res\myapp.rc2""  // non-Visual C++ edited resources\r\n"  
"\r\n"  
"#include ""afxres.rc""  // Standard components\r\n"  
"#include ""afxprint.rc""  // printing/print preview resources\r\n"  
"\0"  
END  
```  
  
## <a name="see-also"></a>另请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

