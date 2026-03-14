# MANIMFORHOUDE 使用教程
## 一、前置说明
- 目标：完成MANIMFORHOUDE的完整运行环境搭建，能执行动画代码并渲染出视频。
- 核心依赖：Python 3.8~3.10（Manim兼容最佳版本）、Git、FFmpeg、MANIMFORHOUDE源码。

## 二、分系统安装Python（3.8~3.10）
### 🔹 Windows系统（Win10/Win11）
#### 步骤1：下载Python安装包
1. 打开Python官网：https://www.python.org/downloads/release/python-3109/（推荐3.10.9，稳定版）；
2. 下滑找到「Files」板块，选择「Windows Installer (64-bit)」（64位系统，绝大多数电脑是64位）；
   - 若不确定系统位数：右键「此电脑」→「属性」→ 查看「系统类型」。

#### 步骤2：安装Python（关键：勾选环境变量）
1. 双击下载的安装包（如`python-3.10.9-amd64.exe`）；
2. 勾选「Add Python 3.10 to PATH」（**必选！否则后续无法在终端调用python**）；
3. 选择「Customize installation」（自定义安装）→ 直接点「Next」；
4. 勾选「Install for all users」，并选择安装路径（建议：`D:\Python310`，避免中文路径）；
5. 点击「Install」，等待安装完成 → 点击「Close」。

#### 步骤3：验证安装
1. 按下`Win+R`，输入`cmd`打开命令提示符；
2. 输入以下命令，若显示版本号（如`Python 3.10.9`）则成功：
   ```bash
   python --version
   # 若提示“python不是内部命令”：说明没勾选PATH，需重新安装并勾选，或手动配置环境变量
   ```
   - 补充：若终端显示`Python 2.x`，改用`python3 --version`，后续命令均替换为`python3`/`pip3`。

### 🔹 macOS系统（macOS 10.15+）
#### 方式1：官网安装（推荐）
1. 打开Python官网：https://www.python.org/downloads/release/python-3109/；
2. 下滑选择「macOS 64-bit universal2 installer」下载；
3. 双击安装包，按引导完成安装（默认路径即可）；
4. 验证：打开「终端」（Launchpad→其他→终端），输入：
   ```bash
   python3 --version  # macOS默认自带Python2，需用python3
   ```

#### 方式2：Homebrew安装（更便捷）
1. 若未安装Homebrew，终端输入：
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
2. 安装Python 3.10：
   ```bash
   brew install python@3.10
   ```
3. 验证：`python3 --version`。

### 🔹 Linux系统（以Ubuntu 20.04/22.04为例）
Ubuntu默认自带Python3，但版本可能过高，需指定3.10：
1. 终端输入以下命令，添加Python源：
   ```bash
   sudo apt update
   sudo apt install software-properties-common
   sudo add-apt-repository ppa:deadsnakes/ppa
   ```
2. 安装Python 3.10：
   ```bash
   sudo apt install python3.10 python3.10-venv python3.10-pip
   ```
3. 验证：
   ```bash
   python3.10 --version
   ```
4. （可选）设置python3默认指向3.10：
   ```bash
   sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.10 1
   ```

## 三、分系统安装Git（克隆仓库用）
### 🔹 Windows系统
1. 下载Git：https://git-scm.com/download/win；
2. 双击安装包，按默认选项一路「Next」（建议安装路径：`D:\Git`）；
3. 验证：打开cmd，输入`git --version`，显示版本号则成功。

### 🔹 macOS系统
1. 方式1：Homebrew安装：`brew install git`；
2. 方式2：官网安装：https://git-scm.com/download/mac；
3. 验证：终端输入`git --version`。

### 🔹 Linux系统（Ubuntu）
```bash
sudo apt install git
git --version  # 验证
```

## 四、分系统安装FFmpeg（动画渲染核心）
### 🔹 Windows系统
1. 下载FFmpeg：https://github.com/BtbN/FFmpeg-Builds/releases（选择「ffmpeg-master-latest-win64-gpl.zip」）；
2. 解压到指定路径（如`D:\FFmpeg`），记住解压后`bin`目录的路径（如`D:\FFmpeg\bin`）；
3. 配置环境变量：
   - 右键「此电脑」→「高级系统设置」→「环境变量」；
   - 在「系统变量」中找到「Path」→「编辑」→「新建」；
   - 粘贴`D:\FFmpeg\bin`→「确定」（所有窗口都点确定）；
4. 验证：重启cmd，输入`ffmpeg -version`，显示版本号则成功。

### 🔹 macOS系统
```bash
# 需先安装Homebrew（已装则跳过）
brew install ffmpeg
# 验证
ffmpeg -version
```

### 🔹 Linux系统（Ubuntu）
```bash
sudo apt update
sudo apt install ffmpeg
# 验证
ffmpeg -version
```

## 五、克隆并配置MANIMFORHOUDE仓库
### 🔹 所有系统通用步骤（终端/CMD操作）
#### 步骤1：克隆仓库
1. 打开终端（Windows：cmd/PowerShell；macOS/Linux：终端）；
2. 选择一个存放代码的目录（如桌面）：
   ```bash
   # Windows
   cd Desktop  # 进入桌面
   # macOS/Linux
   cd ~/Desktop  # 进入桌面
   ```
3. 克隆仓库：
   ```bash
   git clone https://github.com/AAAFTEEE/MANIMFORHOUDE.git
   cd MANIMFORHOUDE  # 进入仓库目录
   ```

