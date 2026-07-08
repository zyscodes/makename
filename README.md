# 宝宝起名小帮手

一个纯静态的儿童起名 HTML 页面，支持按姓氏、名字长度、性别偏好和五行属性随机生成候选名字。页面不依赖后端和构建工具，可以直接部署到 GitHub Pages。

## 功能

- 支持输入单姓或复姓。
- 支持生成两个字姓名或三个字姓名。
- 支持男孩、女孩、不限三种性别偏好。
- 支持金、木、水、火、土五行多选。
- 内置较大的五行汉字池，当前总计约 1190 个字。
- 支持从五行字池中手动挑选喜欢的字，组成“我的字池”。
- 只要“我的字池”中有字，生成结果会优先只从手选字中随机。
- 支持复制名字、收藏名字。
- 收藏数据保存在浏览器本地存储中。
- 移动端自适应，适合手机浏览器使用。

## 使用方式

直接用浏览器打开 `index.html` 即可使用。

常见流程：

1. 输入姓氏，例如 `王` 或 `欧阳`。
2. 选择名字长度、性别偏好、五行属性。
3. 点击“生成名字”。
4. 如果想缩小随机范围，可以在五行字池中点击喜欢的字，组成“我的字池”后再生成。
5. 对满意的名字可以复制或收藏。

## 部署到 GitHub Pages

1. 把 `index.html` 和 `README.md` 上传到 GitHub 仓库根目录。
2. 进入仓库 `Settings`。
3. 找到 `Pages`。
4. Source 选择 `Deploy from a branch`。
5. Branch 选择 `main` 和 `/root`。
6. 保存后等待 GitHub Pages 发布。

发布完成后，访问 GitHub Pages 提供的网址即可使用。

## 字池维护

五行字池在 `index.html` 中的 `rawElementPools` 里维护：

- `metal`：金属性字池
- `wood`：木属性字池
- `water`：水属性字池
- `fire`：火属性字池
- `earth`：土属性字池

可以直接往对应字符串里追加汉字。页面启动时会自动去重，并自动更新每个字池显示的数量。

男孩/女孩偏好加权字池在 `genderPools` 中维护。这里的字不会限制生成范围，只会让对应性别下更常出现这些气质更匹配的字。

## 本地检查

如果电脑有 Node.js，可以用下面命令检查页面脚本语法：

```bash
node -e 'const fs=require("fs"); const html=fs.readFileSync("index.html","utf8"); const script=html.match(/<script>([\s\S]*)<\/script>/)[1]; new Function(script); console.log("JS parsed OK");'
```

也可以临时启动本地静态服务预览：

```bash
python3 -m http.server 8000
```

然后访问：

```text
http://127.0.0.1:8000/index.html
```

## 文件结构

```text
.
├── README.md
└── index.html
```
