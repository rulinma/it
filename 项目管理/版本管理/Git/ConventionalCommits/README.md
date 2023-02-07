# ConventionalCommits

## [约定式提交](https://www.conventionalcommits.org)

    一种用于给提交信息增加人机可读含义的规范

## 使用说明

### 提交规范

* npm install -g commitizen
* npm install -g cz-conventional-changelog
* echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc
* git cz

VSCode有个提交插件，方便使用：Conventional Commits for VSCode。

### 生成changelog

* npm install -g conventional-changelog-cli
* cd my-project
* conventional-changelog -p angular -i CHANGELOG.md -s

# 参考文献

1. [Commitizen for contributors](https://github.com/commitizen/cz-cli)
2. [conventional-changelog-cli](https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli)
