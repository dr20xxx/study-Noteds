该 **的Hello World** 项目是计算机编程历史悠久的传统。 这是一个简单的练习，可以让您开始学习新事物。 让我们开始使用 GitHub！ 

**您将学习如何：** 

- 创建和使用存储库 
- 启动和管理一个新的分支 
- 对文件进行更改并将它们作为提交推送到 GitHub 
- 打开并合并拉取请求 



## 什么是 GitHub？ 

GitHub 是一个用于版本控制和协作的代码托管平台。  它让您和其他人可以从任何地方一起处理项目。 

本教程教您 GitHub 基本知识，如 *存储库* 、 *分支* 、 *提交* 和 *拉取请求* 。 您将创建自己的 Hello World 存储库并学习 GitHub 的 Pull Request 工作流程，这是一种创建和审查代码的流行方式。 

#### 无需编码 

要完成本教程，您需要一个 [GitHub.com 帐户 ](http://github.com)和 Internet 访问权限。 您不需要知道如何编码、使用命令行或安装 Git（版本控制软件 GitHub 是基于它构建的）。 

> **提示：** 在单独的浏览器窗口（或选项卡）中打开本指南，以便您在完成教程中的步骤时可以看到它。 



## 步骤 1. 创建存储库 

一个 **库** 通常用于举办单个项目。 存储库可以包含文件夹和文件、图像、视频、电子表格和数据集——您的项目需要的任何内容。 我们建议包含一个 *README* 或一个包含有关您的项目的信息的文件。 GitHub 可以让您在创建新存储库的同时轻松添加一个。 *它还提供其他常用选项，例如许可证文件。* 

您的 `hello-world`存储库可以是您存储想法、资源甚至与他人共享和讨论事物的地方。 

### 创建新存储库 

1. 在右上角，您的头像或标识旁边，单击 

1. ，然后选择 **New repository** 。 
2. 命名您的存储库 `hello-world`. 
3. 写一个简短的描述。 
4. 选择 **Initialize this repository with a README** 。 

![新的回购形式](https://guides.github.com/activities/hello-world/create-new-repo.png)

单击 **创建存储库** 。 



## 步骤 2. 创建一个分支 

**分支** 是一种同时处理不同版本存储库的方式。 

默认情况下，您的存储库有一个名为的分支 `main`这被认为是最终分支。  在提交之前，我们使用分支进行试验和编辑 `main`. 

当你创建一个分支时 `main`分支，您正在制作副本或快照 `main`就像那个时候一样。  如果其他人更改了 `main`当你在你的分支上工作时，你可以拉入这些更新。 

该图显示： 

- 这 `main`分支 
- 一个名为的新分支 `feature`（因为我们正在这个分支上做“功能工作”） 
- 那个旅程 `feature`在合并之前需要 `main`

![分店](https://guides.github.com/activities/hello-world/branching.png)

您是否曾经保存过不同版本的文件？  就像是： 

- `story.txt`
- `story-joe-edit.txt`
- `story-joe-edit-reviewed.txt`

分支在 GitHub 存储库中实现了类似的目标。 

在 GitHub，我们的开发人员、作者和设计人员使用分支来将错误修复和功能工作与我们的工作分开 `main`（生产）科。  当更改准备好时，他们将分支合并到 `main`. 

### 创建一个新分支 

1. 转到您的新存储库 `hello-world`. 
2. 单击文件列表顶部显示 的下拉菜单 **branch: main** 。 
3. 输入分支名称， `readme-edits`, 进入新的分支文本框。 
4. 选择蓝色的 **创建分支** 框或按键盘上的“Enter”。 

![分支 gif](https://guides.github.com/activities/hello-world/readme-edits.gif)

现在你有两个分支， `main`和 `readme-edits`.  它们看起来完全一样，但不会持续太久！  接下来，我们将更改添加到新分支。 



## 步骤 3. 进行并提交更改 

太棒了！  现在，您在代码视图中 `readme-edits`分支，这是一个副本 `main`.  让我们做一些编辑。 

在 GitHub 上，保存的更改称为 *commits* 。 每个提交都有一个关联的 *提交消息* ，它是解释为什么进行特定更改的描述。 提交消息会记录您更改的历史记录，因此其他贡献者可以了解您所做的事情以及原因。 

#### 进行并提交更改 

1. 点击 `README.md`文件。 
2. 单击 的 

1. 文件视图右上角 铅笔图标进行编辑。 
2. 在编辑器中，写一些关于你自己的信息。 
3. 编写描述更改的提交消息。 
4. 单击 **提交更改** 按钮。 

![犯罪](https://guides.github.com/activities/hello-world/commit.png)

这些更改将仅对您的 README 文件进行 `readme-edits`分支，所以现在这个分支包含的内容不同于 `main`. 



## 步骤 4. 打开拉取请求 

不错的编辑！  现在你在一个分支中有变化 `main`，您可以打开 *拉取请求* 。 

拉取请求是 GitHub 上协作的核心。 当您打开一个 *pull request 时* ，您是在提出您的更改并请求某人审查并提取您的贡献并将它们合并到他们的分支中。 拉取请求显示 *差异* 来自两个分支的内容的 或差异。 变化、增加和减少以绿色和红色显示。 

提交后，即使在代码完成之前，您也可以打开拉取请求并开始讨论。 

通过 使用 GitHub 的 [@mention 系统 ](https://help.github.com/articles/about-writing-and-formatting-on-github/#text-formatting-toolbar)在您的拉取请求消息中 ，您可以向特定人员或团队寻求反馈，无论他们是在大厅里还是在 10 个时区之外。 

您甚至可以在自己的存储库中打开拉取请求并自行合并。  这是在处理大型项目之前学习 GitHub 流程的好方法。 

#### 打开拉取请求以更改自述文件 

*点击图像查看大图* 

| 步    | 截屏 |
| ----- | ---- |
| 单击“ |      |

| **拉取请求”** 选项卡，然后从“拉取请求”页面单击绿色的“ **新建拉取请求”** 按钮。 | [![pr-tab](https://guides.github.com/activities/hello-world/pr-tab.gif)](https://guides.github.com/activities/hello-world/pr-tab.gif) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 在 **示例比较** 框中，选择您创建的分支， `readme-edits`, 比较 `main`（原本的）。 | [![分支](https://guides.github.com/activities/hello-world/pick-branch.png)](https://guides.github.com/activities/hello-world/pick-branch.png) |
| 在“比较”页面上查看差异中的更改，确保它们是您要提交的内容。   | [![差异](https://guides.github.com/activities/hello-world/diff.png)](https://guides.github.com/activities/hello-world/diff.png) |
| 当您对这些是您想要提交的更改感到满意时，单击绿色的大的 **Create Pull Request** 按钮。 | [![创造-拉动](https://guides.github.com/activities/hello-world/create-pr.png)](https://guides.github.com/activities/hello-world/create-pr.png) |
| 为您的拉取请求命名并简要描述您的更改。                       | [![形式](https://guides.github.com/activities/hello-world/pr-form.png)](https://guides.github.com/activities/hello-world/pr-form.png) |

完成消息后，单击 **Create pull request** ！ 

------

> **提示** ：您可以使用 [的表情符号 ](https://help.github.com/articles/basic-writing-and-formatting-syntax/#using-emoji)和 [拖放图片和GIF ](https://help.github.com/articles/file-attachments-on-issues-and-pull-requests/)到的意见和引入请求。 



## 步骤 5. 合并你的拉取请求 

在这最后一步中，是时候将您的更改整合在一起了——合并您的 `readme-edits`分支到 `main`分支。 

1. 单击绿色的 **合并拉取请求** 按钮将更改合并到 `main`. 
2. 单击 **确认合并** 。 
3. 继续删除分支，因为它的更改已合并，使用 的 **删除分支** 紫色框中 按钮。 

![走](https://guides.github.com/activities/hello-world/merge-button.png) ![删除](https://guides.github.com/activities/hello-world/delete-button.png)

### 庆祝！ 

通过完成本教程，您已经学会了在 GitHub 上创建项目并发出拉取请求！ 

以下是您在本教程中完成的工作： 

- 创建了一个开源存储库 
- 开始并管理一个新的分支 
- 更改了一个文件并将这些更改提交到 GitHub 
- 打开并合并一个拉取请求 

看看你的 GitHub 个人资料，你会看到你的新 [贡献方块 ](https://help.github.com/articles/viewing-contributions)！ 

要了解有关 Pull Requests 功能的更多信息，我们建议阅读 [GitHub 流程指南 ](http://guides.github.com/overviews/flow/)。 您还可以访问 [GitHub Explore ](http://github.com/explore)并参与一个开源项目。 

------

> **提示** ：查看我们的其他 [指南 ](http://guides.github.com)、 [YouTube 频道 ](http://youtube.com/githubguides)和 [按需培训 ](https://services.github.com/on-demand/)，了解有关如何开始使用 GitHub 的更多信息。 