### 项目简介

此项目使用 Jekyll 的 "just-the-docs" 主题来创建一个简洁的文档网站并自动化部署。主要内容放置在 `docs` 文件夹内，网站首页通过根目录下的 `index.md` 文件进行配置。额外进行了主题的修改并添加了主题切换按钮。

### 环境设置

#### 必需的软件

- **Ruby** (包括 RubyGems, GCC, 和 Make)
- **Jekyll**
- **Bundler**

#### 安装指南

##### Windows

1. 安装 Ruby:

   - 下载并安装 Ruby+Devkit 版本从 [RubyInstaller](https://rubyinstaller.org/downloads/)。
   - 安装过程中，确保勾选 "Add Ruby to your PATH" 选项。

2. 安装 Jekyll 和 Bundler:

   ```bash
   gem install jekyll bundler
   ```

##### Linux

1. 安装 Ruby (使用 rbenv 或 rvm):

   - 安装 rbenv 和 ruby-build:

     ```bash
     sudo apt-get update
     sudo apt-get install -y git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev
     curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-installer | bash
     ```

   - 添加 rbenv 到 bash:

     ```bash
     echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
     echo 'eval "$(rbenv init -)"' >> ~/.bashrc
     exec $SHELL
     ```

   - 安装 Ruby:

     ```bash
     rbenv install 2.7.2
     rbenv global 2.7.2
     ```

   - 检查 Ruby 安装:

     ```bash
     ruby -v
     ```

2. 安装 Jekyll 和 Bundler:

   ```bash
   gem install jekyll bundler
   ```

### 配置项目

1. 获取项目代码：

- **克隆仓库**：

  ```bash
   git clone https://github.com/lzzsG/just-the-docs-template.git
   cd just-the-docs-template
  ```

- **使用模板**： 访问项目的 GitHub 页面，点击右上角的 “Use this template” 按钮。

- **直接 Fork**： 访问项目的 GitHub 页面，点击右上角的 “Fork” 按钮，然后克隆你 Fork 的仓库


2. 安装依赖：

   ```bash
   bundle install
   ```

3. 修改 `_config.yml` 文件以自定义网站设置（如标题、描述、URL 等）。

4. 编辑 `index.md` 以设置首页内容。

### 运行项目

- 运行以下命令来启动 Jekyll 服务器，并启用实时重载功能：

  ```bash
  bundle exec jekyll serve --livereload
  ```

  访问 `http://localhost:4000` 在浏览器中查看网站。

### 更多配置

- 请参考 [just-the-docs官方文档](https://just-the-docs.com/) 来了解更多高级配置和自定义选项。
