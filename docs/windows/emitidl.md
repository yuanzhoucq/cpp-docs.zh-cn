---
title: "emitidl |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.emitidl
dev_langs:
- C++
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 55fc74eef3d2ead7312f7dca46f20c3a1ed7ba91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="emitidl"></a>emitidl
指定是否所有后续的 IDL 特性进行处理，并在生成的.idl 文件中放入。  
  
## <a name="syntax"></a>语法  
  
```
[ emitidl(state, defaultimports=boolean) ];
```  
  
### <a name="parameters"></a>参数  
*state*  
这些可能的值之一： **true**， **false**，**强制**，**受限**，**推送**，或**pop**。  
  
-   如果**true**，在源代码文件中遇到任何 IDL 类别属性放置在生成的.idl 文件。 这是默认设置**emitidl**。  
  
-   如果**false**，在源代码文件中遇到任何 IDL 类别属性不在生成的.idl 文件。  
  
-   如果**受限**，允许 IDL 特性，要在文件中，而没有[模块](../windows/module-cpp.md)属性。 编译器不生成.idl 文件。  
  
-   如果**强制**，重写后续**受限**特性，这要求文件具有**模块**属性是否存在 IDL 特性在文件中。  
  
-   **推送**允许您将保存当前**emitidl**设置应用于内部**emitidl**堆栈，和**pop**允许你将**emitidl**到任何值是在内部顶部**emitidl**堆栈。  
  
`defaultimports=`*布尔*\(可选)  
-   如果*布尔*是**true**，docobj.idl 导入到生成的.idl 文件。 此外，如果.idl 文件具有相同名称作为.h 文件`#include`到您的源的代码位于与.h 文件中，相同的目录，则生成的.idl 文件包含该.idl 文件的导入语句。  
  
-   如果*布尔*是**false**，docobj.idl 不导入到生成的.idl 文件。 必须显式导入具有.idl 文件[导入](../windows/import.md)。  
  
## <a name="remarks"></a>备注  
后**emitidl**源代码文件中遇到 c + + 属性、 IDL 类别特性都放在生成的.idl 文件。 如果没有任何**emitidl**属性，在源代码文件中的 IDL 特性是输出到生成的.idl 文件。  
  
可以有多个**emitidl**源代码文件中的属性。 如果`[emitidl(false)];`在无后续的文件中遇到`[emitidl(true)];`，则没有属性处理到生成的.idl 文件。  
  
编译器遇到新的文件，每次**emitidl**隐式设置为**true**。  
  
## <a name="requirements"></a>惠?  
  
### <a name="attribute-context"></a>特性上下文  
  
|||  
|-|-|  
|**适用对象**|任何位置|  
|**可重复**|否|  
|**必需的特性**|无|  
|**无效的特性**|无|  
  
有关详细信息，请参见 [特性上下文](../windows/attribute-contexts.md)。  
  
## <a name="see-also"></a>请参阅  
[编译器特性](../windows/compiler-attributes.md)   
[独立特性](../windows/stand-alone-attributes.md)   
[属性示例](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)