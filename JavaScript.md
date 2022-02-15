# JavaScript 命名

JavaScript 作为前端以及Node.js开发人员的必备知识点，其涉及的应用领域很多，各种技术解决方案框架和库众多，因此可参考的项目也非常多。本部分按通用规则和结合前后端框架来分别阐述，阅读完后相信能够解决大部分命名烦恼，让你轻松写出符合规范、易于维护、简短的和可预见的代码。

- <a href="#通用规则">通用规则</a>
  - <a href="#布尔值命名">布尔值命名</a>
    - <a href="#规则1-避免独立变量的否定名称">规则1: 避免独立变量的否定名称</a>
    - <a href="#规则2-始终选择默认启用false设置的名称">规则2: 始终选择默认启用 false 设置的名称</a>
    - <a href="#规则3-尽量使用常规的前缀">规则3: 尽量使用常规的前缀</a>
    - <a href="#规则4-可在命名中添加描述信息">规则4: 可在命名中添加描述信息</a>
  - <a href="#数字命名">数字命名</a>
    - <a href="#规则1-分页选择最佳组合命名">规则1: 分页选择最佳组合命名</a>
    - <a href="#规则2-使用表数量的前后缀数量来命名数量">规则2: 使用表数量的前后缀数量来命名数量</a>


## 通用规则

这部分内容主要阐述 JavaScript 基础类型、函数和方法等的命名规则。

### 布尔值命名

布尔值是两种逻辑状态的变量，它包含两个值：**真**和**假**。在JavaScript中对应 `true` 和 `false`，在实践中通常使用数字 `1` 表示真值，`0` 来表示假值。

#### 规则1: 避免独立变量的否定名称

在命名中要避免使用带有否定的词汇，例如：`not`, `no`, `never`, `wont't`, `doesn't` 等，常见负值词汇如下：

```
no, not, none, no one, nobody, nothing, neither, nowhere, never
hardly, scarcely, barely
does't, isn't, wasn't, shouldn't, wouldn't, won't, can't, don't
```

示例：

```javascript
// Bad
const hasNoValues = myArray.length === 0;
if (hasNoValues) {...}

// Best：移除否定
const hasValues = myArray.length > 0;
if (hasValues) {...}

// Ok: 选择肯定词汇
const isEmpty = myArray.length === 0;
if (isEmpty) {...}
```

#### 规则2: 始终选择默认启用false设置的名称

在实际过程中，封装类，组件和提炼函数的过程中，通常有很多可选项，这个时候强烈推荐使用默认为假值的变量来命名。

常见默认为否定词汇如下：

```
selectable: 可选择
editable: 可编辑
contenteditable: 内容可编辑
writable: 可写的
readable: 可读的
clearable: 可清除
deletable: 可删除的
removable: 可移动的；可去掉的
filterable: 可筛选的
expandable: 可展开
connectable: 可连接
enumerable: 可枚举
iterable: 可迭代
sortable: 可排序
clickable: 可点击
draggable: 可拖拽
movable: 可移动
mutable: 可变的
immutable: 不可变的
visible: 可见
<!-- 约定成俗的词汇 -->
autofocus: 自动获取焦点
disabled: 已禁用
required: 必传
closable: 已关闭
readonly: 只读
nowrap: 换行
```

示例：

```javascript
// Bad, `isEnabled` 给人感觉这个是必传值
const xx = (isEnabled = false) => {...}

// Good
const xx = (disabled = false) => {...}
```

#### 规则3: 尽量使用常规的前缀

推荐命名模板为：`前缀 + 名词/动词/形容词`，推荐前缀词汇为：`is`, `has`, `show`, `can/allow`, `check`, `enable/disable`。

- `is` 前缀搭配表示动作的动词过去式表**状态已完成**，如：`isOpened`, `isClosed`, `isCanceled`, `isFailed`, `isFinished`, `isUpdated`, `isSelected`, `isChecked`, `isIdled`, `isDone`, `isCleared` 等；搭配名词表示**分类**，如：`isReserved`, `isValid`, `isInvalid`, `isList`, `isPlural`, `isArray`, `isUUID`, `isParent`, `isChild`, `isLeaf`；搭配动词现在进行时表示**进行中、持续中**，如：`isLoading`, `isRunning`, `isPending`, `isMounting` 等。
- `has` 前缀搭配名词表示**是否存在**，如：`hasParent`, `hasChild`, `hasMany`, `hasEven`, `hasOdd`, `hasClass`, `hasCss`, `hasSession`。
- `can/allow` 前缀搭配动词表示**操作是否允许**，如：`canLogin`, `canSelectItem`, `canDisplay`, `canUse`, `allowUpdate`, `allowDeletion` 等
- `show` 前缀通常用于配置组件界面功能**是否显示**，如：`showTips`, `showSearchBtn`, `showNotice`, `showTotal`, `showSizeChanger` 等。
- `check` 前缀通常用于**验证**函数名并返回布尔结果，如：`checkEmpty`, `checkHasFruit`, `checkJs`, `checkId`, `checkPrefix`等。
- `enable/disable` 前缀用于**开启/禁用**功能模块，如：`enableCsurf`, `enableLog`, `enableSwagger`, `enableGzip`, `disableCache`, `disableSourceMap`等。

#### 规则4: 可在命名中添加描述信息

在一些复杂的场景下，简单的命名并不足以描述当前变量的具体作用，添加额外的信息可以减少理解成本，特别是一些数量上的条件判断返回值。下面就一些常用的模式进行列举：

- 使用 `some`, `all`, `every`, `each`, `one`, 验证许多情况之一为真的布尔值，如：`isOneUserActive`, `isSomeUserActive`, `isAnyUserActive` 等。
- 使用 `gt`, `ge`, `lt`, `le`, `eq` 前缀在数量表示**大于**，**大于等于**，**小于**，**小于等于**，**等于**，如：`gt3Active`, `lt3Tries` 等。

## 数字命名

这里的数字命名指的是表示数量的词汇搭配具体的上下文来描述业务场景。

#### 规则1: 分页选择最佳组合命名

在数据数量较多的情况下通常会采取以分页的方式按每页多少数量来请求服务器返回指定页数或者偏移的数据。分页通常由**当前页**，**每页数量**和**总数**组成，有的实现也提供了**总页数**。下面列举了实际项目中用到的词汇：

- 当前页：`page` / `current` / `offset` / `pageNo` / `pageIndex`
- 每页数量: `size` / `pageSize` / `currentNum`
- 总数: `total` / `count` / `sum` / `totalCount`

推荐组合(当前页/每页数量/总数)方式：

1. `page` / `size` / `total` 最简洁的组合
2. `current` / `pageSize` / `total` Element UI 分页使用
3. `currentPage` / `pageSize` / `pageCount` Antd 分页使用

> 补充：在ORM框架如Prisma中分页分为**偏移分页**和**游标分页**，使用了 `skip`，`take` 和 `cursor` 来命名数量。在Sequelize中使用 `offset` 和 `limit` 来命名数量。

#### 规则2: 使用表数量的前后缀数量来命名数量

使用 `min`, `max` 和 `total` 前缀来描述数量的范围和总数。使用 `count` 来表示数量，如：`MAVEN_SCM_URL_COUNT`, `postCount`, `strokeLabelCount` 等。

```javascript
// Bad
const users = 3;

// Good
const minUsers = 1;
const maxUsers = 50;
const totalUsers = 10;
```