#### 步骤2：创建Python虚拟环境（隔离依赖，必做）
##### Windows系统
```bash
# 创建虚拟环境（基于Python 3.10）
python -m venv manim-env

# 激活虚拟环境（关键！每次运行都要激活）
manim-env\Scripts\activate
# 激活后终端前缀会显示 (manim-env)
```

##### macOS/Linux系统
```bash
# 创建虚拟环境
python3 -m venv manim-env

# 激活虚拟环境
source manim-env/bin/activate
# 激活后终端前缀显示 (manim-env)
```

#### 步骤3：安装Python依赖
##### 情况1：仓库有requirements.txt（优先）
```bash
# Windows
pip install -r requirements.txt
# macOS/Linux
pip3 install -r requirements.txt
```

##### 情况2：无requirements.txt（手动装核心依赖）
```bash
# Windows
pip install manim==0.17.3 pycairo pydub pillow matplotlib
# macOS/Linux
pip3 install manim==0.17.3 pycairo pydub pillow matplotlib
```
- 若安装pycairo失败：
  - Windows：下载对应版本的pycairo wheel包（https://www.lfd.uci.edu/~gohlke/pythonlibs/#pycairo），比如`pycairo-1.24.0-cp310-cp310-win_amd64.whl`，然后`pip install 包名.whl`；
  - macOS：`brew install cairo pkg-config`，再重新`pip3 install pycairo`；
  - Linux：`sudo apt install libcairo2-dev`，再重新`pip3 install pycairo`。

## 六、分系统编写并运行第一个动画
### 🔹 步骤1：创建动画文件
所有系统都用纯文本编辑器（推荐VS Code，也可用记事本/TextEdit）：
1. 打开VS Code，安装「Python插件」（必装，方便调试）；
2. 打开MANIMFORHOUDE文件夹，新建文件`first_animation.py`；
3. 粘贴以下代码（适配中文，极简示例）：
```python
from manim import *

# 定义动画场景
class HOUDEChineseDemo(Scene):
    def construct(self):
        # 中文文本（指定黑体，避免乱码）
        text = Text(
            "HOUDE 数学动画演示",
            font="SimHei",  # Windows：SimHei；macOS：Heiti TC；Linux：WenQuanYi Micro Hei
            font_size=48,
            color=BLUE
        )
        # 淡入文本
        self.play(FadeIn(text))
        self.wait(2)
        # 文本缩放+变色
        self.play(text.animate.scale(0.8).color(RED))
        self.wait(2)
        # 淡出文本
        self.play(FadeOut(text))
```

### 🔹 步骤2：运行动画（分系统）
确保终端已激活虚拟环境（前缀有`(manim-env)`），且当前目录在MANIMFORHOUDE下。

#### Windows系统（CMD/PowerShell）
```bash
# -p：渲染后自动播放；-ql：低质量（快速渲染，调试用）
manim -pql first_animation.py HOUDEChineseDemo
```

#### macOS/Linux系统（终端）
```bash
# 注意：macOS/Linux需用python3 -m manim 替代manim（避免路径问题）
python3 -m manim -pql first_animation.py HOUDEChineseDemo
```

### 🔹 步骤3：查看结果
1. 运行成功后，会在MANIMFORHOUDE目录下生成`media`文件夹；
2. 动画视频路径：`media/videos/first_animation/480p15/HOUDEChineseDemo.mp4`；
3. 系统会自动弹出播放器播放视频。

## 七、分系统常见问题与解决方案
| 系统       | 问题现象                  | 解决方案                                                                 |
|------------|---------------------------|--------------------------------------------------------------------------|
| Windows    | 输入manim提示“不是内部命令” | 激活虚拟环境后，用`python -m manim`替代`manim`；或检查虚拟环境是否激活    |
| Windows    | 中文乱码                  | 确认font参数是`SimHei`（黑体），且系统安装了黑体；或指定本地字体文件路径  |
| macOS      | 运行时提示“找不到ffmpeg”   | 重启终端，或重新执行`brew install ffmpeg`；验证`ffmpeg -version`是否正常 |
| macOS      | 中文显示方块              | 将font参数改为`Heiti TC`（华文黑体）或`PingFang SC`（苹方）              |
| Linux      | pycairo安装失败            | 先执行`sudo apt install libcairo2-dev pkg-config`，再重新安装pycairo      |
| 所有系统   | 渲染视频卡顿/黑屏          | 改用低质量渲染（-ql），检查Python版本是否为3.8~3.10；关闭其他占用内存的程序 |

## 八、进阶操作（可选）
1. **高质量渲染**：将`-ql`改为`-qh`（1080p），命令示例：
   ```bash
   # Windows
   manim -pqh first_animation.py HOUDEChineseDemo
   # macOS/Linux
   python3 -m manim -pqh first_animation.py HOUDEChineseDemo
   ```
2. **导出GIF**：添加`--format=gif`参数：
   ```bash
   # Windows
   manim -ql --format=gif first_animation.py HOUDEChineseDemo
   ```
3. **VS Code调试**：
   - 打开`first_animation.py`，点击右上角「运行和调试」；
   - 选择「Python文件」→「配置Python启动项」；
   - 在`launch.json`中添加参数：
     ```json
     {
         "name": "Manim Run",
         "type": "python",
         "request": "launch",
         "program": "${file}",
         "args": ["-pql", "${file}", "HOUDEChineseDemo"],
         "console": "integratedTerminal"
     }
     ```
   - 点击「运行」即可调试代码。

至此，你已完成全系统的MANIMFORHOUDE环境搭建和基础使用。

*（以上内容为豆包 AI 生成）*
