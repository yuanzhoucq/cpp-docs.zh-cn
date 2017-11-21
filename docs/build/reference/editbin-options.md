---
title: "EDITBIN 选项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: editbin
dev_langs: C++
helpviewer_keywords: EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5a4b30b5fdc3294220b210001cc19a58bdf4b3b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="editbin-options"></a>EDITBIN 选项
EDITBIN 可用于修改对象文件、 可执行文件和动态链接库 (Dll)。 选项指定 EDITBIN 做的更改。  
  
 选项包括选项说明符，它是短划线 （-） 或正斜杠 （/） 后, 跟选项的名称。 选项名不能缩写。 某些选项带参数，参数在冒号 (:) 后指定。 中的选项规范所允许空格或制表符。 使用一个或多个空格或制表符分隔命令行上的选项规范。 选项名及其关键字参数或文件名参数不区分大小写。 例如，-bind 和 /BIND 意义完全相同。  
  
 EDITBIN 还拥有以下选项：  
  
|选项|用途|  
|------------|-------------|  
|[/ALLOWBIND](../../build/reference/allowbind.md)|指定一个 DLL 是否可以绑定。|  
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|指定 DLL 或可执行文件清单查找行为。|  
|[/APPCONTAINER](../../build/reference/appcontainer.md)|指定应用是否必须在 AppContainer 内运行，例如 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]应用。|  
|[/ 绑定](../../build/reference/bind.md)|将指定对象中的入口点地址设为速度加载时间。|  
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|使用地址空间布局随机化 (ASLR) 功能，指定是否可在加载时随机变基 DLL 或可执行映像。|  
|[/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|向 Microsoft 报告内部错误。|  
|[/ 堆](../../build/reference/heap.md)|以字节设置可执行映像堆的大小。|  
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|指定 DLL 或可执行映像是否支持高熵（64 位）地址空间布局随机化 (ASLR)。|  
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|指定是否在加载时检查数字签名。|  
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|指定对象是否支持大于 2 GB 的地址。|  
|[/NOLOGO](../../build/reference/nologo-editbin.md)|取消显示 EDITBIN 启动横幅。|  
|[/NXCOMPAT](../../build/reference/nxcompat.md)|指定可执行映像是否与 Windows 数据执行保护兼容。|  
|[/REBASE](../../build/reference/rebase.md)|设置指定对象的基址。|  
|[/ 发行版](../../build/reference/release.md)|在标头中设置校验和。|  
|[/ 部分](../../build/reference/section-editbin.md)|重写节的特性。|  
|[/ 堆栈](../../build/reference/stack.md)|以字节设置可执行映像栈的大小。|  
|[/ 子系统](../../build/reference/subsystem.md)|指定执行环境。|  
|[/SWAPRUN](../../build/reference/swaprun.md)|指定可执行映像必须复制到交换文件，然后从其中运行。|  
|[/TSAWARE](../../build/reference/tsaware.md)|指定应用可在多用户环境中运行。|  
|[/ 版本](../../build/reference/version.md)|在标头中设置版本号。|  
  
## <a name="see-also"></a>另请参阅  
 [C/c + + 生成工具](../../build/reference/c-cpp-build-tools.md)   
 [EDITBIN 参考](../../build/reference/editbin-reference.md)