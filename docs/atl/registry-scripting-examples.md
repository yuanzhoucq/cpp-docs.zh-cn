---
title: 注册表脚本示例 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eabb923b165d407f77554d88d710cd7c67a14240
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022106"
---
# <a name="registry-scripting-examples"></a>注册表脚本示例

本主题中的脚本示例演示如何将密钥添加到系统注册表，注册注册机构 COM 服务器，并指定多个分析树。

## <a name="add-a-key-to-hkeycurrentuser"></a>将密钥添加到 HKEY_CURRENT_USER

以下的分析树说明了一个简单的脚本，将单个密钥添加到系统注册表。 具体而言，该脚本会添加密钥，`MyVeryOwnKey`到`HKEY_CURRENT_USER`。 它还将分配的默认字符串值`HowGoesIt`为使用新密钥：

```
HKEY_CURRENT_USER
{  
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

此脚本可以轻松地扩展来定义多个子项，如下所示：

```
HKCU
{  
    'MyVeryOwnKey' = s 'HowGoesIt'  
    {  
        'HasASubkey'  
        {  
            'PrettyCool' = d '55'  
            val 'ANameValue' = s 'WithANamedValue'  
        }  
    }
}
```

现在，该脚本会添加一个子项`HasASubkey`到`MyVeryOwnKey`。 此子项，它将添加到这两`PrettyCool`子项 (默认值`DWORD`值为 55) 和`ANameValue`命名的值 (字符串值为`WithANamedValue`)。

##  <a name="_atl_register_the_registrar_com_server"></a> 注册注册机构 COM 服务器

以下脚本注册注册机构 COM 服务器本身。

```
HKCR
{  
    ATL.Registrar = s 'ATL Registrar Class'  
    {  
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
    }  
    NoRemove CLSID  
    {  
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'  
        {  
            ProgID = s 'ATL.Registrar'  
            InprocServer32 = s '%MODULE%'  
            {  
                val ThreadingModel = s 'Apartment'  
            }  
        }  
    }
}
```

在运行时，此分析树添加`ATL.Registrar`关键`HKEY_CLASSES_ROOT`。 此新注册表项，然后 it:

- 指定`ATL Registrar Class`作为键的默认字符串值。

- 添加`CLSID`作为子项。

- 指定`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`为`CLSID`。 (此值是注册机构的用于 CLSID `CoCreateInstance`。)

由于`CLSID`是共享的它不应删除中取消注册模式。 该语句中， `NoRemove CLSID`，指示为此目的`CLSID`应在注册模式下打开并在注销模式被忽略。

`ForceRemove`语句提供了一个内部管理功能，通过删除然后重新创建该密钥的密钥及其所有子项。 这可以是子项的名称已更改的情况下很有用。 在此脚本示例中，`ForceRemove`检查是否`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`已存在。 如果是这样， `ForceRemove`:

- 以递归方式删除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`和所有子项。

- 重新创建`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

- 将添加`ATL Registrar Class`的默认字符串值作为`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

分析树现在将添加到两个新子项`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。 第一个键， `ProgID`，获取该 progid 的默认字符串值。 第二个密钥， `InprocServer32`，获取默认字符串值， `%MODULE%`，即预处理器值部分所述，[使用可替换参数 （注册机构的预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)，这篇文章。 `InprocServer32` 此外可获取已命名的值`ThreadingModel`，使用的字符串值`Apartment`。

## <a name="specify-multiple-parse-trees"></a>指定多个分析树

若要在脚本中指定多个分析树，只需将一个树放在另一端。 例如，以下脚本添加密钥， `MyVeryOwnKey`，为两个分析树`HKEY_CLASSES_ROOT`和`HKEY_CURRENT_USER`:

```
HKCR
{  
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{  
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> 在注册器脚本中，4 K 是令牌的最大大小。 （令牌是在语法中任何可识别的元素。）在前面的脚本示例`HKCR`， `HKEY_CURRENT_USER`， `'MyVeryOwnKey'`，和`'HowGoesIt'`是所有令牌。

## <a name="see-also"></a>请参阅

[创建注册器脚本](../atl/creating-registrar-scripts.md)

