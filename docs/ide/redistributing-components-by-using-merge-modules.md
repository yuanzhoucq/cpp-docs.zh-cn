---
title: 使用合并模块重新发布组件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- merge modules, using
- redistributing applications, using merge modules
ms.assetid: 93b84211-bf9b-4a78-9f22-474ac2ef7840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d95b6d2a69b4b40c4464136dd33a8c5231185f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-components-by-using-merge-modules"></a>使用合并模块重新发布组件
Visual Studio 包含[的合并模块](http://msdn.microsoft.com/library/aa367434)为每个已获许可与应用程序一起重新分发的 Visual c + + 组件。 合并模块在 Windows Installer 安装文件中编译后，便可以将特定的 DLL 部署到具有特定平台的计算机。 在你的安装文件中，请指定合并模块是应用程序的先决条件。 安装 Visual Studio 后，合并模块将安装在 \program Files\Merge 模块\\。 （仅非调试版本的 Visual c + + Dll 可能一起重新分发。）有关详细信息和链接以进行重新分发许可的合并模块的列表，请参阅[重新分发 Visual c + + 文件](../ide/redistributing-visual-cpp-files.md)。  
  
 可以使用合并模块将可再发行 Visual c + + dll 安装到 %SYSTEMROOT%\system32\ 文件夹。 （visual Studio 本身使用此方法。）但是，安装的用户必须具有管理员权限才能成功安装到该文件夹。  
  
 除非你不必为应用程序提供服务并且不依赖于一个以上的 DLL 版本，否则我们建议你不要使用合并模块。 同一 DLL 的不同版本的合并模块不能包含在一个安装程序中，而且合并模块使你难以独立于应用程序为 DLL 服务。 相反，我们建议你安装 Visual c + + 可再发行组件包。  
  
## <a name="see-also"></a>请参阅  
 [重新分发 Visual C++ 文件](../ide/redistributing-visual-cpp-files.md)