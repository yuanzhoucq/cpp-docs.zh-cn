---
title: 符号： 资源标识符 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols, resource identifiers
- symbols, creating
- resource symbols
- symbols, editing
- resource editors, resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c049aa192aeb253641ab473e5675b1ee5bd685a6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891839"
---
# <a name="symbols-resource-identifiers"></a>符号：资源标识符
符号是由两部分组成的资源标识符 (ID)：一个文本字符串（符号名）与一个整数值（符号值）映射。 例如：  
  
```  
IDC_EDITNAME = 5100  
```  
  
 符号名通常称为标识符。  
  
 在资源编辑器中处理时，符号会在源代码中提供说明性方法来引用资源和用户界面对象。 可以使用 [资源符号对话框](../windows/viewing-resource-symbols.md)在一个方便的位置查看和操作符号。  
  
 创建新资源或资源对象时， [资源编辑器](../windows/resource-editors.md) 会提供资源的默认名称，例如 `IDC_RADIO1`，并向它分配一个值。 这种名称加值的定义存储在 Resource.h 文件中。  
  
> [!NOTE]
>  从一个.rc 文件向另一个复制资源或资源对象时，Visual C++ 可更改传输资源的符号值，或同时更改符号名和符号值，以避免与现有文件中的符号名或符号值发生冲突。  
  
 随着应用程序大小和复杂度的增长，资源和符号的数量也随之增加。 跟踪分散在多个文件中的大量符号就变得尤为困难。 [资源符号对话框](../windows/resource-symbols-dialog-box.md) 可通过提供一个中心工具来简化符号管理，使用该工具可执行以下操作：  
  
- [查看资源符号](../windows/viewing-resource-symbols.md)  
  
- [创建新符号](../windows/creating-new-symbols.md)  
  
- [更改未赋值符号](../windows/changing-unassigned-symbols.md)  
  
- [删除未赋值符号](../windows/deleting-unassigned-symbols.md)  
  
- [打开给定符号的资源编辑器](../windows/opening-the-resource-editor-for-a-given-symbol.md)  
  
- [更改符号或符号名 (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)  
  
- [更改符号的数字值](../windows/changing-a-symbol-s-numeric-value.md)  
  
- [更改符号头文件的名称](../windows/changing-the-names-of-symbol-header-files.md)  
  
- [包含共享（只读）或计算符号](../windows/including-shared-read-only-or-calculated-symbols.md)  
  
- [查看预定义的符号 ID](../windows/predefined-symbol-ids.md)  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 搜索资源中的符号](../windows/how-to-search-for-symbols-in-resources.md)   
 [资源编辑器](../windows/resource-editors.md)   
 [资源文件](../windows/resource-files-visual-studio.md)

