---
title: "静态库 (C + + /cli CX) |Microsoft 文档"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7a64e1f35350968f16a24a46b8611820d68bf785
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="static-libraries-ccx"></a>静态库 (C++/CX)
在通用 Windows 平台 (UWP) 应用程序中使用的静态库可包含 ISO 标准 c + + 代码，包括 STL 类型，同时还未排除的 Windows 运行时应用程序平台的 Win32 api 的调用。 静态库使用 Windows 运行时组件，并可能创建具有某些限制的 Windows 运行时组件。  
  
## <a name="creating-static-libraries"></a>创建静态库  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>若要在 UWP 应用中创建使用静态库  
  
1.  在菜单栏上，依次选择“文件” > “新建” > “项目”。 下**Visual c + +** > **Windows 通用**选择**静态库 (通用 Windows)**。  
  
2.  在“解决方案资源管理器” 中，打开项目的快捷菜单，然后选择“属性” 。 在**属性**对话框中，在**配置属性** > **C/c + +**页上，设置**使用 Windows 运行时扩展**到**是 (/ZW)**。  
  
 如果不对此适用于 UWP 应用的 Win32 api 调用，新的静态库，编译时，编译器将引发错误 C3861"找不到标识符"。 若要查看适用于 Windows 运行时的替代方法，请参阅[UWP 应用中的 Windows Api 的替代项](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。  
  
 如果将 c + + 静态库项目添加到 UWP 应用程序解决方案，你可能必须更新该库项目的属性设置，以便 UWP 支持属性设置为**是**。 没有此设置，代码将生成，当你尝试验证该应用程序的 Microsoft 应用商店链接，但是错误时发生。 编译静态库时的编译器设置应与使用该库的项目的编译器设置相同。  
  
 如果使用创建公共 `ref` 类、公共接口类或公共值类的静态库，则链接器会引发此警告：  
  
> **警告 LNK4264:**存档对象文件使用 /ZW 编译到静态库中; 请注意，创建 Windows 运行时类型时建议不要与包含 Windows 运行时元数据的静态库链接。  
  
 仅当静态库不生成在库自身之外被使用的 Windows 运行时组件，你可以放心地忽略该警告。 如果该库不使用其定义的组件，则链接器可通过优化去除实现，即使公共元数据包含类型信息，情况也不例外。 这意味着，静态库中的公共组件将进行编译，但不会在运行时激活。 为此，必须在动态链接库 (DLL) 中实现供其他组件或应用程序使用任何 Windows 运行时组件。  
  
## <a name="see-also"></a>请参阅  
 [线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)