---
title: "建议的文档注释 （Visual c + +） 标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5c1b0e762ec2167a988e8e18f3dce932214716c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>建议用于文档注释的标记 (Visual C++)
Visual c + + 编译器将在代码中的文档注释处理和创建.xdc 文件以供每个编译单位，以及如何 xdcmake.exe 将处理到一个.xml 文件则.xdc 文件。 处理要创建文档的.xml 文件是需要在你的站点实现了详细信息。  
  
 处理在构造，如类型和类型成员的标记。  
  
 标记必须紧跟类型或成员。  
  
> [!NOTE]
>  文档注释不能应用到命名空间或在超出行定义的属性和事件;文档注释必须在类中声明上。  
  
 编译器将处理属于有效 XML 形式的任何标记。 以下标记提供用户文档中的常用的功能：  
  
||||  
|-|-|-|  
|[\<c>](../ide/c-visual-cpp.md)|[\<code>](../ide/code-visual-cpp.md)|[\<example>](../ide/example-visual-cpp.md)|  
|[\<异常 >](../ide/exception-visual-cpp.md)1|[\<包括 >](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|  
|[\<para>](../ide/para-visual-cpp.md)|[\<param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|  
|[\<权限 >](../ide/permission-visual-cpp.md)1|[\<remarks>](../ide/remarks-visual-cpp.md)|[\<returns>](../ide/returns-visual-cpp.md)|  
|[\<请参阅 >](../ide/see-visual-cpp.md)1|[\<另请参阅 >](../ide/seealso-visual-cpp.md)1|[\<summary>](../ide/summary-visual-cpp.md)|  
|[\<value>](../ide/value-visual-cpp.md)|||  
  
 1. 编译器将验证语法。  
  
 在当前版本中，Visual c + + 编译器不支持`<paramref>`，其他 Visual Studio 编译器支持的标记。 Visual c + + 可能支持`<paramref>`的未来版本中。  
  
## <a name="see-also"></a>请参阅  
 [XML 文档](../ide/xml-documentation-visual-cpp.md)