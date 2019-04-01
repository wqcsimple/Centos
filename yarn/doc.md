##  Yarn 代替 npm
> 相当于npm的包替代工具

### install
`sudo wget https://dl.yarnpkg.com/rpm/yarn.repo -O /etc/yum.repos.d/yarn.repo`
`sudo yum install yarn`

### 设置路径
`export PATH="$PATH:`yarn global bin`"`到你的 profile 文件（也可能是 .profile、.bashrc、.zshrc 等文件）。


Npm | Yarn
---- | ---
npm install | yarn install
npm install --save [package] |  yarn add [package]
npm install --global [package] | yarn global add [package]
npm rebuild | yarn install --force
npm uninstall --save [package] | yarn remove [package]
npm cache clean | yarn cache clean
rm -rf node_modules && npm install | yarn upgrade
