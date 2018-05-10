---
title: 受资源编辑文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [Visual Studio], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb103ac098c8d73db132cdb67b6ab6902ee3f591
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="files-affected-by-resource-editing"></a>受资源编辑影响的文件
在资源编辑会话期间，Visual Studio 环境使用下表中显示的文件。  
  
|文件名|描述|  
|---------------|-----------------|  
|Resource.h|由开发环境生成的头文件；包含符号定义。|  
|Filename.aps|当前资源脚本文件的二进制版本；用于快速加载。<br /><br /> 资源编辑器不直接读取 .rc 或 resource.h 文件。 资源编译器将它们编译成由资源编辑器使用的 .aps 文件。 该文件是一个编译步骤，只存储符号数据。 与普通编译过程一样，非符号信息（如注释）在编译过程中将被放弃。 每当 .aps 文件与 .rc 文件不同步时，就会重新生成 .rc 文件（例如，当你进行“保存”时，资源编辑器将覆盖 .rc 文件和 resource.h 文件）。 对资源本身所做的任何更改依然包含在 .rc 文件中，但一旦覆盖 .rc 文件就总会丢失注释。 有关如何保留注释的信息，请参阅[在编译时包括资源](../windows/how-to-include-resources-at-compile-time.md)。|  
|.rc|包含当前项目中的资源脚本的资源脚本文件。 每当进行保存时，.aps 文件就会覆盖此文件。|  
  

  
## <a name="requirements"></a>要求  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [资源文件](../windows/resource-files-visual-studio.md)