# MUST_Calendar 

[English](README_EN.md) | [简体中文](README.md)

将 澳门科技大学wemust课表通过ics导入系统日历（iOS、Android、HarmonyOS、Mac OS、Windows）

## 本地部署

1. Clone仓库
2. 在目录下新建``config.py``
    ```python
    termCode='2502,2506' # 学期代号，用逗号分隔
    username='你的学号'
    password='你的密码'
    ```
3. 安装chrome driver（如果没有）[https://googlechromelabs.github.io/chrome-for-testing/#stable](https://googlechromelabs.github.io/chrome-for-testing/#stable)
3. 安装依赖并运行
    ```
    pip install -r requirements.txt
    python ./main.py
    ```

## GitHub Action部署

1. Fork仓库
2. `Actions`-同意Workflow
3. `Settings` - `Security` - `Secrets and variables` - `Actions` - `New repository secret`
4. 在 name 中填写 `USERNAME`，`Secret`为学号
5. 同理，再添加一个secret，名为`PASSWORD`，`Value` 为 Wemust 密码
6. 修改[.github/workflows/python-app.yml](.github/workflows/python-app.yml)，在`13`行处设置学期代号；取消`27`行的注释，启动定时运行。

### 使用方法（以IOS为例）

1. 打开日历
2. 日历-添加日历-添加订阅日历
3. 输入 <https://raw.githubusercontent.com/你的GitHub账号/MUST_Calendar/refs/heads/main/output/[学号]_[学期代码].ics>

日历会在每天凌晨更新，可在```.github/workflows/python-app.yml```中修改。

## TODO

- [x] 多学期(2025.5.9)
- [x] 多语言支持(2025.5.23)
- [ ] 考试日历


欢迎PR和Issues！
