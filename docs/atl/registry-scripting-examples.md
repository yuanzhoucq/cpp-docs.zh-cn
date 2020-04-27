---
title: 注册表脚本示例
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168743"
---
# <a name="registry-scripting-examples"></a>注册表脚本示例

本主题中的脚本示例演示了如何将密钥添加到系统注册表，如何注册注册器 COM 服务器，以及如何指定多个分析树。

## <a name="add-a-key-to-hkey_current_user"></a>向 HKEY_CURRENT_USER 添加密钥

以下分析树说明了一个简单的脚本，该脚本将一个键添加到系统注册表中。 具体而言，该脚本会将项`MyVeryOwnKey`添加到。 `HKEY_CURRENT_USER` 它还将的`HowGoesIt`默认字符串值分配给新密钥：

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

可以轻松扩展此脚本以定义多个子项，如下所示：

```rgs
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

现在，该脚本会将子项`HasASubkey`添加到。 `MyVeryOwnKey` 此`PrettyCool`子项添加了子项（默认`DWORD`值为55）和`ANameValue`命名值（字符串值为`WithANamedValue`）。

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>注册注册机构 COM 服务器

下面的脚本注册注册器 COM 服务器本身。

```rgs
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

在运行时，此分析树将`ATL.Registrar`键添加到`HKEY_CLASSES_ROOT`中。 为此新密钥，则：

- 指定`ATL Registrar Class`为键的默认字符串值。

- 添加`CLSID`为子项。

- 为`{44EC053A-400F-11D0-9DCD-00A0C90391D3}` `CLSID`指定。 （此值是用于的注册器 CLSID `CoCreateInstance`。）

由于`CLSID`是共享的，因此不应在取消注册模式下将其删除。 语句`NoRemove CLSID`通过指示`CLSID`应在注册模式下打开并在取消注册模式中忽略，来执行此。

`ForceRemove`语句提供了一项内务处理功能，方法是在重新创建密钥之前删除密钥及其所有子项。 如果子项的名称已更改，这会很有用。 在此脚本示例中`ForceRemove` ，将检查以`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`确定是否已存在。 如果是， `ForceRemove`则：

- 递归删除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`及其所有子项。

- 重新创建`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

- 添加`ATL Registrar Class`为的默认字符串值`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

分析树现在将两个新子项添加`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`到中。 第一个键`ProgID`获取作为 ProgID 的默认字符串值。 第二个键`InprocServer32`获取默认字符串值`%MODULE%`，它是本文的使用可[替换参数（注册器的预处理器）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)一节中介绍的预处理器值。 `InprocServer32`还获取一个具有字符串值`ThreadingModel`的`Apartment`命名值。

## <a name="specify-multiple-parse-trees"></a>指定多个分析树

若要在一个脚本中指定多个分析树，只需将一个树置于另一个树的末尾即可。 例如，下面的脚本将键`MyVeryOwnKey`添加到`HKEY_CLASSES_ROOT`和`HKEY_CURRENT_USER`的分析树中：

```rgs
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
> 在注册器脚本中，4K 是最大标记大小。 （标记是语法中的任何可识别元素。）`HKCR`在上面的脚本示例`HKEY_CURRENT_USER` `'MyVeryOwnKey'`中，、、和`'HowGoesIt'`都是标记。

## <a name="see-also"></a>另请参阅

[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
