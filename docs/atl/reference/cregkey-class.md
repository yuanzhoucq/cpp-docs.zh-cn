---
title: CRegKey 类
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: d3bdb2e7c3ab0ef56ef7f6fba5d43f1ba0bb7fc6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746520"
---
# <a name="cregkey-class"></a>CRegKey 类

此类提供用于操作系统注册表中的条目的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CRegKey
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CRegKey：CRegKey](#cregkey)|构造函数。|
|[CRegKey：*CRegKey](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRegKey：：附加](#attach)|调用此方法通过将[m_hKey](#m_hkey)成员句柄设置为 将`hKey``CRegKey`HKEY 附加到对象。|
|[CRegKey：关闭](#close)|调用此方法以释放[m_hKey](#m_hkey)成员句柄并将其设置为 NULL。|
|[CRegKey：创建](#create)|调用此方法以创建指定的密钥（如果该键不存在为`hKeyParent`的子键）。|
|[CRegKey：:DeleteSubKey](#deletesubkey)|调用此方法从注册表中删除指定的密钥。|
|[CRegKey：:Delete价值](#deletevalue)|调用此方法从[m_hKey](#m_hkey)中删除值字段。|
|[CRegKey：:D埃塔奇](#detach)|调用此方法以将[m_hKey](#m_hkey)成员句柄从对象中分离出来，`CRegKey`并设置为`m_hKey`NULL。|
|[CregKey：：枚举键](#enumkey)|调用此方法以枚举打开注册表项的子键。|
|[CRegKey：：冲洗](#flush)|调用此方法将打开注册表项的所有属性写入注册表。|
|[CRegKey：获取密钥安全](#getkeysecurity)|调用此方法以检索保护打开注册表项的安全描述符的副本。|
|[CRegKey：：通知更改键值](#notifychangekeyvalue)|此方法通知调用方对打开注册表项的属性或内容的更改。|
|[CRegKey：：打开](#open)|调用此方法以打开指定的密钥并将[m_hKey](#m_hkey)设置为此密钥的句柄。|
|[CRegKey：：查询二元值](#querybinaryvalue)|调用此方法以检索指定值名称的二进制数据。|
|[CregKey：：查询DWORD值](#querydwordvalue)|调用此方法以检索指定值名称的 DWORD 数据。|
|[CregKey：：查询GUID值](#queryguidvalue)|调用此方法以检索指定值名称的 GUID 数据。|
|[CregKey：：查询多字符串值](#querymultistringvalue)|调用此方法以检索指定值名称的多字符串数据。|
|[CregKey：：查询QWORD值](#queryqwordvalue)|调用此方法以检索指定值名称的 QWORD 数据。|
|[CRegKey：：查询字符串值](#querystringvalue)|调用此方法以检索指定值名称的字符串数据。|
|[CRegKey：：查询值](#queryvalue)|调用此方法以检索[m_hKey](#m_hkey)的指定值字段的数据。 此方法的早期版本不再受支持，并标记为ATL_DEPRECATED。|
|[CRegKey：：重新诅咒删除密钥](#recursedeletekey)|调用此方法从注册表中删除指定的密钥，并显式删除任何子键。|
|[CRegKey：：设置Binary值](#setbinaryvalue)|调用此方法以设置注册表项的二进制值。|
|[CregKey：：设置DWORD值](#setdwordvalue)|调用此方法以设置注册表项的 DWORD 值。|
|[CRegKey：：SetGUID值](#setguidvalue)|调用此方法以设置注册表项的 GUID 值。|
|[CRegKey：：设置密钥安全性](#setkeysecurity)|调用此方法以设置注册表项的安全性。|
|[CRegKey：：设置键值](#setkeyvalue)|调用此方法将数据存储在指定密钥的指定值字段中。|
|[CRegKey：：设置多字符串值](#setmultistringvalue)|调用此方法以设置注册表项的多字符串值。|
|[CRegKey：：设置QWORD值](#setqwordvalue)|调用此方法以设置注册表项的 QWORD 值。|
|[CRegKey：：设置字符串值](#setstringvalue)|调用此方法以设置注册表项的字符串值。|
|[CRegKey：：设置价值](#setvalue)|调用此方法将数据存储在指定的值字段中[m_hKey](#m_hkey)。 此方法的早期版本不再受支持，并标记为ATL_DEPRECATED。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CRegKey：：操作员HKEY](#operator_hkey)|将`CRegKey`对象转换为 HKEY。|
|[CRegKey：：运算符 |](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CRegKey：m_hKey](#m_hkey)|包含与对象关联的注册表项的`CRegKey`句柄。|
|[CRegKey：m_pTM](#m_ptm)|指向`CAtlTransactionManager`对象的指针|

## <a name="remarks"></a>备注

`CRegKey`提供了在系统注册表中创建和删除键和值的方法。 注册表包含系统组件的特定于安装的定义集，例如软件版本号、已安装硬件的逻辑到物理映射以及 COM 对象。

`CRegKey`为给定的计算机提供到系统注册表的编程接口。 例如，要打开特定的注册表项，请调用`CRegKey::Open`。 要检索或修改数据值，请分别`CRegKey::QueryValue`调用`CRegKey::SetValue`或 。 要关闭密钥，请调用`CRegKey::Close`。

关闭密钥时，其注册表数据将写入（刷新）到硬盘。 该过程需要持续数秒。 如果应用程序必须显式将注册表数据写入硬盘，则可以调用[RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32 函数。 但是，`RegFlushKey`使用许多系统资源，并且仅在绝对必要时才应调用。

> [!IMPORTANT]
> 允许调用方指定注册表位置的任何方法都有可能读取无法信任的数据。 使用[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)的方法应考虑此函数不显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CRegKey：：附加

调用此方法通过将`CRegKey`[m_hKey](#m_hkey)成员句柄设置为*hKey*将 HKEY 附加到对象。

```cpp
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>参数

*h键*<br/>
注册表项的句柄。

### <a name="remarks"></a>备注

`Attach`将断言如果`m_hKey`为非 NULL。

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey：关闭

调用此方法以释放[m_hKey](#m_hkey)成员句柄并将其设置为 NULL。

```
LONG Close() throw();
```

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS;否则返回错误值。

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey：创建

调用此方法以创建指定的密钥（如果它不存在为*hKeyParent*的子键）。

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>参数

*hKey父*<br/>
打开键的句柄。

*lpszKey名称*<br/>
指定要创建或打开的键的名称。 此名称必须是*hKeyParent*的子键。

*lpszClass*<br/>
指定要创建或打开的键的类。 默认值为REG_NONE。

*dwOptions*<br/>
键的选项。 默认值为REG_OPTION_NON_VOLATILE。 有关可能的值和说明的列表，请参阅 Windows SDK 中的[RegCreateKeyEx。](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw)

*萨姆·阿乔*<br/>
密钥的安全访问。 默认值为KEY_READ&#124;KEY_WRITE。 有关可能的值和说明的列表，请参阅`RegCreateKeyEx`。

*lpSecattr*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针，指示密钥的句柄是否可以由子进程继承。 默认情况下，此参数为 NULL（表示无法继承句柄）。

*lpdw 处理*<br/>
[出]如果非 NULL，则检索REG_CREATED_NEW_KEY（如果密钥不存在并创建）或REG_OPENED_EXISTING_KEY（如果密钥存在且已打开）。

### <a name="return-value"></a>返回值

如果成功，返回ERROR_SUCCESS并打开密钥。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

`Create`将[m_hKey](#m_hkey)成员设置为此键的句柄。

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey：CRegKey

构造函数。

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
对 `CRegKey` 对象的引用。

*h键*<br/>
注册表项的句柄。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

创建新的 `CRegKey` 对象。 可以从现有`CRegKey`对象或从句柄创建对象，也可以从注册表项创建对象。

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey：*CRegKey

析构函数。

```
~CRegKey() throw();
```

### <a name="remarks"></a>备注

析构函数释放`m_hKey`。

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey：:DeleteSubKey

调用此方法从注册表中删除指定的密钥。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>参数

*lpszSubkey*<br/>
指定要删除的键的名称。 此名称必须是[m_hKey](#m_hkey)的子键。

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

`DeleteSubKey`只能删除没有子键的密钥。 如果密钥具有子键，请改为调用["重新诅咒删除密钥](#recursedeletekey)"。

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey：:Delete价值

调用此方法从[m_hKey](#m_hkey)中删除值字段。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>参数

*lpszValue*<br/>
指定要删除的值字段。

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey：:D埃塔奇

调用此方法以将[m_hKey](#m_hkey)成员句柄从对象中分离出来，`CRegKey`并设置为`m_hKey`NULL。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>返回值

与`CRegKey`对象关联的 HKEY。

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CregKey：：枚举键

调用此方法以枚举打开注册表项的子键。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>参数

*iIndex*<br/>
子键索引。 此参数对于第一个调用应为零，然后为后续调用递增

*pszName*<br/>
指向接收子键名称（包括终止空字符）的缓冲区的指针。 只有子键的名称复制到缓冲区，而不是完整键层次结构。

*pn名称长度*<br/>
指向指定*pszName*参数指定的缓冲区的大小（在 TCHAR 中）的变量的指针。 此大小应包括终止空字符。 当方法返回时 *，pnNameLength*指向的变量包含存储在缓冲区中的字符数。 返回的计数不包括终止空字符。

*pftLast 写入时间*<br/>
指向接收上次写入枚举子键时间的变量的指针。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

要枚举子键，请`CRegKey::EnumKey`调用索引为零。 增加索引值并重复，直到方法返回ERROR_NO_MORE_ITEMS。 有关详细信息，请参阅 Windows SDK 中的[RegEnumKeyEx。](/windows/win32/api/winreg/nf-winreg-regenumkeyexw)

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey：：冲洗

调用此方法将打开注册表项的所有属性写入注册表。

```
LONG Flush() throw();
```

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

有关详细信息，请参阅 Windows SDK 中的[RegEnumFlush。](/windows/win32/api/winreg/nf-winreg-regflushkey)

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CRegKey：获取密钥安全

调用此方法以检索保护打开注册表项的安全描述符的副本。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>参数

*四*<br/>
指示请求的安全信息[的SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)值。

*Psd*<br/>
指向接收请求的安全描述符副本的缓冲区的指针。

*pn字节*<br/>
以字节为单位的缓冲区的大小（以字节为单位）指向*sd*。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值为非零错误代码，在 WINERROR 中定义。H。

### <a name="remarks"></a>备注

有关详细信息，请参阅[RegGetKey 安全](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity)。

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey：m_hKey

包含与对象关联的注册表项的`CRegKey`句柄。

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey：m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CRegKey：：通知更改键值

此方法通知调用方对打开注册表项的属性或内容的更改。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>参数

*b观察子树*<br/>
指定指示是报告指定密钥及其所有子键中的更改的标志，还是仅在指定键中报告更改。 如果此参数为 TRUE，则该方法将报告键及其子键中的更改。 如果参数为 FALSE，则方法仅报告键中的更改。

*dwNotifyFilter*<br/>
指定一组标志，用于控制应报告哪些更改。 此参数可以是以下值的组合：

|“值”|含义|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|如果添加或删除子键，则通知调用方。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知调用方对密钥属性的更改，例如安全描述符信息。|
|REG_NOTIFY_CHANGE_LAST_SET|通知调用方对密钥值的更改。 这可能包括添加或删除值，或更改现有值。|
|REG_NOTIFY_CHANGE_SECURITY|通知调用方密钥的安全描述符的更改。|

*hEvent*<br/>
事件的句柄。 如果*bAsync*参数为 TRUE，则该方法会立即返回，并通过向此事件发出信号来报告更改。 如果*bAsync*为 FALSE，则忽略*hEvent。*

*bAsync*<br/>
指定指示方法报告方式更改的标志。 如果此参数为 TRUE，则该方法会立即返回，并通过向指定事件发出信号来报告更改。 当此参数为 FALSE 时，该方法在发生更改之前不会返回。 如果*hEvent*未指定有效事件，*则 bAsync*参数不能为 TRUE。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

> [!NOTE]
> 如果删除了指定的密钥，此方法不会通知调用方。

有关详细信息和示例程序，请参阅[RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue)。

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey：：打开

调用此方法以打开指定的密钥并将[m_hKey](#m_hkey)设置为此密钥的句柄。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>参数

*hKey父*<br/>
打开键的句柄。

*lpszKey名称*<br/>
指定要创建或打开的键的名称。 此名称必须是*hKeyParent*的子键。

*萨姆·阿乔*<br/>
密钥的安全访问。 默认值为KEY_ALL_ACCESS。 有关可能的值和说明的列表，请参阅 Windows SDK 中的[RegCreateKeyEx。](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw)

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS;否则，在 WINERROR 中定义的非零错误值。H。

### <a name="remarks"></a>备注

如果*lpszKeyName*参数为 NULL 或指向空字符串`Open`，则打开*hKeyParent*标识的键的新句柄，但不会关闭任何以前打开的句柄。

与[CRegKey：：create](#create)不同，`Open`如果不存在，将不会创建指定的密钥。

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey：：操作员HKEY

将`CRegKey`对象转换为 HKEY。

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey：：运算符 |

赋值运算符。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>参数

*键*<br/>
要复制的键。

### <a name="return-value"></a>返回值

返回对新键的引用。

### <a name="remarks"></a>备注

此运算符从其当前对象分离*密钥*，并将其分配给`CRegKey`对象。

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CRegKey：：查询二元值

调用此方法以检索指定值名称的二进制数据。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。

*pValue*<br/>
指向接收值数据的缓冲区的指针。

*pn字节*<br/>
指向指定*pValue*参数指向的缓冲区的大小（以字节为单位）的变量的指针。 当方法返回时，此变量包含复制到缓冲区的数据的大小。

### <a name="return-value"></a>返回值

如果该方法成功，将返回ERROR_SUCCESS。 如果方法无法读取值，它将返回在 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是REG_BINARY类型，则返回ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`并确认返回正确的数据类型。 有关详细信息[，请参阅 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。 此外，此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不会显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CregKey：：查询DWORD值

调用此方法以检索指定值名称的 DWORD 数据。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。

*dwValue*<br/>
指向接收 DWORD 的缓冲区的指针。

### <a name="return-value"></a>返回值

如果该方法成功，将返回ERROR_SUCCESS。 如果方法无法读取值，它将返回在 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是REG_DWORD类型，则返回ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`并确认返回正确的数据类型。 有关详细信息[，请参阅 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。 此外，此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不会显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>CregKey：：查询GUID值

调用此方法以检索指定值名称的 GUID 数据。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。

*吉德价值*<br/>
指向接收 GUID 的变量的指针。

### <a name="return-value"></a>返回值

如果该方法成功，将返回ERROR_SUCCESS。 如果方法无法读取值，它将返回在 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是有效的 GUID，则返回ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`CRegKey::QueryStringValue`[CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)使用字符串并将其转换为 GUID。

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CregKey：：查询多字符串值

调用此方法以检索指定值名称的多字符串数据。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。

*pszValue*<br/>
指向接收多字符串数据的缓冲区的指针。 多字符串是 null 终止字符串的数组，由两个空字符终止。

*pnChars*<br/>
以 TCHAR 表示的缓冲区的大小（以 TR 形式）指向*pszValue*。 当方法返回时 *，pnChars*包含检索的多字符串（包括终止空字符）的大小（在 TCHA 中）。

### <a name="return-value"></a>返回值

如果该方法成功，将返回ERROR_SUCCESS。 如果方法无法读取值，它将返回在 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是REG_MULTI_SZ类型，则返回ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`并确认返回正确的数据类型。 有关详细信息[，请参阅 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。 此外，此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不会显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CregKey：：查询QWORD值

调用此方法以检索指定值名称的 QWORD 数据。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。

*qwValue*<br/>
指向接收 QWORD 的缓冲区的指针。

### <a name="return-value"></a>返回值

如果该方法成功，将返回ERROR_SUCCESS。 如果方法无法读取值，它将返回在 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是REG_QWORD类型，则返回ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`并确认返回正确的数据类型。 有关详细信息[，请参阅 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。 此外，此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不会显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CRegKey：：查询字符串值

调用此方法以检索指定值名称的字符串数据。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。

*pszValue*<br/>
指向接收字符串数据的缓冲区的指针。

*pnChars*<br/>
以 TCHAR 表示的缓冲区的大小（以 TR 形式）指向*pszValue*。 当方法返回时 *，pnChars*包含检索的字符串的大小（TCHAR），包括终止空字符。

### <a name="return-value"></a>返回值

如果该方法成功，将返回ERROR_SUCCESS。 如果方法无法读取值，它将返回在 WINERROR 中定义的非零错误代码。H。 如果引用的数据不是REG_SZ类型，则返回ERROR_INVALID_DATA。 如果方法返回*ERROR_MORE_DATA，pnChars*等于零，而不是所需的缓冲区大小（以字节为单位）。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`并确认返回正确的数据类型。 有关详细信息[，请参阅 RegQueryValueEx。](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。 此外，此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不会显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey：：查询值

调用此方法以检索[m_hKey](#m_hkey)的指定值字段的数据。 此方法的早期版本不再受支持，并标记为ATL_DEPRECATED。

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要查询的值名称的 null 端接字符串的指针。 如果*pszValueName*为 NULL 或空字符串""，则该方法将检索密钥未命名或默认值的类型和数据（如果有）。

*pdwType*<br/>
指向接收代码的变量的指针，该代码指示存储在指定值中的数据类型。 如果不需要类型代码，*则 pdwType*参数可以是 NULL。

*pData*<br/>
指向接收值数据的缓冲区的指针。 如果不需要数据，此参数可以是 NULL。

*pn字节*<br/>
指向指定*pData*参数指向的缓冲区的大小（以字节为单位）的变量的指针。 当方法返回时，此变量包含复制到*pData*的数据的大小。

*dwValue*<br/>
值字段的数字数据。

*lpszValue名称*<br/>
指定要查询的值字段。

*szValue*<br/>
值字段的字符串数据。

*pdwCount*<br/>
字符串数据的大小。 其值最初设置为*szValue*缓冲区的大小。

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS;否则，在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

不再支持 的两`QueryValue`个原始版本，并标记为ATL_DEPRECATED。 如果使用这些窗体，编译器将发出警告。

其余方法称为 RegQueryValueEx。

> [!IMPORTANT]
> 此方法允许调用方指定任何注册表位置，可能读取无法信任的数据。 此外，此方法使用的 RegQueryValueEx 函数不会显式处理 NULL 终止的字符串。 这两个条件都应由调用代码检查。

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey：：重新诅咒删除密钥

调用此方法从注册表中删除指定的密钥，并显式删除任何子键。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>参数

*lpszKey*<br/>
指定要删除的键的名称。 此名称必须是[m_hKey](#m_hkey)的子键。

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS;否则，在 WINERROR 中定义的非零错误值。H。

### <a name="remarks"></a>备注

如果密钥具有子键，则必须调用此方法以删除该密钥。

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey：：设置Binary值

调用此方法以设置注册表项的二进制值。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果存在具有此名称的值，则方法将其添加到键中。

*pValue*<br/>
指向包含要使用指定值名称存储的数据的缓冲区的指针。

*n 字节*<br/>
指定*pValue*参数指向的信息的大小（以字节为单位）。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将值写入注册表。

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CregKey：：设置DWORD值

调用此方法以设置注册表项的 DWORD 值。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果存在具有此名称的值，则方法将其添加到键中。

*dwValue*<br/>
要使用指定值名称存储的 DWORD 数据。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将值写入注册表。

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>CRegKey：：SetGUID值

调用此方法以设置注册表项的 GUID 值。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果存在具有此名称的值，则方法将其添加到键中。

*吉德价值*<br/>
引用要使用指定值名称存储的 GUID。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

此方法使用`CRegKey::SetStringValue` [StringFromGUID](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2)将 GUID 转换为字符串。

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CRegKey：：设置键值

调用此方法将数据存储在指定密钥的指定值字段中。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>参数

*lpszKey名称*<br/>
指定要创建或打开的键的名称。 此名称必须是[m_hKey](#m_hkey)的子键。

*lpszValue*<br/>
指定要存储的数据。 此参数必须为非 NULL。

*lpszValue名称*<br/>
指定要设置的值字段。 如果键中不存在具有此名称的值字段，则添加该字段。

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS;否则，在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

调用此方法以创建或打开*lpszKeyName*密钥，并将*lpszValue*数据存储在*lpszValueName*值字段中。

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey：：设置密钥安全性

调用此方法以设置注册表项的安全性。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>参数

*四*<br/>
指定要设置的安全描述符的组件。 该值可以是以下值的组合：

|“值”|含义|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|设置密钥的任意访问控制列表 （DACL）。 密钥必须具有WRITE_DAC访问权限，或者调用进程必须是对象的所有者。|
|GROUP_SECURITY_INFORMATION|设置密钥的主组安全标识符 （SID）。 密钥必须具有WRITE_OWNER访问权限，或者调用进程必须是对象的所有者。|
|OWNER_SECURITY_INFORMATION|设置密钥的所有者 SID。 密钥必须具有WRITE_OWNER访问权限，或者调用进程必须是对象的所有者或启用了SE_TAKE_OWNERSHIP_NAME权限。|
|SACL_SECURITY_INFORMATION|设置密钥的系统访问控制列表 （SACL）。 密钥必须具有ACCESS_SYSTEM_SECURITY访问权限。 获取此访问权限的正确方法是在调用方的当前访问令牌中启用SE_SECURITY_NAME[权限](/windows/win32/secauthz/privileges)，打开句柄以ACCESS_SYSTEM_SECURITY访问，然后禁用该权限。|

*Psd*<br/>
指向[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)结构的指针，该结构指定要为指定密钥设置的安全属性。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

设置密钥的安全属性。 有关详细信息[，请参阅 RegSetKey 安全](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity)。

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CRegKey：：设置多字符串值

调用此方法以设置注册表项的多字符串值。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果存在具有此名称的值，则方法将其添加到键中。

*pszValue*<br/>
指向要使用指定值名称存储的多字符串数据的指针。 多字符串是 null 终止字符串的数组，由两个空字符终止。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将值写入注册表。

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey：：设置QWORD值

调用此方法以设置注册表项的 QWORD 值。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果存在具有此名称的值，则方法将其添加到键中。

*qwValue*<br/>
要使用指定值名称存储的 QWORD 数据。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将值写入注册表。

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey：：设置字符串值

调用此方法以设置注册表项的字符串值。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果存在具有此名称的值，则方法将其添加到键中。

*pszValue*<br/>
指向要使用指定值名称存储的字符串数据的指针。

*dwType*<br/>
要写入注册表的字符串的类型：REG_SZ（默认值）或REG_EXPAND_SZ（用于多字符串）。

### <a name="return-value"></a>返回值

如果该方法成功，则返回值ERROR_SUCCESS。 如果方法失败，返回值是在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将值写入注册表。

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey：：设置价值

调用此方法将数据存储在指定的值字段中[m_hKey](#m_hkey)。 此方法的早期版本不再受支持，并标记为ATL_DEPRECATED。

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>参数

*pszValue名称*<br/>
指向包含要设置的值名称的字符串的指针。 如果具有此名称的值在键中不存在，则方法将其添加到键中。 如果*pszValueName*为 NULL 或空字符串""，则该方法将设置键的未命名或默认值的类型和数据。

*dwType*<br/>
指定指示*pValue*参数指向的数据类型的代码。

*pValue*<br/>
指向包含要使用指定值名称存储的数据的缓冲区的指针。

*n 字节*<br/>
指定*pValue*参数指向的信息的大小（以字节为单位）。 如果数据的类型为REG_SZ、REG_EXPAND_SZ或REG_MULTI_SZ，*则 nBytes*必须包括终止空字符的大小。

*hKey父*<br/>
打开键的句柄。

*lpszKey名称*<br/>
指定要创建或打开的键的名称。 此名称必须是*hKeyParent*的子键。

*lpszValue*<br/>
指定要存储的数据。 此参数必须为非 NULL。

*lpszValue名称*<br/>
指定要设置的值字段。 如果键中不存在具有此名称的值字段，则添加该字段。

*dwValue*<br/>
指定要存储的数据。

*b多*<br/>
如果为 false，则指示字符串的类型为REG_SZ。 如果为 true，则指示该字符串是类型REG_MULTI_SZ的多字符串。

*nValueLen*<br/>
如果*bMulti*为 true，*则 nValueLen*是字符中的*lpszValue*字符串的长度。 如果*bMulti*为 false，则值 -1 表示该方法将自动计算长度。

### <a name="return-value"></a>返回值

如果成功，则返回ERROR_SUCCESS;否则，在 WINERROR 中定义的非零错误代码。H。

### <a name="remarks"></a>备注

的两个`SetValue`原始版本标记为ATL_DEPRECATED，不应再使用。 如果使用这些窗体，编译器将发出警告。

第三种方法称为[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)。

## <a name="see-also"></a>请参阅

[DCOM 样品](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)
