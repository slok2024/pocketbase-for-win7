pocketbase for win7

运行pocketbase64.exe serve

第一步：创建管理员账号
在浏览器打开 http://127.0.0.1:8090/_/。

第一次进入会要求你设置 Email 和 Password。

设置完成后登录，你会进入管理面板。

第二步：设计你的数据库 (Collections)
PocketBase 核心就是“集合（Collections）”，你可以把它理解为 Excel 表格或数据库表。

点击左侧菜单的 "Collections"。

点击 "New collection"，给它起个名（比如 posts 或 tasks）。

添加字段（Fields）：比如 title (text), content (editor), status (bool)。

保存。现在你可以点击 "New record" 手动往里填点数据了。

第三步：设置权限 (API Rules)
这是最重要的一步！默认情况下，为了安全，所有人（包括游客）都无法读取数据。

在 Collection 设置页面，点击 "API Rules" 选项卡。

你会看到 List/Search、View、Create 等权限。

点击旁边的“锁”图标：

如果你想让所有人都能看：直接留空或填入 ""（代表公开）。

如果你想让登录用户才能看：填入 @request.auth.id != ""。

点击 "Save changes"。

第四步：在你的前端调用数据
PocketBase 提供了非常简单的 SDK。假设你在写网页：

安装 SDK:

Bash
npm install pocketbase
调用数据代码示例:

JavaScript
import PocketBase from 'pocketbase';

const pb = new PocketBase('http://127.0.0.1:8090');

// 获取 'posts' 集合里的数据
const records = await pb.collection('posts').getFullList();
console.log(records);
第五步：处理文件上传
PocketBase 自带文件管理。

在 Collection 里添加一个类型为 File 的字段。

上传图片或文档。

你可以直接通过 API 获取文件的 URL，甚至可以自动生成缩略图。
